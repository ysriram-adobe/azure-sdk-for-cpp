# Copyright (c) Microsoft Corporation. All rights reserved.
# SPDX-License-Identifier: MIT

if (BUILD_CURL_TRANSPORT)

cmake_minimum_required (VERSION 3.12)
set(TARGET_NAME "azure_core_with_curl")
set(TARGET_NAME_STREAM "azure_core_with_curl_stream")
set(TARGET_NAME_STORAGE_ISSUE_249 "azure_core_storage_issue_249")
set(TARGET_NAME_STORAGE_ISSUE_248 "azure_core_storage_issue_248")

project(${TARGET_NAME} LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable (
     ${TARGET_NAME}
     azure_core_with_curl_bodyBuffer 
)

add_executable (
     ${TARGET_NAME_STREAM}
     azure_core_with_curl_bodyStream
)

add_executable (
     ${TARGET_NAME_STORAGE_ISSUE_249}
     azure_core_storage_test_sample
)

add_executable (
     ${TARGET_NAME_STORAGE_ISSUE_248}
     azure_core_storage_list_containers_sample
)

target_link_libraries(${TARGET_NAME} PRIVATE azure-core)
target_link_libraries(${TARGET_NAME_STREAM} PRIVATE azure-core)
target_link_libraries(${TARGET_NAME_STORAGE_ISSUE_249} PRIVATE azure-core)
target_link_libraries(${TARGET_NAME_STORAGE_ISSUE_248} PRIVATE azure-core)

endif()
