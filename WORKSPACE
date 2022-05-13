load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# -----------------------------------------
# archives
# -----------------------------------------

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "69de5c704a05ff37862f7e0f5534d4f479418afc21806c887db544a316f3cb6b",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.27.0/rules_go-v0.27.0.tar.gz",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.27.0/rules_go-v0.27.0.tar.gz",
    ],
)

# Commit: a0acd1779ee91022fed0e79f640c63274ab0e9ee
# Date: 2022-05-13 02:15:12 +0000 UTC
# URL: https://github.com/bazelbuild/rules_docker/commit/a0acd1779ee91022fed0e79f640c63274ab0e9ee
#
# Remove external loaders
# Size: 964139 (964 kB)
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "89f9d96bd22121bfcf364039925d76c8f7e790e81dd89233b0a94ddf6c494d99",
    strip_prefix = "rules_docker-a0acd1779ee91022fed0e79f640c63274ab0e9ee",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/a0acd1779ee91022fed0e79f640c63274ab0e9ee.tar.gz"],
)

# -----------------------------------------
# rules_go
# -----------------------------------------

load("@io_bazel_rules_go//go:deps.bzl", "go_download_sdk", "go_register_toolchains", "go_rules_dependencies")

go_download_sdk(
    name = "go_sdk",
    version = "1.16.2",
)

go_register_toolchains()

go_rules_dependencies()

# -----------------------------------------
# rules_docker
# -----------------------------------------

load("@io_bazel_rules_docker//repositories:repositories.bzl", container_repositories = "repositories")

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load("@io_bazel_rules_docker//container:pull.bzl", "container_pull")
load("@io_bazel_rules_docker//container:load.bzl", "container_load")

container_pull(
    name = "alpine_linux_armv6_fixed_id",
    architecture = "arm",
    cpu_variant = "v6",
    digest = "sha256:f29c3d10359dd0e6d0c11e4f715735b678c0ab03a7ac4565b4b6c08980f6213b",
    os = "linux",
    registry = "index.docker.io",
    repository = "library/alpine",
)

container_load(
    name = "pause_tar",
    file = "@io_bazel_rules_docker//testdata:pause.tar",
)
