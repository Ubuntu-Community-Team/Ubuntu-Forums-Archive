---
title: "Xen and make world problems"
date: 2010-11-21
forum: Virtualisation
---

### Post by shadower108 on 2010-11-21
This forum is such a great tool for people who use Ubuntu. I actually now have run into a nag setting up xen on my new setup of Ubuntu 10.10 server edition.

BTW, I'm follwing this tutorial: [https://help.ubuntu.com/community/Xen#Maverick](https://help.ubuntu.com/community/Xen#Maverick) Notes (Xen 4.0.1 pvops on Ubuntu 10.10)

I downloaded the xen source and unpacked it in my home directory. After downloading multiple packages described on the tutorial, I then ran **make world**.

The **make world** command took quite some time, but by the end, it stated this:

make[4]: Entering directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
xen-hooks.mak:56: === pciutils-dev package not found - missing /usr/include/pci
xen-hooks.mak:57: === PCI passthrough capability has been disabled
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen/xen-4.0.1'
make: *** [world] Error 2

TBH, I can't think of anything I may have missed on my end. But I may be wrong.

If anyone has any idea of what's going on and could help that would be great. Or even things to possibly look at.

Thanks!

---

### Post by tgalati4 on 2010-11-21
What happens when you:

sudo apt-get install pciutils-dev

On my jaunty system:

apt-cache search pciutils

libpci-dev - Linux PCI Utilities (development files)
pciutils - Linux PCI Utilities
libpci1 - Linux PCI Utilities (for 2.*.* kernels) (old shared library)

So the -dev (development headers) for pciutils is indeed missing.  Go find it!!  It's possible that installing libpci-dev gives you the same thing. 

sudo apt-get install libpci-dev

---

### Post by shadower108 on 2010-11-22
Thank you for the reply! I typed in **sudo apt-get install pciutils-dev** like you said, and it found **libpci-dev** and **zlib1g-dev** (just like you said)

After running that command, I again attempted to run **make world**, and still at the same spot as before. 

Any other ideas? I'm still scouring the internet for what may be creating the problem...

Thanks for your help so far! Anything helps right about now. 

> **tgalati4 said:**
> What happens when you:

sudo apt-get install pciutils-dev

On my jaunty system:

apt-cache search pciutils

libpci-dev - Linux PCI Utilities (development files)
pciutils - Linux PCI Utilities
libpci1 - Linux PCI Utilities (for 2.*.* kernels) (old shared library)

So the -dev (development headers) for pciutils is indeed missing.  Go find it!!  It's possible that installing libpci-dev gives you the same thing. 

sudo apt-get install libpci-dev

---

### Post by shadower108 on 2010-11-22
Ok so still haven't found anything online. But I now notice a slight difference after doing what tgalati4 said to do.

After running the **make world** command, I now see this at the end:

=== PCI passthrough capability has been enabled ===
make[4]: Entering directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen/xen-4.0.1'
make: *** [world] Error 2

Anyone see this before or have any ideas of what may be causing this?

---

### Post by shadower108 on 2010-11-22
Actually, just keeping this up to date about what I find.

