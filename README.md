[![Publish Docker Image](https://github.com/wiiu-env/libwuhbutils/actions/workflows/push_image.yml/badge.svg)](https://github.com/wiiu-env/libwuhbutils/actions/workflows/push_image.yml)

# libwuhbutils
Requires the [WUHBUtilsModule](https://github.com/wiiu-env/WUHBUtilsModule) to be running via [WUMSLoader](https://github.com/wiiu-env/WUMSLoader).  
Requires [wut](https://github.com/devkitPro/wut) for building.
Install via `make install`.

## Usage
Make sure to define 
```
WUMS_ROOT := $(DEVKITPRO)/wums
```
and add `-lwuhbutils` to `LIBS` and `$(WUMS_ROOT)` to `LIBDIRS`.

After that you can simply include `<wuhb_utils/utils.h>`, to get access to WUHBUtils function.

To init the library call `WUHBUtils_Init()` and check for the `WUHB_UTILS_RESULT_SUCCESS` return code.

## Use this lib in Dockerfiles.
A prebuilt version of this lib can found on dockerhub. To use it for your projects, add this to your Dockerfile.
```
[...]
COPY --from=ghcr.io/wiiu-env/libwuhbutils:[tag] /artifacts $DEVKITPRO
[...]
```
Replace [tag] with a tag you want to use, a list of tags can be found [here](https://github.com/orgs/wiiu-env/packages/container/libwuhbutils/versions). 
It's highly recommended to pin the version to the **latest date** instead of using `latest`.

## Format the code via docker

`docker run --rm -v ${PWD}:/src ghcr.io/wiiu-env/clang-format:13.0.0-2 -r ./source ./include -i`
