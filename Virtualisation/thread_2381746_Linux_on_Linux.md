---
title: "Linux on Linux"
date: 2018-01-04
forum: Virtualisation
---

### Post by al892 on 2018-01-04
I installed Ubuntu PowerPC remix on an X5000 (e5500 cpu). Then, I setup in a chroot environment I setup Debian wheezy X86. 

This is what I did:
First, I installed all the other dependencies with pkgsrc for qemu except zlib. 
sudo -s
wget **[http://zlib.net/zlib-1.2.11.tar.gz](http://zlib.net/zlib-1.2.11.tar.gz)**
gzip -xvzpf  zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure 
make
make install

Install qemu:
git clone [**git://git.qemu.org/qemu.git**]("git://git.qemu.org/qemu.git")
cd qemu
./configure --target-list=i386-linux-user --static
make 

setup chroot:
mount -t binfmt_misc none /proc/sys/fs/binfmt_misc
echo -1 > /proc/sys/fs/binfmt_misc/status
echo   ':i386:M::\x7fELF\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\x03:\xff\xff\xff\xff\xff\xfe\xfe\xff\xff\xff\xff\xff\xff\xff\xff\xff\xfb\xff\xff:/usr/bin/qemu-i386-static:'  > /proc/sys/fs/binfmt_misc/register
debootstrap --arch=i386 --foreign wheezy chroot-wheezy-i386 **[http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian)**
cp ~/qemu/i386-linux-user/qemu-i386 ~/chroot-wheezy-i386/usr/bin/qemu-i386-static
DEBIAN_FRONTEND=noninteractive  DEBCONF_NONINTERACTIVE_SEEN=true LC_ALL=C LANGUAGE=C LANG=C chroot  chroot-wheezy-i386 /debootstrap/debootstrap --second-stage
echo "deb **[http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/)** wheezy main" > chroot-wheezy-i386/etc/apt/sources.list.d/wheezy.list
env -i TERM=xterm /usr/sbin/chroot chroot-wheezy-i386 /bin/su -l root

I then typed arch and was told I was on a X86 system, but it doesn't work as I had hoped. For example: it give me an error: 
ubuntu:~$ iceweasel
bash: /usr/bin/iceweasel: cannot execute binary file

---

### Post by TheFu on 2018-01-05
First, a powerpc is not an x86.  You need for qemu to emulate a powerpc architecture if you want Ubuntu PowerPC remix to run.

---

