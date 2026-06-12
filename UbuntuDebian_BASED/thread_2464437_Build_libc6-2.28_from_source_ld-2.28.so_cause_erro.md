---
title: "Build libc6-2.28 from source: ld-2.28.so cause errors when installing deb package"
date: 2021-07-02
forum: Ubuntu/Debian BASED
---

### Post by pilot8 on 2021-07-02
We try to build libc6-2.28 from source code. Our board runs Ubuntu 18.04 in armhf architecture. We download the source code from [https://launchpad.net/ubuntu/+source/glibc/2.28-0ubuntu1](https://launchpad.net/ubuntu/+source/glibc/2.28-0ubuntu1).
Here is what we did to create the deb package:
1. We build it by using these bash commands:
```
/usr/bin/dpkg-source -x glibc_2.28-0ubuntu1.dsc libc6-2.28
pushd libc6-2.28/
mkdir build
pushd build/
../configure \
    --host=arm-linux-gnueabihf \
    --prefix=/tmp/armhf/libc6/usr \
    --enable-obsolete-nsl
make
make install

```

2. Create a deb folder and copy files to this folder. Also put the control file and post/pre scripts in "DEBIAN" folder in the deb folder.
3. Create deb file: /usr/bin/dpkg-deb --build --root-owner-group $deb_folder/


The deb file was created. But there are errors when we install the deb in our armhf board(sudo dpkg -i libc6_2.28-0ubuntu1-my_armhf.deb):
```
Unpacking libc6:armhf (2.28-0ubuntu1) over (2.28-0ubuntu1) ...
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dpkg: warning: old libc6:armhf package post-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dpkg: error processing archive libc6_2.28-0ubuntu1-my_armhf.deb (--install):
 new libc6:armhf package post-removal script subprocess returned error exit status 127

```

After investigation, we finally narrowed it down to "ld-2.28.so". Its path in the deb file is "lib/arm-linux-gnueabihf/ld-2.28.so". The file ld-2.28.so built by us will cause the errors above. But the one from the official deb works fine. We used the file ld-2.28.so from [https://launchpad.net/ubuntu/+source/glibc/2.28-0ubuntu1/+build/15300581/+files/libc6_2.28-0ubuntu1_armhf.deb](https://launchpad.net/ubuntu/+source/glibc/2.28-0ubuntu1/+build/15300581/+files/libc6_2.28-0ubuntu1_armhf.deb) to replace the built one in our deb. There will be no errors. The deb package can be installed properly.


I used the tool readelf, nm and objdump to check the files. There seems to be no difference between the built file by me and the one from the official deb. Could you tell me what could be wrong? Is there anything I can do to investigate it?


Help please!
Thanks in advance!

---

