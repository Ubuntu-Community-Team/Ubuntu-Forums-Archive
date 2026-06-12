---
title: "Steam."
date: 2016-10-06
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2016-10-06
Steam is not available in ubuntu 16.10 software center, but when I try from the cli it is available.

henry@wyatt:~$ sudo apt install steam
[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386 libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386 libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxss1:i386
  libxxf86vm1:i386 zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 rng-tools:i386 steam-devices:i386
The following NEW packages will be installed:
  gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386
  libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386 libgcrypt20:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386 libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxss1:i386
  libxxf86vm1:i386 steam:i386 zlib1g:i386
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n

I did not install, not sure about suggested packages.  Do I need to install them?

Henry

---

### Post by bregma2 on 2016-10-06
You don't need to install the suggested packages, unless you have a Steam controller (you may want the steam-devices package in that case).

---

### Post by Hewjr100 on 2016-10-09
Sorry for the long wait to reply, but I am not getting email replies to my posts and its replies.  Thanks for your reply.

Henry

---

### Post by jbicha on 2016-10-09
> **Hewjr100 said:**
> Steam is not available in ubuntu 16.10 software center

[https://launchpad.net/bugs/1564570](https://launchpad.net/bugs/1564570)

---

