# QtUsb [![GitHub version](https://badge.fury.io/gh/fpoussin%2Fqtusb.svg)](https://badge.fury.io/gh/fpoussin%2Fqtusb) [![Total alerts](https://img.shields.io/lgtm/alerts/g/fpoussin/QtUsb.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/fpoussin/QtUsb/alerts/) [![Language grade: C/C++](https://img.shields.io/lgtm/grade/cpp/g/fpoussin/QtUsb.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/fpoussin/QtUsb/context:cpp)


GCC: [![Build Status](https://jenkins.netyxia.net/buildStatus/icon?job=QtUsb%2Fmaster)](https://jenkins.netyxia.net/blue/organizations/jenkins/QtUsb/branches/)  
MSVC: [![Build status](https://ci.appveyor.com/api/projects/status/4ns2jbdoveyj8n0y?svg=true)](https://ci.appveyor.com/project/fpoussin/qtusb)  

A Cross-platform USB Module for Qt built around libusb-1.0 and libhidapi  
Can be used as a library, or included directly into the project  

## Features

- Bulk transfer
- Interrupt transfer
- Hotplug detection
- Device enumeration and filtering
- HID

## Install library 

**Ubuntu** (stable versions only)  
```
sudo add-apt-repository ppa:fpoussin/ppa
sudo apt install libqt5usb5 libqt5usb5-dev
```

**Windows**  
Check the [releases](https://github.com/fpoussin/QtUsb/releases) page or [appveyor build artifacts](https://ci.appveyor.com/project/fpoussin/qtusb) for binary archives  

## Build the library

**Unix**  
You need libusb-1.0-0-dev, libhidapi-dev and pkg-config packages installed  
```shell
mkdir build && cd build
qmake ..
make install
```

Alternatively build as static library (best for portability)  
```shell
mkdir build && cd build
qmake CONFIG+=static_lib ..
# Link with '*.a' file later in you project
```

**MSVC 2017**  
You need the Windows SDKs to compile libusb  
These are available from the Visual Studio Installer  
```
build_msvc2017.bat [x64|x86] QT_PATH
ie: build_msvc2017.bat x64 C:\Qt\5.14.1\msvc2017_64
```

## Using the library or code directly  

**Option 1: Using the library**  
You'll need to add the module to your project file:  
```
qt += usb
```
Include headers:  
```
#include <QUsbDevice>
#include <QUsbInfo>
#include <QUsbEndpoint>
```

**Option 2: Importing the code in your project**  
This will tie your app to a specific Qt version as it uses private headers  
You need to include the pri file into your qmake file:
```
include(QtUsb/src/usb/usb-lib.pri)
```
Include headers:  
```
#include "qusbdevice.h"
#include "qusbinfo.h"
#include "qusbendpoint.h"
```

## Documentation

QCH files can be found with each release, they are also included in ubuntu packages.  
You have to manually install them in Qt Creator on Windows.  
Online documentation can be found here: https://fpoussin.github.io/doxygen/qtusb/0.6.x/  

## Downloads

[Ubuntu PPA](https://launchpad.net/~fpoussin/+archive/ubuntu/ppa)
Windows binaries are [in the releases section](https://github.com/fpoussin/QtUsb/releases).  
