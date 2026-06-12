---
title: "Attempt to create Xen PV DomU for Intrepid Server via python-vm-builder"
date: 2008-12-28
forum: Virtualisation
---

### Post by dbaxps on 2008-12-28
Environment Ubuntu 8.10 Server (x86_64) with Ubuntu Desktop installed
via tasksel. Follow :-
[http://www.howtoforge.com/creating-virtual-machines-for-xen-kvm-vmware-workstation-6-vmware-server-with-vmbuilder-on-ubuntu-8.10](http://www.howtoforge.com/creating-virtual-machines-for-xen-kvm-vmware-workstation-6-vmware-server-with-vmbuilder-on-ubuntu-8.10)
Script to create Xen PV DomU per mentioned above "Howto":-
vmbuilder xen ubuntu --suite=intrepid --flavour=virtual --arch=amd64  \
--mirror=http://192.168.1.33:9999/ubuntu -o --tmpfs=- --ip=192.168.1.47 --domain=. \
--part=vmbuilder.partition --templates=mytemplates --user=boris \
--name=UbuntuPV --pass=aaaaaa --addpkg=vim-nox  \
--addpkg=acpid --firstboot=boot.sh --mem=1024 --hostname=vm7
Output :-
root@ServerIntrepid:~/vm7# ./build.sh
2008-12-28 08:31:27,270 INFO     Creating filesystem
2008-12-28 08:31:27,271 INFO     Not preallocated, so we create it.
2008-12-28 08:31:27,271 INFO     A name wasn't specified either, so we make one up: /tmp/vmbuilderm9yqh6/root.img
2008-12-28 08:31:27,322 INFO     mke2fs 1.41.3 (12-Oct-2008)
2008-12-28 08:31:31,934 INFO     Creating filesystem
2008-12-28 08:31:31,934 INFO     Not preallocated, so we create it.
2008-12-28 08:31:31,934 INFO     A name wasn't specified either, so we make one up: /tmp/vmbuilderm9yqh6/swap.img
2008-12-28 08:31:31,967 INFO     Creating filesystem
2008-12-28 08:31:31,968 INFO     Not preallocated, so we create it.
2008-12-28 08:31:31,968 INFO     A name wasn't specified either, so we make one up: /tmp/vmbuilderm9yqh6/____.img
2008-12-28 08:31:31,986 INFO     mke2fs 1.41.3 (12-Oct-2008)
2008-12-28 08:31:34,767 INFO     Mounting target filesystems
2008-12-28 08:31:34,775 INFO     Installing guest operating system. This might take some time...
2008-12-28 08:32:36,242 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:36,243 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:36,243 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:36,844 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,402 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,403 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,403 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,404 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,404 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,404 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,405 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,405 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,405 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,406 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,406 INFO     find: `/var/cache/fontconfig': No such file or directory
2008-12-28 08:32:41,407 INFO     find: `/var/cache/fonts': No such file or directory
2008-12-28 08:32:41,407 INFO     find: `/var/cache/anthy': No such file or directory
2008-12-28 08:32:41,407 INFO     find: `/var/lib/belocs': No such file or directory
2008-12-28 08:32:41,408 INFO     find: `/var/lib/gconf': No such file or directory
2008-12-28 08:32:41,408 INFO     find: `/var/lib/defoma': No such file or directory
2008-12-28 08:32:41,408 INFO     find: `/var/log/installer': No such file or directory
2008-12-28 08:32:41,409 INFO     find: `/initrd.img': No such file or directory
2008-12-28 08:32:41,409 INFO     find: `/vmlinuz': No such file or directory
2008-12-28 08:32:41,409 INFO     find: `/cdrom': No such file or directory
2008-12-28 08:32:41,409 INFO     find: `/media/cdrom': No such file or directory
2008-12-28 08:32:41,410 INFO     find: `/usr/share/fonts': No such file or directory
2008-12-28 08:32:41,410 INFO     find: `/var/lib/anthy': No such file or directory
2008-12-28 08:32:41,410 INFO     find: `/var/lib/defoma': No such file or directory
2008-12-28 08:32:41,411 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,411 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,411 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:41,415 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-28 08:32:44,236 INFO     Updating certificates in /etc/ssl/certs....done.
2008-12-28 08:32:44,237 INFO     Running hooks in /etc/ca-certificates/update.d....done.
2008-12-28 08:32:44,237 INFO     grep: /proc/self/status: No such file or directory
2008-12-28 08:32:44,238 INFO     Use of uninitialized value $x in scalar assignment at /usr/share/perl/5.10/utf8_heavy.pl line 242.
2008-12-28 08:32:44,238 INFO     Use of uninitialized value $x in pattern match (m//) at /usr/share/perl/5.10/utf8_heavy.pl line 243.
2008-12-28 08:32:44,239 INFO     Use of uninitialized value $uni in pattern match (m//) at /usr/bin/ckbcomp line 3109.
2008-12-28 08:32:44,239 INFO     Use of uninitialized value $uni in pattern match (m//) at /usr/bin/ckbcomp line 3109.
2008-12-28 08:32:44,239 INFO     Use of uninitialized value $uni in pattern match (m//) at /usr/bin/ckbcomp line 3109.
2008-12-28 08:32:44,240 INFO     Use of uninitialized value $uni in pattern match (m//) at /usr/bin/ckbcomp line 3109.
2008-12-28 08:32:44,240 INFO     update-initramfs: deferring update (trigger activated)
2008-12-28 08:32:44,244 INFO     Copying to disk images
2008-12-28 08:32:47,393 INFO     Unmounting target filesystem
2008-12-28 08:32:48,025 INFO     Moving /tmp/vmbuilderm9yqh6/root.img to ubuntu-xen/root.img
2008-12-28 08:32:56,429 INFO     Moving /tmp/vmbuilderm9yqh6/swap.img to ubuntu-xen/swap.img
2008-12-28 08:32:57,291 INFO     Moving /tmp/vmbuilderm9yqh6/____.img to ubuntu-xen/____.img
2008-12-28 08:33:00,946 INFO     Cleaning up
I've attempted to load created PV DomU at Xen 3.3.1-RC4 CentOS 5.2 Dom0
Loading got stuck when attempted to lock /var/lib/dpkg 
Sending to console "are you root ?"

---

