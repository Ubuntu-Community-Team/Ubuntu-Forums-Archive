---
title: "Installing Grsec kernel"
date: 2006-09-01
forum: Server Platforms
---

### Post by b0red on 2006-09-01
Hi All,
I'm trying to install a GRsec kernel but have'nt found a decent how-to on the matter.
This gave me some idea [http://www.evolution-security.com/modules.php?name=News&file=article&sid=250](http://www.evolution-security.com/modules.php?name=News&file=article&sid=250)
as did the grsec docs,
I'm not sure what kernel source to download from kernel.org though
I'm running kernel 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

But there's no kernel 2.16.15-26 at kernel.org or am i looking at the wrong thing?

Has anyone had any experience of doing this and can they give me a pointer?

---

### Post by felosi on 2006-09-01
grsecurity is more of a kernel for servers that is open to the public and has users and such.
You go to grsecurity.net and see the latest patch for 2.6 kernel and I think it is 2.6.17.11 now , the latest one and you go grab that patch and the kernel and go to town.
But if you are doing this on a personal pc you dont need it, ubuntu kernel is fine. I used to like that ck kernel but it ended up causing problems. 
Stay with ubuntu kernel, it is secure and good for home pc. Dont know about server though which I would never use ubuntu on server, desktop only ;)

---

### Post by b0red on 2006-09-01
OK did this to get headers
apt-get install build-essential linux-headers-2.6.15-26-386 copied grsec patch to /usr/src

root@mercury:/usr/src# ls
grsecurity-2.1.9-2.4.33.2-200608231938.patch.gz  linux-headers-2.6.15-26  linux-headers-2.6.15-26-386
root@mercury:/usr/src# gunzip < grsecurity-2.1.9-2.4.33.2-200608231938.patch.gz |patch -p0
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urNp linux-2.4.33.2/arch/alpha/config.in linux-2.4.33.2/arch/alpha/config.in
|--- linux-2.4.33.2/arch/alpha/config.in        2006-08-19 08:43:49.000000000 -0400
|+++ linux-2.4.33.2/arch/alpha/config.in        2006-08-20 15:15:12.000000000 -0400
--------------------------
File to patch:  

...what next?

---

### Post by felosi on 2006-09-01
You have to get the kernel for 2.6.17.11, unzip it and then run the patch it will look in the directory for linux-2.6.17.11 
 I will make an updated tut this evening but you just replace the new file names where the other ones are.

Again though, grsecurity is really only helpful for servers or something where you will be having shell users

---

### Post by felosi on 2006-09-01
Ok updated walkthrough

```
 sudo apt-get install build-essential bin86 kernel-package

sudo apt-get install libqt3-headers libqt3-mt-dev (needed for make xconfig)
```

First get what is needed and patch the kernel.
```

cd /usr/src
```
```

wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.11.tar.bz2
```

```
wget grsecurity-2.1.9-2.6.17.11-200608282236.patch.gz
```

```
tar -xjvf linux-2.6.17.7.tar.bz2
```

```

gunzip < grsecurity-2.1.9-2.6.17.7-200607261817.patch.gz | patch -p0
```
```

mv linux-2.6.17.7 linux-2.6.17.7-grsec
```

```
ln -s linux-2.6.17.7-grsec linux
```

```
cd linux
```

copy your current config over

do uname -r to see what kernel your running and copy it, example:
```

cp /boot/config-2.6.15-26-686L .config
```

*Configure the kernel:

```
sudo make xconfig
```
 For servers use 
```
sudo make menuconfig
```
if you are doing this on a server use make menuconfig

make sure you select the basic stuff that is needed, iptables, your processor type, and then go in Security Options and to grsecurity, select which level of security you want and any other options you may want.

*In a terminal make sure you are in /usr/src/linux with full root access.

We will build a ".deb" file that can be installed in our Ubuntu system, using make-kpkg.

*In a terminal type:

```
make-kpkg clean

make-kpkg -initrd --revision=gr2 kernel_image



```

If there wasn't errors this will build the kernel and a ".deb" file will be created at /usr/src.
*To install it:

```
sudo dpkg -i kernel-image-2.6.17*.deb
```

Now reboot and if you did everything correctly it should boot back up and you will be using the new grsecurity kernel.

---

### Post by b0red on 2006-09-03
Followed the instructions exactly went fine up to this point

root@Mercury:/usr/src/linux# make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
qconf: cannot connect to X server
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2

---

### Post by b0red on 2006-09-05
I've done exactly as the walkthrough says , installed everything via apt-get

so far....
used apt-get to get all my packages
Downloaded kernel 2.6.17 unpacked it
Applied patch applied perfectly

>>>copying in generic-config to usr/src and /usr/src/linux-2.6.17.11

root@Mercury:/usr/src# cp /home/b0red/grsec/generic-config .

root@Mercury:/usr/src# cp /home/b0red/grsec/generic-config /usr/src/linux-2.6.17.11

>>>renaming linux-2.6.17.11 linux-2.6.17.11-grsec

root@Mercury:/usr/src# mv linux-2.6.17.11 linux-2.6.17.11-grsec

>>>creating a symlink called linux with linux-2.6.17.11-grsec

root@Mercury:/usr/src# ln -s linux-2.6.17.11-grsec/ linux

>>>switch to linux symlink

root@Mercury:/usr/src# cd linux

>>>copying in my boot config

