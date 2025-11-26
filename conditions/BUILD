# -*- python -*-

# Copyright 2023 mjbots Robotic Systems, LLC.  info@mjbots.com
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("@bazel_skylib//lib:selects.bzl", "selects")

package(default_visibility = ["//visibility:public"])

config_setting(
    name = "cpu_local",
    values = {
        "cpu" : "local",
    },
)

config_setting(
    name = "cpu_k8",
    values = {
        "cpu" : "k8",
    },
)

config_setting(
    name = "cpu_darwin_x86_64",
    values = {
        "cpu" : "darwin_x86_64",
    },
)

config_setting(
    name = "aarch64",
    values = {
        "cpu" : "aarch64",
    },
)

config_setting(
    name = "aarch64_constraint",
    constraint_values = [
        "@platforms//cpu:aarch64",
    ],
)

# Alias that matches either cpu=aarch64 or platform constraint for aarch64
alias(
    name = "aarch64_all",
    actual = select({
        ":aarch64" : ":aarch64",
        ":aarch64_constraint" : ":aarch64_constraint",
        "//conditions:default" : ":aarch64",
    }),
)

config_setting(
    name = "armeabihf",
    values = {
        "cpu" : "armeabihf",
    },
)

# X86_64 conditions
config_setting(
    name = "x86_64_cpu_only",
    constraint_values = [
        "@platforms//cpu:x86_64",
    ],
)

selects.config_setting_group(
    name = "x86_64_group",
    match_any = [
        ":cpu_k8",
        ":cpu_local", 
        ":cpu_darwin_x86_64",
        ":x86_64_cpu_only",
    ],
)

alias(
    name = "x86_64",
    actual = ":x86_64_group",
)

alias(
    name = "linux",
    actual = select({
        ":cpu_local" : ":cpu_local",
        ":cpu_k8" : ":cpu_k8",
        "//conditions:default" : ":cpu_local",
    }),
)

alias(
    name = "sizet_8bytes",
    actual = select({
        ":x86_64" : ":x86_64",
        ":aarch64" : ":aarch64",
        "//conditions:default" : "x86_64",
    }),
)

alias(
    name = "long_8bytes",
    actual = select({
        ":x86_64" : ":x86_64",
        ":aarch64" : ":aarch64",
        "//conditions:default" : "x86_64",
    }),
)

alias(
    name = "long_double_16bytes",
    actual = select({
        ":x86_64" : ":x86_64",
        ":aarch64" : ":aarch64",
        "//conditions:default" : "x86_64",
    }),
)

alias(
    name = "sizet_long",
    actual = select({
        ":x86_64" : ":x86_64",
        ":aarch64" : ":aarch64",
        "//conditions:default" : "x86_64",
    }),
)

alias(
    name = "has_uint128",
    actual = select({
        ":x86_64" : ":x86_64",
        ":aarch64" : ":aarch64",
        "//conditions:default" : "x86_64",
    }),
)

config_setting(
    name = "sizet_4bytes",
    values = {
        "cpu" : "armeabihf",
    },
)

config_setting(
    name = "long_4bytes",
    values = {
        "cpu" : "armeabihf",
    },
)

config_setting(
    name = "long_double_8bytes",
    values = {
        "cpu" : "armeabihf",
    },
)

config_setting(
    name = "sizet_int",
    values = {
        "cpu" : "armeabihf",
    },
)

config_setting(
    name = "arm",
    values = {
        "cpu" : "armeabihf",
    },
)

config_setting(
    name = "gcc",
    values = {
        "define": "GCC=true",
    },
)

config_setting(
    name = "clang",
    values = {
        "define": "CLANG=true",
    },
)
