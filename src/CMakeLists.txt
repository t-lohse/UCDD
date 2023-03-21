file(GLOB cdd_source "*.c" "*.cpp" "*.h")
add_library(UCDD STATIC)

target_include_directories(UCDD
    PRIVATE
        # where the library itself will look for its internal headers
        ${CMAKE_BINARY_DIR}/include
    PUBLIC
        # where top-level project will look for the library's public headers
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
        # where external projects will look for the library's public headers
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

target_sources(UCDD PRIVATE ${cdd_source})
target_link_libraries(UCDD UDBM)
