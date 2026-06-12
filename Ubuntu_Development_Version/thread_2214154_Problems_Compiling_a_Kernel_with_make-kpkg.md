---
title: "Problems Compiling a Kernel with make-kpkg"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by forest2 on 2014-03-30
Hi,

I'm  on Ubuntu Studio 14.04 Beta 2 (upgraded through apt-get from Beta 1,)  and I'm trying to compile my own low-latency kernel with make-kpkg. I  just want to remove xhci-hda and ehci-hda from the kernel so my USB  Audio Interface (the [PreSonus AudioBox 1818VSL]("https://www.presonus.com/products/AudioBox-1818VSL")) will work correctly. With the xhci-hda driver built into the kernel, the AudioBox is treated as a usb 3 device and there is crackling noise in the playback. I've found this problem [reported by other presonus users elsewhere]("https://forums.presonus.com/posts/list/33427.page"). Here are the [details on xchi-hda and the kernel]("http://www.pcl-developers.org/xhci-hcd-I-hate-you-USB-3-0-and-Primesense-Asus-Xtion-td5707949.html").

I modify the config file via make  menuconfig, but then when I run

sudo make-kpkg clean

 I get the following output:

```

exec make kpkg_version=12.036+nmu3 -f /usr/share/kernel-package/ruleset/minimal.mk clean
====== making target minimal_clean [new prereqs: ]======
This is kernel package version 12.036+nmu3.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=i386 distclean
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-12-lowlatency'
  CLEAN   .
/usr/src/linux-headers-3.13.0-12-lowlatency/drivers/net/dpa/Makefile:7: /usr/src/linux-headers-3.13.0-12-lowlatency/drivers/net/dpa/NetCommSw/ncsw_config.mk: No such file or directory
make[4]: *** No rule to make target `/usr/src/linux-headers-3.13.0-12-lowlatency/drivers/net/dpa/NetCommSw/ncsw_config.mk'.  Stop.
make[3]: *** [drivers/net/dpa] Error 2
make[2]: *** [drivers/net] Error 2
make[1]: *** [_clean_drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-12-lowlatency'
make: *** [minimal_clean] Error 2

```
 
The same thing happens with the 3.13.0-20-lowlatency version of the kernel as well. I have the build-essential package installed as well as linux-headers-lowlatency and linux-headers-generic. It seems like the device driver ncsw_config.mk is just missing, and I've filed a bug, but I thought someone more experience with compiling kernels might have some other advice? Any ideas?

---

### Post by su:bhatta on 2014-03-30
Am I missing something or  are you compiling the 3.13.0-12 low-latency kernel? 

 Todays or maybe yesterdays upgrade brought in the 3.13.0-20 kernel.

From my system:
```
~$ uname -a
Linux  3.13.0-20-lowlatency #42-Ubuntu SMP PREEMPT Fri Mar 28 10:25:59 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

In case you are updating with CLI, then use :

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Make sure you have linux- lowlatency installed, otherwise the upgrades will not bring in the latest kernel.

```

sudo apt-get install linux-lowlatency
```

BTW, all 14.04 posts go to Ubuntu +1, be it any flavor.

---

### Post by forest2 on 2014-03-30
> **bhattabhishek said:**
> Am I missing something or  are you compiling the 3.13.0-12 low-latency kernel? 

 Todays or maybe yesterdays upgrade brought in the 3.13.0-20 kernel.


Thank you for the quick response. Originally, I tried compiling the 3.13.0-20 low latency kernel but encountered the same problem. So then I tried it with the 3.13.0-12 low latency kernel, thinking maybe that might work. I get the same error with either one. I tried the generic (high-latency?) kernel and encountered the same error there as well.

> **bhattabhishek said:**
> 
In case you are updating with CLI, then use :

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Make sure you have linux- lowlatency installed, otherwise the upgrades will not bring in the latest kernel.


I do have linux-lowlatency installed. I'm not sure what you mean by "CLI." I'm upgrading via apt-get, but I hadn't though to do a dist-upgrade. I was just doing

sudo apt-get update
sudo apt-get upgrade

and then

sudo apt-get install package-name

for any packages that were being held-back. I'll try a dist-upgrade when I get home.

> **bhattabhishek said:**
> 
BTW, all 14.04 posts go to Ubuntu +1, be it any flavor.

Sorry about that.

---

### Post by su:bhatta on 2014-03-31
> **forest2 said:**
> 
I do have linux-lowlatency installed. I'm not sure what you mean by "CLI." 
Sorry about that.

CLI=Command Line :)

