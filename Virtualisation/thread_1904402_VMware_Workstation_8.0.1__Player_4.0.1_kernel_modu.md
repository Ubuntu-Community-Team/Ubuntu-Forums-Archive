---
title: "VMware Workstation 8.0.1 / Player 4.0.1 kernel module compilation on oneiric (64bit)"
date: 2012-01-04
forum: Virtualisation
---

### Post by kindergartencop on 2012-01-04
Hi all,

just because I spent some hours getting that d*mn piece of expensive junk to compile its kernel modules yesterday, I thought I might as well share the result. Please note that my patches might be crude and even wrong and I take NO RESPONSIBILITY if weird stuff happens because you follow my instructions and use them.

I am using a 64 bit core i7 system with stock kernel 3.0.0-14-generic here and failed to find any place on the net where someone already posted a solution for this software/hardware combo. Feel free to add your 32bit experience to this thread; I did not test that but it will probably work, too.

Of course, an existing install of vmware workstation or -player is required, prior to applying these instructions.

I also assume you have basic knowledge of development tools and shell on linux and I WILL NOT elaborate further on the process if you don't. If this guide is too much for you, please save your time and don't post questions. I'd rather strongly recommend you to complain loudly to vmware and ask for refund if you already bought a license. After all there is VirtualBox for free and it is delivered one-click-installable and ready to run on all recent versions of ubuntu.

Download the attached file and do the following:

```
cd /usr/lib/vmware/modules/
cp -a source source.backup
cd source
for file in *
do
tar xvf $file
done
``` Apply the patch:

```
zcat VMWare-WS8.0.1-ubuntu11.10-oneiric.patch.gz | patch -p1
```re-pack all archives and get rid of the unpacked directories:

```
for file in *-only
do
tar cvf `basename $file -only`.tar $file
done
rm -rf *-only
``` Now you should be able to build and load the modules:

```
 vmware-modconfig --console --install-all
```Good luck!

---