I changed into the directory **/xen-4.0.1/tools/ioemu-qemu-xen/** and after listing the directory, I see the file **rules.mak**.

So... if this file is there... why doesn't the **make world** command find it?



> **shadower108 said:**
> Ok so still haven't found anything online. But I now notice a slight difference after doing what tgalati4 said to do.

After running the **make world** command, I now see this at the end:

=== PCI passthrough capability has been enabled ===
make[4]: Entering directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen/xen-4.0.1'
make: *** [world] Error 2

Anyone see this before or have any ideas of what may be causing this?

---

### Post by shadower108 on 2010-11-22
Still haven't found anything on the internetz... which sucks because that means I'm stuck here until I can figure it out. Just to maybe clear things up if people don't understand what's going on... I'm installing *xen* on *ubuntu 10.10 server edition* and it's having troubles with the **make world** command after it finishes. It displays the above problem, about not finding the **rules.mak** file, even though I do see it in the file, located at **/xen-4.0.1/tools/ioemu-qemu-xen/**.


Any help is appreciated.

---

### Post by tgalati4 on 2010-11-22
There must be a config file to specify the root build directory.  I have played with Xen on Hardy Server, but I haven't built it from scratch, so I can't really help that much.  What is in the rules.mak file? Perhaps there is a directory tree problem.

---

### Post by shadower108 on 2010-11-22
Well this is what I get when I look within the file, using **vi**:

  1
  2 %.o: %.c
  3     $(call quiet-command,$(CC) $(CPPFLAGS) $(CFLAGS) -c -o $@ $<,"  CC    $(TARGET_DIR)$@")
  4
  5 %.o: %.S
  6     $(call quiet-command,$(CC) $(CPPFLAGS) -c -o $@ $<,"  AS    $(TARGET_DIR)$@")
  7
  8 %.o: %.m
  9     $(call quiet-command,$(CC) $(CFLAGS) $(CPPFLAGS) -c -o $@ $<,"  OBJC  $(TARGET_DIR)$@")
 10
 11 LINK = $(call quiet-command,$(CC) $(LDFLAGS) -o $@ $^ $(LIBS),"  LINK  $(TARGET_DIR)$@")
 12
 13 %$(EXESUF): %.o
 14     $(LINK)
 15
 16 %.a:
 17     $(call quiet-command,rm -f $@ && $(AR) rcs $@ $^,"  AR    $(TARGET_DIR)$@")
 18
 19 quiet-command = $(if $(V),$1,$(if $(2),@echo $2 && $1, @$1))



> **tgalati4 said:**
> There must be a config file to specify the root build directory.  I have played with Xen on Hardy Server, but I haven't built it from scratch, so I can't really help that much.  What is in the rules.mak file? Perhaps there is a directory tree problem.

---

### Post by meatpan on 2010-11-24
Any progress yet?  I don't have a solution, but a few (probably obvious) suggestions.  Make sure you run 'make clean', or 'make distclean' in between failed builds.  This has made a difference for me when struggling with xen builds.  Also, try running make from within the ioemu-qemu-xen subdir and see if you get the same error.

meatpan

---

### Post by shadower108 on 2010-11-26
Thanks for the reply. Unfortunately no I haven't had any progress as of yet. I also created a thread at linuxquestions.org to see if anyone there knew what may be going on. No definite answers as of yet. I tried the commands in-between builds that you pointed out, such as **make clean** and **make distclean**. I did not know of these, so I will make sure to use these whenever I think appropriate.

Quick question: how did you know those commands, **make clean** and **make distclean**, existed? Is there some kind of help file within the xen source code that I skipped over that informed you of these commands? Or was it simple findings online? 

But, steps that I have tried so far: I removed the entire xen source file and re-downloaded using **wget [http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz](http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz)**. I placed it in my home directory, instead of the **xen** directory I created in my home directory, hoping that would make a difference upon the **make world** command (as pointed out to me in the other thread by scheidel21; [http://www.linuxquestions.org/questions/showthread.php?p=4167883#post4167883](http://www.linuxquestions.org/questions/showthread.php?p=4167883#post4167883))

Then, as also pointed out, I attempted the same thing in the root of the drive, /, and the same results appeared. 

Now my question is: is there an easier way? TBH, I was hoping this wouldn't be this difficult. But of course, nothing in linux is easy ;)

After reading the walk-through on the ubuntu xen documentation, they say for my distro, that it should be compiled by hand. But are there easier ways? Anyone out there able to install xen-4.0.1 on Ubuntu 10.10 Server edition?

Again, thank you meatpan. I thank you for your input. As any help right now is greatly appreciated. I'm hoping to figure this out sometime soon, as I am going to be bald soon from ripping my hair out... and I'm only 21 :D

> **meatpan said:**
> Any progress yet?  I don't have a solution, but a few (probably obvious) suggestions.  Make sure you run 'make clean', or 'make distclean' in between failed builds.  This has made a difference for me when struggling with xen builds.  Also, try running make from within the ioemu-qemu-xen subdir and see if you get the same error.
meatpan

---

### Post by tgalati4 on 2010-11-26
The rules.mak file contains an environment variable called TARGET_DIR.  What is that variable set to?  Is it correct?

To examine your environment:

env

Did you run ./configure in the build directory?  Normally you have to configure for your environment before you can make anything.

---

### Post by agent8131 on 2010-11-27
I remember jumping through these hoops with Xen 4.0.0.  I can't remember exactly what the problem or solution was.  That was on 10.04 as well.  I've just fired off a make world on Xen 4.0.1 / Ubuntu 10.10 machine and I'll let you know what I find.  And no, Linux is not supposed to be this difficult, most software should just work by running "./configure; make; sudo make install" or something similar.  Xen seems to always be tricky which is why it is not packaged properly.

---

### Post by agent8131 on 2010-11-27
It seems that "make world" worked fine for me from the fresh source.  It might be worth examining your environment.  Also, are you by any chance trying to compile as root?  It seems like that's known to cause problems.

---

### Post by sawozny on 2010-11-27
Greetings, Ubuntu gurus!
 
OK, so I've been working with Linux to varying degrees for a number of years now, but something as ambitious as building the Xen Hypervisor from source is a little out of my depth. I found this post in the forums and it sounds like we're having the same problems so I thought I'd post the data I've gathered as a reply to this post hoping between the data posted by each of us someone finds something that helps explain and correct this.
 
Here's my situation. I'm starting with Ubuntu Server 10.10 64-bit on Intel hardware with nothing but the core system and OpenSSH Server installed. I'm following the instructions in the community area at: [https://help.ubuntu.com/community/Xen#Maverick%20Notes%20(Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10](https://help.ubuntu.com/community/Xen#Maverick%20Notes%20(Xen%204.0.1%20pvops%20on%20Ubuntu%2010.10)) which clearly state that installing Xen from the ubuntu-xen-desktop package doesn't work.
 
I start, as instructed, with sudo apt-get installs of gettext, bin86, bcc, libc6-dev-i386, iasl, texinfo and git which all go smoothly. I then wget [http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz](http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz) into my home directory and tar -xvf the xen-4.0.1.tar.gz file. 
Up until this point everything is going swimmingly. No errors or warnings I can see and so we're ready for the "make world". When I run that under my user ID as instructed, the process seems to go well for quite a while, but completes with a few error conditions. There are literally thousands of lines of output during this process so I won't post it all here, but I can if it seems useful. The last few pages of output seems to indicate that some key things are not well that I've **bolded**.
 
---------------------
 
 
LD vmlinux.o
MODPOST vmlinux.o
**WARNING: modpost: Found 8 section mismatch(es).**
**To see full details build your kernel with:**
**'make CONFIG_DEBUG_SECTION_MISMATCH=y'**
GEN .version
CHK include/linux/compile.h
UPD include/linux/compile.h
CC init/version.o
LD init/built-in.o
LD .tmp_vmlinux1
KSYM .tmp_kallsyms1.S
AS .tmp_kallsyms1.o
LD .tmp_vmlinux2
KSYM .tmp_kallsyms2.S
AS .tmp_kallsyms2.o
LD .tmp_vmlinux3
KSYM .tmp_kallsyms3.S
AS .tmp_kallsyms3.o
LD vmlinux
SYSMAP System.map
SYSMAP .tmp_System.map
CC arch/x86/boot/a20.o
AS arch/x86/boot/bioscall.o
CC arch/x86/boot/cmdline.o
AS arch/x86/boot/copy.o
HOSTCC arch/x86/boot/mkcpustr
CPUSTR arch/x86/boot/cpustr.h
CC arch/x86/boot/cpu.o
CC arch/x86/boot/cpucheck.o
CC arch/x86/boot/edd.o
VOFFSET arch/x86/boot/voffset.h
LDS arch/x86/boot/compressed/vmlinux.lds
AS arch/x86/boot/compressed/head_64.o
CC arch/x86/boot/compressed/misc.o
OBJCOPY arch/x86/boot/compressed/vmlinux.bin
GZIP arch/x86/boot/compressed/vmlinux.bin.gz
HOSTCC arch/x86/boot/compressed/mkpiggy
**/home/sawozny/xen-4.0.1/linux-2.6-pvops.git/arch/x86/boot/compressed/mkpiggy.c: In function âmainâ:**
**/home/sawozny/xen-4.0.1/linux-2.6-pvops.git/arch/x86/boot/compressed/mkpiggy.c:65: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result**
**MKPIGGY arch/x86/boot/compressed/piggy.S**
AS arch/x86/boot/compressed/piggy.o
LD arch/x86/boot/compressed/vmlinux
ZOFFSET arch/x86/boot/zoffset.h
AS arch/x86/boot/header.o
CC arch/x86/boot/main.o
CC arch/x86/boot/mca.o
CC arch/x86/boot/memory.o
CC arch/x86/boot/pm.o
AS arch/x86/boot/pmjump.o
CC arch/x86/boot/printf.o
CC arch/x86/boot/regs.o
CC arch/x86/boot/string.o
CC arch/x86/boot/tty.o
CC arch/x86/boot/video.o
CC arch/x86/boot/video-mode.o
CC arch/x86/boot/version.o
CC arch/x86/boot/video-vga.o
CC arch/x86/boot/video-vesa.o
CC arch/x86/boot/video-bios.o
LD arch/x86/boot/setup.elf
OBJCOPY arch/x86/boot/setup.bin
OBJCOPY arch/x86/boot/vmlinux.bin
HOSTCC arch/x86/boot/tools/build
BUILD arch/x86/boot/bzImage
Root device is (251, 0)
Setup is 12028 bytes (padded to 12288 bytes).
System is 4423 kB
CRC 1efe0189
Kernel: arch/x86/boot/bzImage is ready (#1)
make[4]: Leaving directory `/home/sawozny/xen-4.0.1/build-linux-2.6-pvops_x86_64'
mkdir -p /home/sawozny/xen-4.0.1/dist/install/boot
select-linux-arch: x86
select-linux-image: build-linux-2.6-pvops_x86_64/arch/x86/boot/bzImage
`build-linux-2.6-pvops_x86_64/arch/x86/boot/bzImage' -> `/home/sawozny/xen-4.0.1/dist/install/boot/vmlinuz-2.6.32.26'
`build-linux-2.6-pvops_x86_64/.config' -> `/home/sawozny/xen-4.0.1/dist/install/boot/config-2.6.32.26'
`build-linux-2.6-pvops_x86_64/System.map' -> `/home/sawozny/xen-4.0.1/dist/install/boot/System.map-2.6.32.26'
make[3]: Leaving directory `/home/sawozny/xen-4.0.1'
make[2]: Leaving directory `/home/sawozny/xen-4.0.1'
make -C tools ioemu-dir-find
make[2]: Entering directory `/home/sawozny/xen-4.0.1/tools'
set -ex; \
if test -d ioemu-qemu-xen; then \
rm -f ioemu-dir; \
ln -sf ioemu-qemu-xen ioemu-dir; \
else \
if [ ! -d ioemu-remote ]; then \
rm -rf ioemu-remote ioemu-remote.tmp; \
mkdir ioemu-remote.tmp; rmdir ioemu-remote.tmp; \
git clone ioemu-qemu-xen ioemu-remote.tmp; \
if [ "xen-4.0.1" ]; then \
cd ioemu-remote.tmp; \
git branch -D dummy >/dev/null 2>&1 ||:; \
git checkout -b dummy xen-4.0.1; \
cd ..; \
fi; \
mv ioemu-remote.tmp ioemu-remote; \
fi; \
rm -f ioemu-dir; \
ln -sf ioemu-remote ioemu-dir; \
fi
+ test -d ioemu-qemu-xen
+ rm -f ioemu-dir
+ ln -sf ioemu-qemu-xen ioemu-dir
set -e; \
case ".." in /*) XEN_ROOT=.. ;; *) xen_root_lhs=`pwd`; xen_root_rhs=../; while [ "x${xen_root_rhs#../}" != "x$xen_root_rhs" ]; do xen_root_rhs="${xen_root_rhs#../}"; xen_root_rhs="${xen_root_rhs#/}"; xen_root_rhs="${xen_root_rhs#/}"; xen_root_lhs="${xen_root_lhs%/*}"; done; XEN_ROOT="$xen_root_lhs/$xen_root_rhs" ;; esac; export XEN_ROOT; \
PREFIX="/usr"; XEN_SCRIPT_DIR="/etc/xen/scripts"; export PREFIX; export XEN_SCRIPT_DIR; \
cd ioemu-dir; \
./xen-setup
**Error: zlib check failed**
**Make sure to have the zlib libs and headers installed.**
**sed: can't read config-host.h: No such file or directory**
**make[2]: *** [ioemu-dir-find] Error 2**
**make[2]: Leaving directory `/home/sawozny/xen-4.0.1/tools'**
**make[1]: *** [tools/ioemu-dir] Error 2**
**make[1]: Leaving directory `/home/sawozny/xen-4.0.1'**
**make: *** [world] Error 2**
sawozny@xen-host:~/xen-4.0.1$
---------------------
 
One thing about the make world that was unexpected was being prompted for configuration options with the choices in square brackets and the default capitalized which is all pretty standard, but after the options there was a (NEW) before the cursor waiting for my input like this:
 
---------------------
 
Paravirtualized guest support (PARAVIRT_GUEST) [Y/n/?] y
Xen guest support (XEN) [Y/n/?] y
Enable Xen debug and tuning parameters in debugfs (XEN_DEBUG_FS) [Y/n/?] y
Enable Xen privileged domain support (XEN_DOM0) [Y/n/?] y
Enable support for Xen PCI passthrough devices (XEN_PCI_PASSTHROUGH) [N/y/?] (NEW)
 
---------------------
 
Not sure what the (NEW) meant, but to keep things simple, I just hit enter to accept all the defaults (this happened several times). I may need to change some of those options to make the Hypervisor so some of the things I'm going to need it to do later, but that's a battle for another day.
So, despite these issues, I decided to continue with the instructions to see if the errors won't really get in the way. Again, a LOT of output, but here is the last page of output indicating things probably aren't going to work out.
 
---------------------
 
make[3]: Entering directory `/home/sawozny/xen-4.0.1/tools/check'
PYTHON=python LIBXENAPI_BINDINGS=n ACM_SECURITY=n ./chk build
Xen CHECK-BUILD Sat Nov 27 18:45:15 EST 2010
Checking check_crypto_lib: OK
Checking check_curl: unused, OK
Checking check_openssl_devel:
*** check_openssl_devel FAILED: missing openssl headers
Checking check_python: OK
Checking check_python_devel: OK
Checking check_uuid_devel:
*** check_uuid_devel FAILED: missing uuid headers (package uuid-dev)
Checking check_x11_devel:
*** check_x11_devel FAILED: can't find X11 headers
OK
Checking check_xgettext: OK
Checking check_xml2: unused, OK
Checking check_zlib_devel:
*** check_zlib_devel FAILED: can't find zlib headers
Checking check_zlib_lib: OK
make[3]: *** [check-build] Error 1
make[3]: Leaving directory `/home/sawozny/xen-4.0.1/tools/check'
make[2]: *** [subdir-install-check] Error 2
make[2]: Leaving directory `/home/sawozny/xen-4.0.1/tools'
make[1]: *** [subdirs-install] Error 2
make[1]: Leaving directory `/home/sawozny/xen-4.0.1/tools'
make: *** [install-tools] Error 2
sawozny@xen-host:~/xen-4.0.1$
 
---------------------
 
Finally, even if this all would have worked, I tried to modify GRUB per the instructions by adding the following to /etc/grub.d/40_custom:
menuentry "Xen 4.0 2.6.32.25 pvops" {
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
search --no-floppy --fs-uuid --set 294e6dee-238e-42c2-814f-fb47aaa45571
multiboot /boot/xen.gz
module /boot/vmlinuz-2.6.32.25 root=/dev/sda1
module /boot/initrd-2.6.32.25.img
}
 
There is a statement that follows this text to make sure that fs-uuid is the same as in other boot targets and to just copy and paste that line. Unfortunately, I can't seem to identify any other instance of fs-uuid. I ran a "grep fs-uuid *" in the /etc/grub.d directory and there isn't any other use of that keyword. Did I misunderstand the instructions? I know my build problems above need to be resolved first, but I'm pretty sure this is going to become an issue eventually. If I just drop the text as specified in 40_custom here are the results from my sudo update-grub.
 
---------------------
 
sawozny@xen-host:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-server
Found initrd image: /boot/initrd.img-2.6.35-22-server
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number
Found linux image: /boot/vmlinuz-2.6.32.26
Found linux image: /boot/vmlinuz-2.6.32.26
Found memtest86+ image: /memtest86+.bin
done
sawozny@xen-host:/etc/grub.d$
 
---------------------
 
So, obviously, I'm in also in pretty bad shape here. I've searched other xen forums and google and I can't seem to find anybody else with the same issues as me until I found this post but this process also seems to be pretty new. So, does anyone have any advice on what might be different between my setup and the author of the instructions and / or any recommendations on how to get Xen to install based upon these issues?
 
Thanks in advance for any and all help,
 
Scott

---

### Post by agent8131 on 2010-11-27
You're missing a number of required libraries.  Try this:

```
sudo apt-get install build-essential libssl-dev uuid-dev zlib1g-dev libncurses5-dev libx11-dev

```

You definitely do not want to alter your grub configuration until "make world" completes successfully.  After that you need to run "sudo make install" and then make changes to grub.

---

### Post by sawozny on 2010-11-28
> **agent8131 said:**
> You're missing a number of required libraries. Try this:
 
```
sudo apt-get install build-essential libssl-dev uuid-dev zlib1g-dev libncurses5-dev libx11-dev

```
 
You definitely do not want to alter your grub configuration until "make world" completes successfully. After that you need to run "sudo make install" and then make changes to grub.
 
 
------------------------
OK, so I installed the library packages you suggested and then removed the xen-4.0.1 directory and re-expanded the Xen 4.0.1 source tree. 
 
When I ran make world again, things seemed to go really well for a while, but at the end the output had the following issues:
 
------------------------
 
gcc -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -m64 -fno-strict-aliasing -std=gnu99 -Wall -Wstrict-prototypes -Wno-unused-value -Wdeclaration-after-statement -D__XEN_TOOLS__ -MMD -MF .buildpy.d -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -fPIC -I../../tools/libxc -I../../tools/xenstore -I../../tools/include -Ixen/lowlevel/xc -I/usr/include/python2.6 -c xen/lowlevel/xc/xc.c -o build/temp.linux-x86_64-2.6/xen/lowlevel/xc/xc.o -fno-strict-aliasing -Werror
xen/lowlevel/xc/xc.c:7: fatal error: Python.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1
make[4]: *** [buildpy] Error 1
make[4]: Leaving directory `/home/sawozny/xen-4.0.1/tools/python'
make[3]: *** [subdir-install-python] Error 2
make[3]: Leaving directory `/home/sawozny/xen-4.0.1/tools'
make[2]: *** [subdirs-install] Error 2
make[2]: Leaving directory `/home/sawozny/xen-4.0.1/tools'
make[1]: *** [install-tools] Error 2
make[1]: Leaving directory `/home/sawozny/xen-4.0.1'
make: *** [world] Error 2
[EMAIL="sawozny@xen-host:~/xen-4.0.1$"]sawozny@xen-host:~/xen-4.0.1$[/EMAIL]

------------------------
 
So, it looks a lot closer, but not quite there yet.  I'd be curious what the person who wrote the community FAQ on installing Xen.  I'd just start from that install point and install as suggested.  Based upon what I'm seeing, I need to install Python to complete the make world process.  Does anyone know what that package is called?
 
Thanks for the help,
 
Scott

---

### Post by agent8131 on 2010-11-29
```
sudo apt-get install python-dev
```

---

### Post by big-fun-man on 2010-11-29
> **shadower108 said:**
> This forum is such a great tool for people who use Ubuntu. I actually now have run into a nag setting up xen on my new setup of Ubuntu 10.10 server edition.

BTW, I'm follwing this tutorial: [https://help.ubuntu.com/community/Xen#Maverick](https://help.ubuntu.com/community/Xen#Maverick) Notes (Xen 4.0.1 pvops on Ubuntu 10.10)

I downloaded the xen source and unpacked it in my home directory. After downloading multiple packages described on the tutorial, I then ran **make world**.

The **make world** command took quite some time, but by the end, it stated this:

make[4]: Entering directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
xen-hooks.mak:56: === pciutils-dev package not found - missing /usr/include/pci
xen-hooks.mak:57: === PCI passthrough capability has been disabled
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen/xen-4.0.1'
make: *** [world] Error 2

TBH, I can't think of anything I may have missed on my end. But I may be wrong.

If anyone has any idea of what's going on and could help that would be great. Or even things to possibly look at.

Thanks!

Try to change $(SRC_PATH)/rules.mak on /home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen/rules.mak in files Makefile and Makefile.target in directory /home/shadower/xen/xen-4.0.1/tools/ioemu-qemu-xen

---

### Post by shadower108 on 2010-12-03
Thanks for the reply. What I think I might do is just make another fresh copy. I mean the only thing I did before I was attempting to compile the Xen source was I updated the install with **sudo apt-get update** and I setup **SSH** so that I could SSH from my college to home. But now that these problems have arisen, I thought, well, I might as well just install a fresh copy again. So I brought it back to my dorm. 

> **agent8131 said:**
> It seems that "make world" worked fine for me from the fresh source.  It might be worth examining your environment.  Also, are you by any chance trying to compile as root?  It seems like that's known to cause problems.

---

### Post by shadower108 on 2010-12-03
Thanks everyone for the replies. I think I'm just going to install a fresh copy and attempt it again. 

I'll update the thread with what goes on. I'm hoping to begin the install tonight.

---

### Post by sawozny on 2010-12-04
OK, so after python-dev and the other required packages were installed I ran the make world again and this time I ran into this error:
 
fatal: git checkout: branch xen/stable-2.6.32.x already exists
 
Looks like this is no longer an OS issue, but a source issue.
 
I saw a post on serverfault.com where a couple of other people had the same issue, but no replies yet.  I'm going to post in the xen users forum to see if anybody there can help and I'll keep you posted.  :)

---

### Post by big-fun-man on 2010-12-06
somebody tried to use this instruction? [http://bderzhavets.wordpress.com/2010/10/15/set-up-xen-4-0-1-libvirt-0-8-3-on-top-of-ubuntu-10-10-desktop/](http://bderzhavets.wordpress.com/2010/10/15/set-up-xen-4-0-1-libvirt-0-8-3-on-top-of-ubuntu-10-10-desktop/)

---

### Post by MTDrifter on 2010-12-06
As posted in another forum that I was following about this issue; here's a work around/fix...

edit the following file: ./buildconfigs/src.git-clone (under xen folder)

edit the following line (line 29 in my config)

**(cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); **

to look like 

**(cd $(LINUX_SRCDIR).tmp; git checkout ); **


> **sawozny said:**
> OK, so after python-dev and the other required packages were installed I ran the make world again and this time I ran into this error:
 
fatal: git checkout: branch xen/stable-2.6.32.x already exists
 
Looks like this is no longer an OS issue, but a source issue.
 
I saw a post on serverfault.com where a couple of other people had the same issue, but no replies yet.  I'm going to post in the xen users forum to see if anybody there can help and I'll keep you posted.  :)

---

### Post by shadower108 on 2010-12-09
Yet again, I'm still having problems with installing xen. Here are the exact steps I've taken:
1. I installed a fresh copy of Ubuntu 10.10 server edition on my box.
2. Right after it was installed, I ran **wget [http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz](http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz)** 
3. I unpacked it with **tar zxvf xen-4.0.1.tar.gz**
4. Again I had another error. This time was different. Unfortunately, I don't have that same error. I have been using the box for other means lately... but I still have the same error as before when I run **make world**

[B]make[4]: Entering directory `/home/shadower/xen-4.0.1/tools/ioemu-qemu-xen'
xen-hooks.mak:56: === pciutils-dev package not found - missing /usr/include/pci
xen-hooks.mak:57: === PCI passthrough capability has been disabled
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen-4.0.1'
make: *** [world] Error 2[/B]

I don't know... I'm running out of ideas at this point. Should I not use 10.10? Should I not use Xen 4.0.1?

I also tried the work around you suggested MTDrifter, that's why I quoted it. This did not help as well. 

If anyone has had success with installing Xen 4.0.1 by source on Ubuntu 10.10 x64 Server edition had steps to do so would be great!

Thanks everyone for the responses!
Shadower


> **MTDrifter said:**
> As posted in another forum that I was following about this issue; here's a work around/fix...

edit the following file: ./buildconfigs/src.git-clone (under xen folder)

edit the following line (line 29 in my config)

**(cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); **

to look like 

**(cd $(LINUX_SRCDIR).tmp; git checkout ); **

---

### Post by Metrax on 2010-12-09
Hi,

this worked for me with Ubuntu 10.10 amd64:
```
apt-get install build-essential libncurses5-dev python-twisted git-core zlib1g-dev gettext libX11-dev uuid-dev libssl-dev bin86 bcc flex bison python-dev bridge-utils pciutils-dev libpci-dev

cd /usr/src
wget http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz
tar xfz xen-4.0.1.tar.gz
cd xen-4.0.1
nano buildconfigs/src.git-clone
# Replace Line
# (cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); \
# with:
# (cd $(LINUX_SRCDIR).tmp; git checkout -b local/$(XEN_LINUX_GIT_LOCALBRANCH) --track $(XEN_LINUX_GITREV) ); \
make world
make install
```

Kernel was compiled successfully. Until now I didn't test this, because it is too late tonight here Germany and I'm going to bed.

Best regards,

Metrax

---

### Post by shadower108 on 2010-12-10
Thanks for signing up and replying to my thread Metrax :D

1. I did what you said. I actually went through and installed all of those packages individually.

2. I then replaced the line in the git-clone file.

3. I ran make world, and again same error... :(

[B]=== PCI passthrough capability has been enabled ===
make[4]: Entering directory `/home/shadower/xen-4.0.1/tools/ioemu-qemu-xen'
Makefile:4: /rules.mak: No such file or directory
make[4]: *** No rule to make target `/rules.mak'.  Stop.
make[4]: Leaving directory `/home/shadower/xen-4.0.1/tools/ioemu-qemu-xen'
make[3]: *** [subdir-clean-ioemu-dir] Error 2
make[3]: Leaving directory `/home/shadower/xen-4.0.1/tools'
make[2]: *** [subdirs-clean] Error 2
make[2]: Leaving directory `/home/shadower/xen-4.0.1/tools'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/shadower/xen-4.0.1'
make: *** [world] Error 2
[/B]

Metrax, are you able to paste the contents of your rules.mak file? It's located in the xen-4.0.1/tools/ioemu-qemu-xen$ folder. I can see my file, even though for some reason when I run make world, it seems like it doesn't see it. Maybe there's something wrong or missing in my rules.mak file? Or maybe it's a permission issue?

ALSO: I'm not running make world as sudo or root! I'm running it as myself, the little 'ol user :(

but... again... nothing so far! I'm so glad for all of the responses I have gotten. I can't believe after all of this help, nothing has come out of it yet... 

I'm really hoping this can be nailed sooner or later. I built this box specifically for ubuntu with Xen hypervisor. I've been messing around with virtualization for a while, with VMWare and Microsoft Virtual PC. But I know using Xen would be way better than these other virtualization softwarez.

Anyways.. enough of that. Any more ideas? :D Maybe I should post on the Xen forums now? haha

Thanks, 
Shadower 

> **Metrax said:**
> Hi,

this worked for me with Ubuntu 10.10 amd64:
```
apt-get install build-essential libncurses5-dev python-twisted git-core zlib1g-dev gettext libX11-dev uuid-dev libssl-dev bin86 bcc flex bison python-dev bridge-utils pciutils-dev libpci-dev

cd /usr/src
wget http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz
tar xfz xen-4.0.1.tar.gz
cd xen-4.0.1
nano buildconfigs/src.git-clone
# Replace Line
# (cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); \
# with:
# (cd $(LINUX_SRCDIR).tmp; git checkout -b local/$(XEN_LINUX_GIT_LOCALBRANCH) --track $(XEN_LINUX_GITREV) ); \
make world
make install
```

Kernel was compiled successfully. Until now I didn't test this, because it is too late tonight here Germany and I'm going to bed.

Best regards,

Metrax

---

### Post by Metrax on 2010-12-10
I also had the same problem with this file, because I also used the docs from ubuntu for installing Xen 4.0.1. After installing all this packages I tried to compile Xen again and got the same error again.

Then I removed the complete source folder and extracted this again. After changing the file and running make world again it was working fine.

Did you removed the complete source?

I have only the root access. It is a dedicated server, and for my tests I don't need any security.

(I also investigated more than 4 hours last night to find all this out and Google was my best fried ;))

---

### Post by shadower108 on 2010-12-11
So when you said "Did you removed the complete source?", what did you mean by this? Because what I've done before was remove the entire extracted xen-4.0.1 file with the command **rm -rf**. Is that what you would constitute as "removing the complete source"? I did it before on the last installation of Ubuntu, but haven't done it this time as of yet...

If that's the case, then I can always try it again.

> **Metrax said:**
> I also had the same problem with this file, because I also used the docs from ubuntu for installing Xen 4.0.1. After installing all this packages I tried to compile Xen again and got the same error again.

Then I removed the complete source folder and extracted this again. After changing the file and running make world again it was working fine.

Did you removed the complete source?

I have only the root access. It is a dedicated server, and for my tests I don't need any security.

(I also investigated more than 4 hours last night to find all this out and Google was my best fried ;))

---

### Post by Metrax on 2010-12-11
Yes, i meant to delete the xen-4.0.1 folder completely.

---

### Post by sawozny on 2010-12-11
Hello all!
 
Thanks to everyone who replied and especialy to shadower108 who didn't flame me for jumping in on his thread :P as our problems were similar, but not the same.
 
Just as an FYI, I got all the way through install with no fatal errors. Here is the exact procedure I needed to follow (based upon the community documentation and modifications suggested from various locations):
 
- Install Ubuntu 10.10 server amd64 with only the core operating system and OpenSSH server
- sudo apt-get install gettext bin86 bcc libc6-dev-i386 iasl texinfo git uuid-dev # from the communuty documentation
- sudo apt-get install build-essential libssl-dev uuid-dev zlib1g-dev libncurses5-dev libx11-dev python-dev # from feedback in the forums; maybe the community documentation should be updated to reflect these needs as well, but I don't know how that process works
- wget [http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz](http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz)
- tar xfz xen-4.0.1.tar.gz
- cd xen-4.0.1
- nano buildconfigs/src.git-clone
# Replace Line
# (cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); \
# with:
# (cd $(LINUX_SRCDIR).tmp; git checkout -b local/$(XEN_LINUX_GIT_LOCALBRANCH) --track $(XEN_LINUX_GITREV) ); \
- make world
- sudo make install
 
Unfortunately, the custom boot target info in the community docs don't seem to match the /boot directory I ended up with, but I'll research that problem separately and if I can't find the info I'll post under a separate thread.
 
Thanks so much to everyone,
 
Scott

---

### Post by slooksterpsv on 2010-12-11
Well that was worthless... I tried to compile it it gave me an error said the branch already existed so I did sudo make install and it started to download again :(. This is horrible! I don't want to have to keep redownloading TONS of files. Where is the tar.gz of all the files? Quit wasting my bandwidth, quit wasting your bandwidth... Overall I may try again here in a min after I calm down but I'm so mad that I've downloaded it 3 times already!

---

### Post by dnp.romi on 2011-01-02
Hey shadower did u succeed in installing XEN in UBUNTU 10.10 ?? ... i followed all the instructions as per
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) but futile .... i get an error message while restarting xen from grub ...
cannot mount root on any filesystem .

---

### Post by paniag on 2011-01-03
I was able to get `make world' past the originally posted error by making the following changes to makefiles:

[LIST=1]
[*]xen-4.0.1/tools/ioemu-qemu-xen/Makefile
```
-include $(SRC_PATH)/rules.mak
+#include $(SRC_PATH)/rules.mak
+include ./rules.mak
```
[*]xen-4.0.1/tools/ioemu-qemu-xen/i386-dm/Makefile
```
-include $(SRC_PATH)/rules.mak
+#include $(SRC_PATH)/rules.mak
+include ../rules.mak
```
[/LIST]

I figured this was worth a shot because a quick check shows that there is a unique `rules.mak' file in the sources:

```
xen-4.0.1> find /path-to-xen-4.0.1 -name 'rules.mak'
/path-to-xen-4.0.1/tools/ioemu-qemu-xen/rules.mak
```

`make world' is currently building drivers with no new complaints. I'll post an update after I can learn more.

---

### Post by paniag on 2011-01-03
`make world' now fails as follows:

```
make[11]: Entering directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios/32bit/tcgbios'
gcc   -O2 -fomit-frame-pointer -m32 -march=i686 -fno-strict-aliasing -std=gnu99 -Wall -Wstrict-prototypes -Wno-unused-value -Wdeclaration-after-statement  -D__XEN_TOOLS__ -MMD -MF .tcgbios.o.d  -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -mno-tls-direct-seg-refs -DNDEBUG -Werror -fno-stack-protector -fno-exceptions -fno-builtin -msoft-float -I../../../../../tools/include -I.. -I../.. -c -o tcgbios.o tcgbios.c
In file included from /usr/include/features.h:387,
                 from /usr/include/stdint.h:26,
                 from ../rombios_compat.h:8,
                 from tcgbios.c:24:
/usr/include/gnu/stubs.h:7: fatal error: gnu/stubs-32.h: No such file or directory
compilation terminated.
make[11]: *** [tcgbios.o] Error 1
make[11]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios/32bit/tcgbios'
make[10]: *** [subdir-all-tcgbios] Error 2
make[10]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios/32bit'
make[9]: *** [subdirs-all] Error 2
make[9]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios/32bit'
make[8]: *** [subdir-all-32bit] Error 2
make[8]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios'
make[7]: *** [subdirs-all] Error 2
make[7]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware/rombios'
make[6]: *** [subdir-all-rombios] Error 2
make[6]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware'
make[5]: *** [subdirs-all] Error 2
make[5]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/eric/src/xen-4.0.1/tools/firmware'
make[3]: *** [subdir-install-firmware] Error 2
make[3]: Leaving directory `/home/eric/src/xen-4.0.1/tools'
make[2]: *** [subdirs-install] Error 2
make[2]: Leaving directory `/home/eric/src/xen-4.0.1/tools'
make[1]: *** [install-tools] Error 2
make[1]: Leaving directory `/home/eric/src/xen-4.0.1'
make: *** [world] Error 2
```

I found a solution here: [http://bderzhavets.wordpress.com/2010/10/15/set-up-xen-4-0-1-libvirt-0-8-3-on-top-of-ubuntu-10-10-desktop/#comment-1316]("http://bderzhavets.wordpress.com/2010/10/15/set-up-xen-4-0-1-libvirt-0-8-3-on-top-of-ubuntu-10-10-desktop/#comment-1316")

After installing gcc-multilib (per above reference) and xfig (to build documentation) `make world' now completes without issue.

PS: 'uname -a', 'cat /proc/cpuinfo', 'sudo lshw' output included in attached file.

---

### Post by MTDrifter on 2011-01-04
shadower, just wondering if you ever got XEN up and running. I've been messing with this off and on since my last post. I'm able to compile without getting errors (took a whole list of libs to install first).

Now the issue is with the boot targets in grub (/etc/grub.d/40_custom) 

Grub is still complaining about "dpkg: version '/boot/xen.gz' has bad syntax: invalid character in version number"

it's almost getting to be a habit starting over trying to figure out what I'm doing wrong.

Please post an update on steps taken to install Xen if you've successfully installed it.

Thanks!

---

### Post by paniag on 2011-01-05
I have successfully booted Xen, and Xen successfully loads the Dom0 OS graphical interface. I'm reading now about configuring and creating Xen VMs so I can test VM creation and administration.

Included below is my record of what I did. I have put all the packages I installed up front. Note that some of these steps (namely the first 5) were just to set up the OS (10.10 Desktop on x86_64) for my use. I chose not to remove these lines simply for completeness.

```
sudo apt-get install openssh-server tmux zsh vim screen htop ipython colordiff
scp -r -P 443 paniag@galactica.local:"{.ssh/config,.vim,.screenrc,.tmux.conf,.zshrc,.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml}" .
mv %gconf .gconf/apps/gnome-terminal/profiles/Default/
mv config .ssh/
chsh -s /bin/zsh

# BEGIN for Xen
sudo apt-get install gettext bin86 bcc libc-dev-bin iasl texinfo git uuid-dev latex209-bin pciutils-dev
sudo apt-get install build-essential libssl-dev uuid-dev zlib1g-dev libncurses5-dev libx11-dev python-dev
sudo apt-get install bridge-utils xfig mercurial
# required for 64-bit architecture
sudo apt-get install gcc-multilib
# END for Xen

-------------------------------------------------

wget "http://bits.xensource.com/oss-xen/release/4.0.1/xen-4.0.1.tar.gz"
tar xvzf xen-4.0.1.tar.gz
cd xen-4.0.1

vim buildconfigs/src.git-clone
# Replace Line
# (cd $(LINUX_SRCDIR).tmp; git checkout -b $(XEN_LINUX_GIT_LOCALBRANCH) $(XEN_LINUX_GITREV) ); \
# with:
# (cd $(LINUX_SRCDIR).tmp; git checkout -b local/$(XEN_LINUX_GIT_LOCALBRANCH) --track $(XEN_LINUX_GITREV) ); \

vim tools/ioemu-qemu-xen/Makefile
# Replace Line
# include $(SRC_PATH)/rules.mak
# with:
# include ./rules.mak

vim tools/ioemu-qemu-xen/i386-dm/Makefile
# Replace Line
# include $(SRC_PATH)/rules.mak
# with:
# include ../rules.mak

make world  # Hung on 'latex -c user.tex > /dev/null'; I killed it and moved on
sudo make install   # Hung on 'latex -c user.tex > /dev/null'; I killed it and reran the other install targets:
sudo make install-xen install-kernels install-tools install-stubdom

sudo vim /etc/default/grub
# Comment out the following lines:
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true

# In this step, the 2 'module' entries were customized based on the content of my /boot
sudo vim /etc/grub.d/40_custom
# Add following entry:
# menuentry "Xen 4.01  2.6.32.25 pvops" {
# insmod part_msdos
# insmod ext2
# set root=(hd0,msdos1)
# search --no-floppy --fs-uuid --set fb9cfc1f-5e1f-42bf-8964-193a01ede70b
# multiboot /boot/xen.gz
# module /boot/vmlinuz-2.6.32.27 root=/dev/sda1 # changed to reflect only vmlinuz file present
# module /boot/initrd-2.6.32.27.img # changed to reflect initrd created below
# }

make linux-2.6-pvops-config CONFIGMODE=menuconfig
# Enable Ext4 filesystem (no other changes)

make linux-2.6-pvops-build
sudo make linux-2.6-pvops-install
sudo depmod 2.6.32.27
sudo mkinitramfs -o /boot/initrd-2.6.32.27.img 2.6.32.27
sudo update-grub
sudo reboot
# When booting, I had to scroll to the bottom of the grub menu to find this new entry. There were a bunch of auto-generated entries added before it.

# for some reason, I was getting a python import error on module xen when trying to start xend
sudo vim /usr/lib/python2.6/sitecustomize.py
# Inside the try block, add lines:
#   import sys
#   sys.path.append('/usr/lib/python2.6/site-packages')
```

Best of luck with your own installations. I'll let you know if I can successfully work with VMs or if I encounter some further problem.

---

### Post by slooksterpsv on 2011-01-08
So I've tried before, but it would panic when booting into a Xen kernel, may have to go through your instructions and see if those work. Then we need an article created specifically for 10.10 on how to do it.

---

### Post by rwoods3 on 2011-01-09
Been trying for a couple of days now to get this setup and figured this would be the best thread to post this in. I too am receiving an error when running sudo make world. I didn't notice this error in any of the other replies so here it is:

Checking out files: 100% (30571/30571), done.
+ cd linux-2.6-pvops.git.tmp
+ git checkout xen/master
error: pathspec 'xen/master' did not match any file(s) known to git.
make[3]: *** [linux-2.6-pvops.git/.valid-src] Error 1
make[3]: Leaving directory '/home/rwoods3/xen/xen-4.0.0'
make[2]: *** [linux-2.6-pvops-install] Error 2
make[2]: Leaving directory '/home/rwoods3/xen/xen-4.0.0'
make[1]: *** [install-kernals] Error 1
make[1]: *** [world] Error 2

A suggestion in another forum was to let **xen**/**master** point(symlink) to xen/stable-2.6.32.x branch as the xen/master branch is obsolete and has been for a while according to the post. I tried running the follow as was suggested in another post on a different forum:
 
git clone git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-xen (this will take about 15-20 minutes)
 cd reset &#8211;hard
 git checkout -b xen/stable-2.6.32.x origin/xen/stable-2.6.32.x
 git pull
 ln -s xen/master xen/stable-2.6.32.x

 Reran sudo make world and got the same error above.

 Any ideas or suggestions???

---

### Post by hirantha on 2011-02-05
I'm getting the following error..
[B]=================================
make -f buildconfigs/mk.linux-2.6-pvops build
make[3]: Entering directory `/home/hirantha/xen-4.0.1'
set -ex; \
	if ! [ -d linux-2.6-pvops.git ]; then \
		rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp; \
		mkdir linux-2.6-pvops.git.tmp; rmdir linux-2.6-pvops.git.tmp; \
		git clone -o xen -n git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-pvops.git.tmp; \
		(cd linux-2.6-pvops.git.tmp; git checkout -b xen/stable-2.6.32.x xen/xen/stable-2.6.32.x ); \
		mv linux-2.6-pvops.git.tmp linux-2.6-pvops.git; \
	fi
+ '[' -d linux-2.6-pvops.git ']'
+ rm -rf linux-2.6-pvops.git linux-2.6-pvops.git.tmp
+ mkdir linux-2.6-pvops.git.tmp
+ rmdir linux-2.6-pvops.git.tmp
+ git clone -o xen -n git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-pvops.git.tmp
Initialized empty Git repository in /home/hirantha/xen-4.0.1/linux-2.6-pvops.git.tmp/.git/
fatal: Unable to look up git.kernel.org (port 9418) (Name or service not known)
make[3]: *** [linux-2.6-pvops.git/.valid-src] Error 128
make[3]: Leaving directory `/home/hirantha/xen-4.0.1'
make[2]: *** [linux-2.6-pvops-install] Error 2
make[2]: Leaving directory `/home/hirantha/xen-4.0.1'
make[1]: *** [install-kernels] Error 1
make[1]: Leaving directory `/home/hirantha/xen-4.0.1'
make: *** [world] Error 2
=============================[/B]

Since I can not configure my modem to work with ubuntu 10.10, I checked out the branch from windows. How can i use that local branch to complete the Xen installation? Do i need to modify some files? If so what are those and How ?

---

### Post by visvp on 2011-02-08
Hi Shadower,

I am also facing the same problem in "make world" as you have posted. Were you able to install Xen on Ubuntu successfully?
If you have the procedure of doing it, can you please post it in this thread.

Thanks,
visvp

---

