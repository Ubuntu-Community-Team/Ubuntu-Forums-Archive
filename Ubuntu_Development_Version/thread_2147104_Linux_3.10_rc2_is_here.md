---
title: "Linux 3.10 rc2 is here"
date: 2013-05-20
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-05-20
still does not like nvidia drivers
possible issue with the r8169 nic driver
it does boot and the nic driver works

---

### Post by paul_in_london on 2013-05-20
> **pqwoerituytrueiwoq said:**
> still does not like nvidia drivers
possible issue with the r8169 nic driver

Same here. :(

From /var/lib/dkms/nvidia-304-updates/304.88/build/make.log:

```
...
include/linux/compiler.h:152:40: note: in definition of macro ‘likely’
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
/var/lib/dkms/nvidia-304-updates/304.88/build/nv-i2c.c: In function ‘nv_i2c_del_adapter’:
/var/lib/dkms/nvidia-304-updates/304.88/build/nv-i2c.c:327:14: error: void value not ignored as it ought to be
     osstatus = i2c_del_adapter(pI2cAdapter);
              ^
make[3]: *** [/var/lib/dkms/nvidia-304-updates/304.88/build/nv-i2c.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia-304-updates/304.88/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
paul@lubuntu-64:~/3.10$
```

---

### Post by pqwoerituytrueiwoq on 2013-05-20
i am using the 313.30 driver

---

### Post by VinDSL on 2013-05-22
> **paul_in_london said:**
> Same here. :(
Me too!

nvidia-304

```
vindsl@Zuul:~$ apt-cache policy nvidia-304:
  Installed: 304.88-0ubuntu1

```

---

### Post by Milos_SD on 2013-05-22
Here is the patch for 319.17 driver version on 3.10-rc2+ kernel:
[https://devtalk.nvidia.com/default/topic/543728/linux/building-nvidia-driver-on-kernel-3-9-0/post/3814531/#3814531](https://devtalk.nvidia.com/default/topic/543728/linux/building-nvidia-driver-on-kernel-3-9-0/post/3814531/#3814531)

Do you guys know how to apply this? When I do:  sh NVIDIA-Linux-x86_64-319.17.run --apply-patch nvidia-3.10-rc2.diff
it asks me what file do I want to patch.

---

### Post by VinDSL on 2013-05-22
Just ran across this:  [http://www.ubuntuupdates.org/package/xorg-edgers/raring/main/base/nvidia-graphics-drivers-319](http://www.ubuntuupdates.org/package/xorg-edgers/raring/main/base/nvidia-graphics-drivers-319)  (2013-05-22 17:09:41 UTC)

> nvidia-graphics-drivers-319 (319.17-0ubuntu1+xedgers~raring1) raring; urgency=medium 
 . 
   * debian/dkms/patches/buildfix_kernel_3.10.patch: 
     - Add linux 3.10 compat patch

Still looking for a version that will support legacy cards...

---

### Post by Harry33 on 2013-05-23
> **VinDSL said:**
> Just ran across this:  [http://www.ubuntuupdates.org/package/xorg-edgers/raring/main/base/nvidia-graphics-drivers-319](http://www.ubuntuupdates.org/package/xorg-edgers/raring/main/base/nvidia-graphics-drivers-319)  (2013-05-22 17:09:41 UTC)



Still looking for a version that will support legacy cards...

In the xorg-edgers PPA there is also the saucy flavour of the same 319.17 driver, with the linux 3.10 patch.

---

### Post by VinDSL on 2013-05-23
> **Harry33 said:**
> In the xorg-edgers PPA there is also the saucy flavour of the same 319.17 driver, with the linux 3.10 patch.
Yep!  There she blows...

LINK:  [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-319/?C=M;O=D](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-319/?C=M;O=D)

Hope they come up with a 304.xx version soon.

Can't even find a patch for legacy cards right now.

---

### Post by Cheltspy on 2013-05-23
So far, looking good with 3.10 rc2 and Nvidia nvidia-319_319.23-0ubuntu1~xedgers~saucy1_amd64.

So much faster.:D

Note it will not build on 3.10 rc1 (dependency problem with system_wq)

---

### Post by fooman on 2013-05-23
> **Cheltspy said:**
> So far, looking good with 3.10 rc2 and Nvidia nvidia-319_319.23-0ubuntu1~xedgers~saucy1_amd64.

So much faster.:D

don't know about it being any faster, but working great for me with xorg-edgers 319.23

```
Current Date/Time: Thu May 23 20:47:13 EDT 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.6.3.1
Unity Release: unity 7.0.0
```

---

