# Copyright 2010-2020 The Khronos Group Inc.
# SPDX-License-Identifier: Apache-2.0

add_executable( toktx
    ${PROJECT_SOURCE_DIR}/lib/basisu/encoder/jpgd.cpp
    ${PROJECT_SOURCE_DIR}/lib/basisu/encoder/jpgd.h
    image.cc
    image.hpp
    jpgimage.cc
    lodepng.cc
    lodepng.h
    npbmimage.cc
    pngimage.cc
    stdafx.h
    targetver.h
    toktx.cc
)
create_version_header( tools/toktx toktx )

target_include_directories(
    toktx
PRIVATE
    .
    $<TARGET_PROPERTY:ktx,INCLUDE_DIRECTORIES>
    $<TARGET_PROPERTY:objUtil,INTERFACE_INCLUDE_DIRECTORIES>
    ${PROJECT_SOURCE_DIR}/lib
    ${PROJECT_SOURCE_DIR}/lib/basisu
    ${PROJECT_SOURCE_DIR}/other_include
)

target_link_libraries(
    toktx
    ktx
    objUtil
)

target_compile_definitions(
    toktx
PRIVATE
    $<TARGET_PROPERTY:ktx,INTERFACE_COMPILE_DEFINITIONS>
)

set_tool_properties(toktx)
set_code_sign(toktx)
