---
title: "VMWare-Installation - VMmon error"
date: 2008-09-15
forum: Virtualisation
---

### Post by Manu311 on 2008-09-15
Hi,

I'm trying to install VMWare on my Debian (lenny) for using my windows partition without reboot (for some little programms which don't like wine :(). So I Downloaded VMWare Server and Player tar.gzs and tryd different tutorials google gave me.
Best Result so far:
> 
Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.3.2". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.3.2" anyway? [no] y

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.26-1-686-bigmem/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Server 2.0.0 build 110949 detected. Building for Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.26-1-686-bigmem/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.26-1-686-bigmem'
/tmp/vmware-config4/vmmon-only/Makefile:126: *** Inappropriate build environment: you wanted to use gcc version 4.3.2 while kernel attempts to use gcc version 4.1.3.
/tmp/vmware-config4/vmmon-only/Makefile:128: *** For proper build you'll have to replace  gcc-4.1 with symbolic link to /usr/bin/gcc.  Schluss.
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Fehler 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686-bigmem'
make: *** [vmmon.ko] Fehler 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.


Now I found one solutions very often: any-any-patch
I downloaded anyany-117 but the same error appeared. Only other solution I found was editing a file and change asm to linux, but in my files there still was: linux (and not asm).

So I have no Idea how to install vmware on my debian :(.
A more experienced friend told me: only one version (server or player) works with debian and the "Your kernel was built with "gcc" version "4.1.3", while you are trying to use 
"/usr/bin/gcc" version "4.3.2"." error doesn't matter, so I hope he's right ;).

some1 help me please :(.

---

### Post by walmartshopper67 on 2008-10-10
I wouldn't be so quick to write off the gcc error. He may be right, and i'm sure he's smarter than I am, but if it doesn't work you would be well served to act on the information it's giving you (albeit not that much information). 

I'm in a similar struggle, but mine is a kernel issue. And what does he mean by "only one version works with debian"? I've used serveral vmware products on debian/ubuntu machines.

---

### Post by Manu311 on 2008-10-15
My problem is, I have no idea how to compile the kernel manually, and I fear all the problems I had when I installed debian (like not supported nvidia gc) will come up again.
"only one version" means only the player or the server, not both.

---

### Post by bodhi.zazen on 2008-10-15
There is a sticky here on how to install VMWare, give it a try.

The any-any update is somewhat outdated and I would not use it if it is not needed.

---

### Post by Manu311 on 2008-10-18
And it tells nothing else then 200 other tutorials I tried before.
Under Troubleshooting there is a page with some problems. But it doesn't help me.

---

### Post by bodhi.zazen on 2008-10-18
Well the link I gave you should walk you through the installation.

You indicated earlier you are using the any-any update, so what have you done up to now?

Have you tried installing without using the any-any update ?

If you read the error message it also tells you what to do :

> For proper build you'll have to replace  gcc-4.1 with symbolic link to /usr/bin/gcc

so ...

```
sudo mv /usr/bin/gcc-4.1 /usr/bin/gcc-4.1.bak
sudo ln -s /usr/bin/gcc /usr/bin/gcc-4.1
```After the install I suggest you un do those steps ;)

---

### Post by Manu311 on 2008-10-20
Hmmm,
I tried the last idea yesterday (before I read your post ;)), and it does something it did not before ;).
But at the end (after lots of errors):

> /tmp/vmware-config1/vmmon-only/linux/driver.c:2292: warning: assignment makes pointer from integer without a cast
/tmp/vmware-config1/vmmon-only/linux/driver.c:2302: error: &#8216;HZ&#8217; undeclared (first use in this function)
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Fehler 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686-bigmem'
make: *** [vmmon.ko] Fehler 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

it crashs again.

Btw: If there is an easier way to run my win partition (dual boot) while I'm in debian, I'd be happy to hear about it ;).

---

### Post by myle on 2008-10-27
> **bodhi.zazen said:**
> ```
sudo mv /usr/bin/gcc-4.1 /usr/bin/gcc-4.1.bak
sudo ln -s /usr/bin/gcc /usr/bin/gcc-4.1
```After the install I suggest you un do those steps ;)

It works for me.

And a noobish question probably. How do I launch the vmware? I tried Alt+F2 > vmware but asks for a username and a password. It doesn't work when I fill it in with my username/password even though I am the user who did the installation.

---

### Post by bodhi.zazen on 2008-10-27
> **myle said:**
> It works for me.

And a noobish question probably. How do I launch the vmware? I tried Alt+F2 > vmware but asks for a username and a password. It doesn't work when I fill it in with my username/password even though I am the user who did the installation.

Unless you set a username and password -> just click on continue without entering one.

---

### Post by Manu311 on 2008-11-02
> **myle said:**
> It works for me.


gratulations, but it doesn't work for me :'(.

Edit:
Some1 got a good tutorial how to compile my kernel again with an newer ggc-version? I'm afraid I could destroy something (I saved my linux-partition before) and would be happier if I got some tutorial. And not only a standart tutorial "how to create a kernel", because I even got a lot of problems at the last time, because some drivers had got problems.

---

### Post by Manu311 on 2008-11-22
I've downloaded the newest version of vmware workstation (trial) now. I'm using the .bundle file.
The installer starts but it crashs at "configuring VMPlayer".
I can't kill the program with kill, top or the close button. I needed xkill ....

There is no deb or tar.gz version so I can't download an other version (only rpm - via alien .... it didn't work neither).

So any ideas?

---