root@Mercury:/usr/src/linux# cp /boot/config-2.6.15-26-386 .config


>>>Make xconfig and dies <<<

root@Mercury:/usr/src/linux# make xconfig
HOSTCC scripts/basic/fixdep
HOSTCC scripts/basic/split-include
HOSTCC scripts/basic/docproc
CHECK qt
HOSTCC scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
HOSTCC scripts/kconfig/kconfig_load.o
HOSTCC scripts/kconfig/kxgettext.o
HOSTCC scripts/kconfig/mconf.o
SHIPPED scripts/kconfig/zconf.tab.c
SHIPPED scripts/kconfig/lex.zconf.c
SHIPPED scripts/kconfig/zconf.hash.c
HOSTCC scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
HOSTCXX scripts/kconfig/qconf.o
HOSTLD scripts/kconfig/qconf
scripts/kconfig/qconf arch/i386/Kconfig
qconf: cannot connect to X server
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2

---

### Post by felosi on 2006-09-07
use make menuconfig then ;)
You are probably missing some qt libs or something, Make menuconfig is same thing excpet ncurses. On server you cant use xconfig either.

---

### Post by b0red on 2006-09-08
Make menu config did'nt work either.
Needed to apt-get install ncurses-dev then it worked.

I ran make-kpkg clean make-kpkg -initrd --revision=gr2 kernel_image
and got the following error

make-kpkg clean make-kpkg -initrd --revision=gr2 kernel_image
Error: Unknown target make-kpkg
use --targets to display help on valid targets.
(I then realised it was actually 
make kpkg clean make kpkg -initrd --revision=gr2 kernel_image
but there is no --evision option in make kpkg)

I then tried
make dep bzImage modules modules_install install
(per the grsec quickstart guide)

and the kernel compiled..and i got this message at the end

GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.17.11-grsec

I edited menu.lst to
title Ubuntu, kernel 2.6.17.11-grsec
root (hd0,1)
kernel /boot/vmlinuz-2.6.17.11-grsec root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

but on boot I get the error cannot find /dev/hda2 (where my O/S is) I think it's to do with the /boot/initrd.img-2.6.15-26-386 as the grsec kernel did not produce it's own initrd.img file i used the last existing one.

as a last point when i try to boot with the new kernel I get an error saying cannot find /lib/modules/vmlinuz-2.6.17.11-grsec.something.temp
alert cannot open /dev/hda2

it then drops to a shell when i do uname -aI get vmlinuz-2.6.17.11-grsec
so I think I'm getting there.

---

### Post by felosi on 2006-09-09
> **b0red said:**
> Make menu config did'nt work either.
Needed to apt-get install ncurses-dev then it worked.

I ran make-kpkg clean make-kpkg -initrd --revision=gr2 kernel_image
and got the following error

make-kpkg clean make-kpkg -initrd --revision=gr2 kernel_image
Error: Unknown target make-kpkg
use --targets to display help on valid targets.
(I then realised it was actually 
make kpkg clean make kpkg -initrd --revision=gr2 kernel_image
but there is no --evision option in make kpkg)

I then tried
make dep bzImage modules modules_install install
(per the grsec quickstart guide)

and the kernel compiled..and i got this message at the end

GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.17.11-grsec

I edited menu.lst to
title Ubuntu, kernel 2.6.17.11-grsec
root (hd0,1)
kernel /boot/vmlinuz-2.6.17.11-grsec root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

but on boot I get the error cannot find /dev/hda2 (where my O/S is) I think it's to do with the /boot/initrd.img-2.6.15-26-386 as the grsec kernel did not produce it's own initrd.img file i used the last existing one.

as a last point when i try to boot with the new kernel I get an error saying cannot find /lib/modules/vmlinuz-2.6.17.11-grsec.something.temp
alert cannot open /dev/hda2

it then drops to a shell when i do uname -aI get vmlinuz-2.6.17.11-grsec
so I think I'm getting there.

Well after some testing I found out that the only way to make it work is doing it the regular way, same as centos/red hat. For some reason its not making the deb package right. 
It did do ok on the 2.6.17.7 grsecurity just not the new ones.

this right here should work 
[http://www.evolution-security.com/modules.php?name=News&file=article&sid=245](http://www.evolution-security.com/modules.php?name=News&file=article&sid=245)

are you doing this on a server? Again, there is really no need for this on a home pc unless you got ssh server and such running to the public

good luck

---

### Post by b0red on 2006-09-10
This is currently being done on a test bed, prior to going on a production server.

This is one of many security precautions being taken.

BTW the command line was wrong it should have been 

make-kpkg clean ; make-kpkg -init --revision=gr2 kernel_image

that allows the kernel to compile correctly.

---

### Post by felosi on 2006-09-13
> **b0red said:**
> This is currently being done on a test bed, prior to going on a production server.

This is one of many security precautions being taken.

BTW the command line was wrong it should have been 

make-kpkg clean ; make-kpkg -init --revision=gr2 kernel_image

that allows the kernel to compile correctly.

thanks, Something must have changed with this release because we have been doing them up until now like that, same way as ck. Ill update the walkthrough, To be honest seems like centos is the way to go server wise anymore. I love ubuntu for the desktop but would never consider it for a server. SOme things on rh distros like the service commands, the way it runs apache, and so on is just much easier and better if you have to go in your box and do some things in a hurry

---

