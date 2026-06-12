---
title: "Web Application install problems"
date: 2010-03-10
forum: Server Platforms
---

### Post by sdamron on 2010-03-10
I am trying to install Greenbone Security Assistant on Ubuntu server 9.10.  I have loaded all the dependencies, but for some reason the install script can't find the libs needed.  Here is out put from the cmake script.

-- Configuring greenbone-security-assistant...
-- Looking for pkg-config... /usr/bin/pkg-config
-- Looking for libopenvas-config... /usr/local/bin/libopenvas-config
-- checking for modules 'libmicrohttpd>=0.4.2;libxml-2.0;glib-2.0;gthread-2.0'
--   package 'libxml-2.0' not found
CMake Error at /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:270 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:322 (_pkg_check_modules_internal)
  CMakeLists.txt:79 (pkg_check_modules)


-- checking for modules 'libxslt;gnutls'
--   package 'libxslt' not found
CMake Error at /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:270 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:322 (_pkg_check_modules_internal)
  CMakeLists.txt:82 (pkg_check_modules)


CMake Error at CMakeLists.txt:85 (message):
  One or more reguired libraries was not found (see message above), please
  install the missing libraries and run cmake again.


I know this isn't really an Ubuntu problem, but if someone could tell me where the heck the libraries get installed for those, or provide a list, I would REALLY appreciate it!

TIA,

Scott

---

### Post by n0dix on 2010-03-10
Try installing the following packages:
```
$ sudo apt-get install libxml++2.6-2
$ sudo apt-get install libxslt1.1 
```

---

### Post by sdamron on 2010-03-11
No go.  It did install the libxml, but libxslt is already installed and the cmake fails with the same error.

---

### Post by stoneage on 2010-03-11
If you are building from source you may also need the development packages for those dependencies.

---

### Post by sdamron on 2010-03-11
that did it, many thanks!!

---

