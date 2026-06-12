---
title: "AMD Catalyst 12.4 installation error in Ubuntu 12.04 Beta 2"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by caveman7 on 2012-04-25
Hello all. I wanted to install AMD Catalyst Driver for my Lenovo G470 laptop in Ubuntu 12.04. Various websites and forums suggests manual installation (i.e. downloading driver from the official website and compile it). During installation, there is an error and this is the log:

> KMS make.log for fglrx-8.961 for kernel 3.2.0-23-generic-pae (i686)
Thu Apr 26 09:57:22 WIT 2012
AMD kernel module generator version 2.1
make.sh: 390: [: 1: unexpected operator
make.sh: 396: [: 1: unexpected operator
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-23-generic-pae/build SUBDIRS=/var/lib/dkms/fglrx/8.9$
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
  CC [M]  /var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c: In function ‘KCL_fpu_beg$
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c:5812:28: error: ‘TS_USEDF$
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c:5812:28: note: each undec$
make[2]: *** [/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.961/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [kmod_build] Error 2
build failed with return value 2


I've seen this type of error before when attempting to install Catalyst 12.3 but many sources told me that this issue is fixed in Catalyst 12.4 (which apparently not). Any help will be appreciated.

---

### Post by pqwoerituytrueiwoq on 2012-04-25
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
that was able to do 12.3 for me try that way (though i am happy with the open source drivers on my apu)

---

### Post by caveman7 on 2012-04-25
> **pqwoerituytrueiwoq said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
that was able to do 12.3 for me try that way (though i am happy with the open source drivers on my apu)

actually that was the website I referred to when attempting to install AMD Catalyst drivers :).

---

### Post by QIII on 2012-04-26
What is in the repos is from the 8.96 stream, which is to say that the  Precise repos have had a Beta version of 12.4 since the middle of  March.  I don't remember when it was that I got fglrx in an update but  it has been within the last week or so, which means it is probably the  final release -- a pre-release as far as the rest of the Linux world is  concerned.

The 8.97 stream (maybe 12.5) leaked out a bit a couple of days ago.

For quite some time, ATI has released new Linux drivers to coincide with  releases of Ubuntu before they are available to other Linux distros.   Phoronix complains about this every time.

Edit:  Just checked. I still have 8.960, the pre-release Beta. 12.4.  8.961 is the release version.

I'm not going to rush out and install it by hand, since I'm sure an update will come soon via the repos.

---

### Post by caveman7 on 2012-04-26
> **QIII said:**
> What is in the repos is from the 8.96 stream, which is to say that the  Precise repos have had a Beta version of 12.4 since the middle of  March.  I don't remember when it was that I got fglrx in an update but  it has been within the last week or so, which means it is probably the  final release -- a pre-release as far as the rest of the Linux world is  concerned.

The 8.97 stream (maybe 12.5) leaked out a bit a couple of days ago.

For quite some time, ATI has released new Linux drivers to coincide with  releases of Ubuntu before they are available to other Linux distros.   Phoronix complains about this every time.

Edit:  Just checked. I still have 8.960, the pre-release Beta. 12.4.  8.961 is the release version.

I'm not going to rush out and install it by hand, since I'm sure an update will come soon via the repos.

Can you please tell me which repo to add?

---

### Post by QIII on 2012-04-26
You needn't add a repo.  It's in the standard set.

I don't know what state your machine is in with your failed installation, but it will need to be cleaned up.  Go back to the binary drivers how-to, which has instructions for purging.

Then, add the driver and the Catalyst Control Center

```
sudo apt-get install fglrx amdcccle
```

Immediately set up the initial configuration:

```
sudo aticonfig --initial
```

Reboot.

If something goes wrong, we can help you sort it out from there.

The only time it is worth doing a manual install is if a new driver is released and you absolutely MUST have it right away.

If you want hardware acceleration, start a new thread and IM me to let me know it is there.  I won't give instructions in IMs because the community will not see any potential solution.

Unlike NVIDIA with its proprietary VDPAU, AMD/ATI doesn't have hardware acceleration out of the box.  ATI uses the open standard VA-API with the XvBA back end.  Those have to be installed separately.  Fortunately, the four required packages are also available in the repos.

---

