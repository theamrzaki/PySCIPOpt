Instructions for installation on rossoverde
-------------------------------------------

1. Make sure you have the latest Cmake version.
    ```
    conda install cmake
    hash -r
    cmake --version
    ```
    It should be at least version 3.0.0.

2. Download the [latest SCIP suite source code](http://scip.zib.de/download.php?fname=scipoptsuite-5.0.1.tgz) in your local workspace and untar it.

    ```
    cd /local_workspace/<username>
    tar -xzf scipoptsuite-5.0.1.tgz /local_workspace/<username>/scipoptsuite-5.0.1
    ```

3. In that folder, edit /local_workspace/&lt;username>/scipoptsuite-5.0.1/CMakeLists.txt and *delete* the lines 16-18:

    ```
    if(${BISON_FOUND} AND ${FLEX_FOUND} AND ${GMP_FOUND})
      add_subdirectory(zimpl)
    endif()
    ```

    This is a hack to prevent cmake from finding ZIMPL, which is not compatible with the latest gcc.

4. Create a build folder and run cmake, make and make install with the desired install directory, e.g. /local_workspace/&lt;username>/scipoptsuite.

    ```
    cd /local_workspace/<username>/scipoptsuite-5.0.1
    mkdir build
    cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/local_workspace/<username>/scipoptsuite/
    make INSTALLDIR=/local_workspace/chetdidi/scipoptsuite/
    make install INSTALLDIR=/local_workspace/chetdidi/scipoptsuite/
    ```

That should be it! You are now ready to install pyscipopt.