Dont be sorry I also learn't it the same way, last year.

Did you get the 3.13.0-20 lowlatency? using:

```
sudo apt-get dist-upgrade
```

Also, I learnt from experienced members to run

```

sudo apt-get -f install
```

after every upgrade & dist-upgrade, to make sure there are no broken upgrades that might corrupt the system

---

### Post by cariboo on 2014-03-31
@forest2, you have to pay attention to what the error message says. In your case it says that there is a missing directory or file:

```
/usr/src/linux-headers-3.13.0-12-lowlatency/drivers/net/dpa/NetCommSw/ncsw_config.mk: No such file or directory
```

Have you checked to see if the above mentioned directory and file exists?

---

### Post by forest2 on 2014-03-31
> **cariboo907 said:**
> @forest2, you have to pay attention to what the error message says. In your case it says that there is a missing directory or file:

```
/usr/src/linux-headers-3.13.0-12-lowlatency/drivers/net/dpa/NetCommSw/ncsw_config.mk: No such file or directory
```

Have you checked to see if the above mentioned directory and file exists?

Yes, of course, I've gone to the directory and the file is missing. As I said, I've filed a bug report

[https://bugs.launchpad.net/ubuntustudio/+bug/1299878](https://bugs.launchpad.net/ubuntustudio/+bug/1299878)

but it seems odd that one random driver would be missing. This is a feature I don't even think I need, but I can't find the place in menuconfig or in the .config file to turn it off.

---

### Post by forest2 on 2014-03-31
> **bhattabhishek said:**
> CLI=Command Line :)

Did you get the 3.13.0-20 lowlatency? using:

```
sudo apt-get dist-upgrade
```

Also, I learnt from experienced members to run

```

sudo apt-get -f install
```

after every upgrade & dist-upgrade, to make sure there are no broken upgrades that might corrupt the system

I originally got the 3.13.0-20 kernel by directly upgrading with

sudo apt-get install linux-lowlatency

Tonight, I also tried

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get --reinstall -f install linux-lowlatency

but there were no new files for the dist-upgrade to download and I'm still have the same error with make-kpkg clean.

---

### Post by forest2 on 2014-04-05
I added this info to the bug report, but thought I'd post it here as well:

A couple of days ago, I ran

```


 sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f dist-upgrade

```


 and thereby installed linux-headers-3.13.0-22-lowlatency. In the process, I got these errors:

```


 Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
Error! Bad return status for module build on kernel: 3.13.0-22-lowlatency (i686)
Consult /var/lib/dkms/openvswitch/2.0.1+git20140120/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
update-initramfs: Generating /boot/initrd.img-3.13.0-22-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-22-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-22-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-22-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-22-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-20-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-20-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-12-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-12-lowlatency
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up libsystemd-journal0:i386 (204-5ubuntu16) ...
Setting up python3-cairo (1.10.0+dfsg-3ubuntu2) ...
Setting up python3-gi-cairo (3.12.0-1) ...
Setting up python3-pexpect (3.1-1) ...
Setting up catfish (1.0.2-2) ...
Setting up libbaloocore4 (4:4.12.97-0ubuntu1) ...
Setting up libbalooxapian4 (4:4.12.97-0ubuntu1) ...
Setting up libbaloofiles4 (4:4.12.97-0ubuntu1) ...
Setting up linux-headers-3.13.0-22 (3.13.0-22.44) ...
Setting up linux-headers-3.13.0-22-generic (3.13.0-22.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-22-generic /boot/vmlinuz-3.13.0-22-generic
Error! Bad return status for module build on kernel: 3.13.0-22-generic (i686)
Consult /var/lib/dkms/openvswitch/2.0.1+git20140120/build/make.log for more information.
Setting up linux-headers-3.13.0-22-lowlatency (3.13.0-22.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-22-lowlatency /boot/vmlinuz-3.13.0-22-lowlatency
Error! Bad return status for module build on kernel: 3.13.0-22-lowlatency (i686)
Consult /var/lib/dkms/openvswitch/2.0.1+git20140120/build/make.log for more information.
Setting up linux-headers-generic (3.13.0.22.26) ...
Setting up linux-image-lowlatency (3.13.0.22.26) ...
Setting up linux-headers-lowlatency (3.13.0.22.26) ...
Setting up linux-lowlatency (3.13.0.22.26) ...
Processing triggers for libc-bin (2.19-0ubuntu3) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-22-lowlatency

```

