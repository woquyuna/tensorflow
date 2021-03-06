licenses(["notice"])  # Apache 2.0

load("//tensorflow:tensorflow.bzl", "tf_cc_binary")
load("//tensorflow:tensorflow.bzl", "tf_cc_test")
load("//tensorflow/core:platform/default/build_config.bzl", "tf_proto_library")
load("//tensorflow/core:platform/default/build_config.bzl", "tf_additional_all_protos")

cc_library(
    name = "dump_tpu_profile",
    srcs = ["dump_tpu_profile.cc"],
    hdrs = ["dump_tpu_profile.h"],
    visibility = ["//visibility:public"],
    deps = [
        ":trace_events_to_json",
        "//tensorflow/core:framework",
        "//tensorflow/core:grpc_services",
        "//tensorflow/core:lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core/profiler:protos_all_cc",
    ],
)

cc_library(
    name = "version",
    hdrs = ["version.h"],
    visibility = ["//visibility:public"],
)

tf_cc_binary(
    name = "capture_tpu_profile",
    srcs = [
        "capture_tpu_profile.cc",
    ],
    visibility = ["//visibility:public"],
    deps = [
        ":version",
        "//tensorflow/core:framework_internal",
        "//tensorflow/core:lib",
        "//tensorflow/core/profiler/rpc/client:capture_profile",
    ],
)

cc_library(
    name = "trace_events_to_json",
    srcs = ["trace_events_to_json.cc"],
    hdrs = ["trace_events_to_json.h"],
    deps = [
        "//tensorflow/core:lib",
        "//tensorflow/core/profiler:protos_all_cc",
        "@jsoncpp_git//:jsoncpp",
    ],
)

tf_cc_test(
    name = "trace_events_to_json_test",
    srcs = ["trace_events_to_json_test.cc"],
    deps = [
        ":trace_events_to_json",
        "//tensorflow/core:lib",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
        "//tensorflow/core/profiler:protos_all_cc",
        "@jsoncpp_git//:jsoncpp",
    ],
)
