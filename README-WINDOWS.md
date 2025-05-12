# Windows setup

To build this library in a Windows environment the following dependencies are required:
- [CMake](https://cmake.org)
- A C++11 capable compiler. A solution can be installing [MSVC](https://learn.microsoft.com/en-us/cpp/build/vscpp-step-0-installation?view=msvc-170) following this [guide](https://learn.microsoft.com/en-us/cpp/build/vscpp-step-0-installation?view=msvc-170)
- [vcpkg](https://github.com/microsoft/vcpkg), follow the installation guides shown [here](https://learn.microsoft.com/en-us/vcpkg/get_started/get-started?pivots=shell-bash)

Other requirements are specified in the `vcpkg.json` configuration file and are automatically installed when running cmake (see the build steps).

# Windows build

1. `mkdir build`
2. run `cmake`:
    ```sh
    cmake -DCMAKE_TOOLCHAIN_FILE=C:/path/to/vcpkg.cmake -DCMAKE_INSTALL_PREFIX=C:/path/to/install/dir -DVCPKG_TARGET_TRIPLET=x64-windows -S . build/
    ```
    where `CMAKE_TOOLCHAIN_FILE` is necessary to tell CMake to use the vcpkg toolchain file, useful for cross-compilation (it can be found in `vcpkg/scripts/buildsystems/` directory), and `VCPKG_TARGET_TRIPLET` is used to specify the x64 architecture with dynamic linking.
3. build with:
    ```sh
    cmake --build build/ --config Release
    ```

To perform the installation in a new directory, named `install`, run:
```sh
mkdir install && cmake --install build/ --config Release
```