In particular, does "Error! Bad return status for module build on kernel: 3.13.0-22-lowlatency (i686)" mean that I just have a bad installation? I've been troubleshooting this problem for over a week and getting nowhere. The file ncsw_config.mk is definitely missing from that directory so now what? Anyone have any ideas about what to do to fix this?

I should add that I tried making a dummy text file in the directory titled ncsw_config.mk just to see what would happen. In that case, make-kpkg clean accepted the dummy file, but then found another missing .mk file. I'm really stumped.

---

### Post by forest2 on 2014-04-15
Two  weeks later and this problem persists. It basically makes my computer  unusable for the purpose I bought it, which is making me really angry at  Ubuntu. What kind of distribution ships a buggy usb3.0 driver built  into the kernel (rather than as a module)??

 
I got desperate today and tried making a fake ncsw_config.mk file. I  just went to that directory, opened a blank file titled ncsw_config.mk in  vi, and then saved it. When I ran make-kpkg clean, it accepted the fake  file, but then told me


 ```
/usr/src/linux-headers-3.13.0-24-lowlatency/ubuntu/aufs/Makefile:2: ubuntu/aufs/magic.mk: No such file or directory
```


 so I went to /usr/src/linux-headers-3.13.0-24-lowlatency/ubuntu/aufs/ and again made a fake magic.mk file.
Now I was able to run make-kpkg  clean without any errors. I have to run it with sudo though because with  fakeroot I get errors because various permissions are denied. Then I  tried running 

sudo make-kpkg --initrd --append-to-version=.041514 kernel_image kernel_headers


 and I get the following output:


 ```

exec make kpkg_version=12.036+nmu3 -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=.041514  INITRD=YES
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.036+nmu3.
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -f debian/control || sed         -e 's/=V/3.13.9.041514/g'  \
                -e 's/=D/3.13.9.041514-10.00.Custom/g'         -e 's/=A/i386/g'  \
  -e 's/=SA//g'  \
  -e 's/=I//g'				    \
  -e 's/=CV/3.13/g'			    \
  -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'		    \
  -e 's/=ST/linux/g'      -e 's/=B/i386/g'    \
                  /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/3.13.9.041514/g'       \
            -e 's/=D/3.13.9.041514-10.00.Custom/g'        -e 's/=A/i386/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/i386/g'         \
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                            \
             /usr/share/kernel-package/changelog > debian/changelog
chmod 0644 debian/control debian/changelog
test -d ./debian/stamp || mkdir debian/stamp
make -f debian/rules debian/stamp/conf/kernel-conf
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
====== making target debian/stamp/conf/kernel-conf [new prereqs: ]======
make EXTRAVERSION=.041514   ARCH=i386 \
                    oldconfig;
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
make EXTRAVERSION=.041514   ARCH=i386 prepare
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
scripts/kconfig/conf --silentoldconfig Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
make[3]: *** No rule to make target `/usr/src/linux-headers-3.13.0-24-lowlatency/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.
make[2]: *** [archheaders] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
make[1]: *** [debian/stamp/conf/kernel-conf] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-lowlatency'
make: *** [debian/stamp/conf/minimal_debian] Error 2
Failed to create a ./debian directory:  at /usr/bin/make-kpkg line 984.

```


 I have no idea what to do. I  think I'm just going to have to use a different distro. It seems like  nobody bothered to update the kernel configuration files, but then  surely others have experienced these problems as well??

---

