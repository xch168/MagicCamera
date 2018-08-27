# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

include_directories(
        ./src/main/cpp
        ./src/main/cpp/bitmap
        ./src/main/cpp/beautify
)

aux_source_directory(./src/main/cpp SRC)
aux_source_directory(./src/main/cpp/bitmap SRC_BITMAP)
aux_source_directory(./src/main/cpp/beautify SRC_BEAUTIFY)

list(APPEND SRC ${SRC_BITMAP})
list(APPEND SRC ${SRC_BEAUTIFY})

add_library( MagicBeautify
             SHARED
             ${SRC} )


find_library( log-lib
              log )

find_library( graphics
              jnigraphics )

target_link_libraries( MagicBeautify
                       ${graphics}
                       ${log-lib} )