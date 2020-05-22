# 环境准备

## mingw64

在官网上下载mingw64，https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/。注意，一定要下载[x86_64-posix-seh](https://sourceforge.net/projects/mingw-w64/files/Toolchains targetting Win64/Personal Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z)这个版本，不要下载win32的版本（如果下载win32的版本，会报一些接口不存在的错误，比如下面的这个错误`utility.hpp:697:14: error: 'recursive_mutex' in namespace 'std' does not name a type`）。

# msys2

下载地址：http://mingw-w64.org/doku.php/download/msys2

下载完成后安装。记住要将下载的mingw64包里面的所有文件拷贝到msys2安装目录下的mingw64目录下。

# 安装cmake

下载地址：https://cmake.org/

# 安装freetype的依赖包

打开msys2安装目录下的mingw64.exe，分别之下面两个命令：

```shell
pacman -S mingw-w64-x86_64-freetype
pacman -S mingw-w64-x86_64-harfbuzz
pacman -S mingw-w64-x86_64-pkg-config
```

# 编译

1、在opencv源码目录下新建build目录

2、打开cmake-gui，选择源码目录和编译目录（编译目录指向刚刚新建的build目录）

3、点击configure，配置编译器为mingw，选择编译器路径，然后会第一次configure

4、关掉with_python， with_java, with_opencl。CMAKE_BUILD_TYPE设为release。设置OPENCV_EXTRA_MODULES_PATH为opencv_contrib下面的module目录。然后再次点击configure开始第二次配置。配置完后点击generate。

5、在msys2命令行中进入刚刚新建的build目录，输入mingw32-make开始编译，编译结束后输入mingw32-make install安装

