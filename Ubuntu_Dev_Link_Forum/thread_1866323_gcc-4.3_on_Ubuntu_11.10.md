---
title: "gcc-4.3 on Ubuntu 11.10"
date: 2011-10-21
forum: Ubuntu Dev Link Forum
---

### Post by ErlendA on 2011-10-21
Hi

On ubuntu 11.04 it was straightforward to install gcc-4.3, using meerkats deb-packages ([http://packages.ubuntu.com/maverick/gcc-4.3](http://packages.ubuntu.com/maverick/gcc-4.3)). On 11.10, however, it is problematic: the following dependency breakage occurs:

```

Unpacking gcc-4.3 (from gcc-4.3_4.3.5-3ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of gcc-4.3:
 libgcc1:i386 (1:4.6.1-9ubuntu3) breaks gcc-4.3 and is installed.
 libgcc1 (1:4.6.1-9ubuntu3) breaks gcc-4.3 and is installed.
dpkg: error processing gcc-4.3 (--install):
 dependency problems - leaving unconfigured

```

For people like me, requiring gcc-4.3 to wrap code into MATLAB, for instance, this is a problem. I need gcc-4.3 to compile code which can run on the computing servers.

---

### Post by gsmanners on 2011-10-22
I think I'd put Ubuntu 10.04 in a VirtualBox and install gcc4.3 on that. I'm not sure how you fix breakage in gcc.

---

### Post by micalith on 2012-02-11
try the reply from [michal kvasnicka]("http://askubuntu.com/users/37403/michal-kvasnicka") on [http://askubuntu.com/questions/77035/how-do-i-compile-gcc-4-3-4](http://askubuntu.com/questions/77035/how-do-i-compile-gcc-4-3-4)

---

