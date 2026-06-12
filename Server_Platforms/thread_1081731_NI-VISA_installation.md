---
title: "NI-VISA installation"
date: 2009-02-26
forum: Server Platforms
---

### Post by fedesuarez on 2009-02-26
Hi, sorry if I'm off-topic but I didn't know where to post this thread...

I'm trying to install NI-VISA drivers which are basically a bunch of drivers for instrumentation under GPIB, etc.; which is very used by electronics since it is the way to control oscilloscopes, power supplies, wave-generators, etc. with programs like LabView or even programs written in C. Unfortunately, National Instruments does not have support for debian-like systems but only for RH, SUSE and Mandriva.

I'm running ubuntu-server 2.6.24-16 and I would really appreciate to have NI-VISA functioning, so I thought it could be great to make it work under Ubuntu so you could help me to install it and try to write a howto for this. So far, I'm interested in installing the libraries just to do C programming.

NI-VISA 4.4 can be downloaded from [www.ni.com](www.ni.com) which is an .iso file. Then, I followed some forums to try to install it but I got stuck.

After mounting the .iso file I did:

sudo bash ./INSTALL    and followed all the questions

some problems concerning dependencies and rpm packages were solved by installing alien, linux-source..., and linux-headers....

but I finally got this message which I don't understand:

```

The following components will be installed using cpio:
  NI-VISA Runtime 4.4.0              3113 KB  (in /usr/local/vxipnp)
  NI-VISA Runtime Kernel 4.4.0        109 KB  (in /usr/local/vxipnp)
  NI-VISA Development 4.4.0          9685 KB  (in /usr/local/vxipnp)
  NI-VISA Configuration 4.4.0         500 KB  (in /usr/local/vxipnp)
  NI-VISA Server 4.4.0                236 KB  (in /usr/local/vxipnp)
  PXI Services 1.6.0                  791 KB  (in /usr/local/natinst/nipxi)
  NI Spy 2.6.0                       2397 KB  (in /usr/local/natinst/nispy)
  CVI Runtime 8.0                    8555 KB  (in /usr/local/natinst/cvirte)
  LabVIEW Runtime 8.2.1             38472 KB  (in /usr/local/lib/LabVIEW-8.2)
  NI-ORB 1.9.0                        481 KB  (in /usr/local/natinst/.nicore)
  NI-DIM 1.9.0                        605 KB  (in /usr/local/natinst/.nicore)
  NI-RPC 4.0.0                        124 KB  (in /usr/local/natinst/.nicore)
  NI-PAL 2.3.0                        832 KB  (in /usr/local/natinst/nipal)
  NI-PAL Kernel Support 2.3.0        1118 KB  (in /usr/local/natinst/nipal)
  NI-KAL 1.8.0                        242 KB  (in /usr/local/natinst/nikal)
Total space required:               67260 KB
Space available:                477950900 KB

Continue? [Yn] Y

******************************** WARNING **************************************
* The version of gcc in the path does not match the version of gcc used to    *
* compile the currently running kernel.  This can cause unpredictable         *
* behavior in kernel drivers and should be fixed.                             *
* gcc version: 4.2.4                                                          *
* kernel compiled with: 4.2.3                                                 *
******************************** WARNING **************************************
Installing NI-KAL 1.8.0 (f0) ...

Installing NI-PAL Kernel Support 2.3.0 (f1) ...

Installing NI-PAL 2.3.0 (f1) ...
/tmp/nivisa.install/rpmpostun.28512: 156: Syntax error: Bad for loop variable

Installation aborted.


```

I don't know what else to do...

Thanks in advance.

fede.

---

### Post by dmitriyp13 on 2009-03-17
Make sure everything is up do date on the system, including the kernel sources.  After that, try forcing the earlier version of GCC through synaptic.  If that does not work, you can install the rpm packages by hand.

---

### Post by wkulecz on 2009-03-18
I think he has all the rpm files installed with alien (all that stuff in /usr/local), the problem is building the kernel modules to support nidaq and ni-visa.

Try and see what the rpmpostun.28512 file is doing on line 156.

You would probably get better advice at the National Instruments user forum.  Although they don't support Ubuntu, people who've installed it might have a clue as to what the error message is trying to tell you.

I use the NI CVI for Linux runtime and cross-compiler, but since I don't use nidaq or ni-visa, I could skip the steps of building the modules after instaling the deb files created by alien from the rpms.

--wally.

---

