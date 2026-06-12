---
title: "cannot connect to my kvm vm"
date: 2009-03-08
forum: Virtualisation
---

### Post by el_baby on 2009-03-08
Hi,

I created a VM following the instructions in [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I'm doing this on a hosted intrepid server I have no access other than ssh.

I created a bridge on my physical NIC and attached eth0 to it, it works fine.

I created my vm using

```

sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual --arch i386 \
        --components=main,restricted,universe,multiverse --libvirt qemu:///system \
        --iso=$HOME/soft/ubuntu/ubuntu-8.10-server-i386.iso \
        --mirror=http://nl.archive.ubuntu.com/ubuntu \
        --addpkg ubuntu-standard --addpkg ssh \
        --hostname=vmtest1 --domain=example.com \
        --dest /var/vm/vmtest1.example.com --overwrite \
        --user=user --name="My User" --pass=password

```
I'm copying the output of this command at the bottom of this message.

After creating the VM, I connect to libvirt using
```

$ virsh --connect qemu:///system

```
I can see the VM if I do a **list --all** and I can start it using **start vmtest1**... but I see nothing happening.

I checked the /var/lib/libvirt/dhcp-default.leases file and it's empty... I tried pinging 192.168.122.2 and I get a series of messages:
```

From 192.168.1.1 icmp_seq=1 Destination Port Unreachable

```
so fast that sometimes I can't even stop them with ^C (and I have to kill the shell from another terminal)...

I re-created the VM using a fixed **--ip=192.168.1.2** to no avail...

I put a password to the root account and tried connecting from my desktop using **virt-manager**, but it hangs trying to connect (it does ask me for the root password, so I guess the ssh handshake does work) but the virt-manager window freezes with status "connecting" to my remote host.

Is there any command to connect to the VM's console in text mode (maybe emulating a serial line console?)

Any hints will be largely appreciated.

here's the output of the **vmbuilder** command above:
```

2009-03-08 20:35:46,292 INFO     Creating disk image: /tmp/vmbuilderHE8-8J/disk0.img
2009-03-08 20:35:46,295 INFO     Adding partition table to disk image: /tmp/vmbuilderHE8-8J/disk0.img
2009-03-08 20:35:46,339 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderHE8-8J/disk0.img
2009-03-08 20:35:46,344 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderHE8-8J/disk0.img
2009-03-08 20:35:46,349 INFO     Creating loop devices corresponding to the created partitions
2009-03-08 20:35:46,357 INFO     Creating file systems
2009-03-08 20:35:46,393 INFO     mke2fs 1.41.3 (12-Oct-2008)
2009-03-08 20:35:46,936 INFO     Mounting target filesystems
2009-03-08 20:35:46,961 INFO     Installing guest operating system. This might take some time...
2009-03-08 20:49:20,537 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:20,537 INFO     Moving old data out of the way
2009-03-08 20:49:20,583 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:20,920 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-03-08 20:49:21,062 INFO     Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2009-03-08 20:49:21,063 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-03-08 20:49:21,068 INFO     Testing for an existing GRUB menu.lst file ...
2009-03-08 20:49:21,068 INFO     
2009-03-08 20:49:21,068 INFO     Could not find /boot/grub/menu.lst file.
2009-03-08 20:49:21,069 INFO     Generating /boot/grub/menu.lst
2009-03-08 20:49:21,121 INFO     Searching for splash image ... none found, skipping ...
2009-03-08 20:49:21,228 INFO     grep: /boot/config*: No such file or directory
2009-03-08 20:49:21,283 INFO     Updating /boot/grub/menu.lst ... done
2009-03-08 20:49:21,283 INFO     
2009-03-08 20:49:21,433 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-03-08 20:49:21,497 INFO     Searching for default file ... found: /boot/grub/default
2009-03-08 20:49:21,498 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-03-08 20:49:21,584 INFO     Searching for splash image ... none found, skipping ...
2009-03-08 20:49:21,609 INFO     grep: /boot/config*: No such file or directory
2009-03-08 20:49:21,667 INFO     Updating /boot/grub/menu.lst ... done
2009-03-08 20:49:21,668 INFO     
2009-03-08 20:49:21,693 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-03-08 20:49:30,253 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:30,253 INFO     Done.
2009-03-08 20:49:30,254 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:30,254 INFO     Running depmod.
2009-03-08 20:49:30,254 INFO     update-initramfs: Generating /boot/initrd.img-2.6.27-11-server
2009-03-08 20:49:32,162 INFO     Running postinst hook script /usr/sbin/update-grub.
2009-03-08 20:49:32,163 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-03-08 20:49:32,163 INFO     Searching for default file ... found: /boot/grub/default
2009-03-08 20:49:32,164 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-03-08 20:49:32,164 INFO     Searching for splash image ... none found, skipping ...
2009-03-08 20:49:32,165 INFO     grep: /boot/config*: No such file or directory
2009-03-08 20:49:32,165 INFO     Found kernel: /boot/vmlinuz-2.6.27-11-server
2009-03-08 20:49:32,166 INFO     Replacing config file /var/run/grub/menu.lst with new version
2009-03-08 20:49:32,166 INFO     Updating /boot/grub/menu.lst ... done
2009-03-08 20:49:32,166 INFO     
Extracting templates from packages: 100%
2009-03-08 20:49:44,144 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:44,145 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:44,145 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:44,146 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:44,146 INFO     No override present.
2009-03-08 20:49:44,147 INFO     Opening /proc/modules: No such file or directory
2009-03-08 20:49:53,076 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,076 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,077 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,077 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,078 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,078 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,079 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,080 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,080 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,081 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:49:53,081 INFO     Building database of manual pages ...
2009-03-08 20:50:00,225 INFO     
2009-03-08 20:50:00,225 INFO     Creating config file /etc/ufw/before.rules with new version
2009-03-08 20:50:00,225 INFO     
2009-03-08 20:50:00,226 INFO     Creating config file /etc/ufw/before6.rules with new version
2009-03-08 20:50:00,226 INFO     
2009-03-08 20:50:00,227 INFO     Creating config file /etc/ufw/after.rules with new version
2009-03-08 20:50:00,227 INFO     
2009-03-08 20:50:00,227 INFO     Creating config file /etc/ufw/after6.rules with new version
2009-03-08 20:50:00,441 INFO     Creating SSH2 RSA key; this may take some time ...
2009-03-08 20:50:01,348 INFO     Creating SSH2 DSA key; this may take some time ...
2009-03-08 20:50:02,104 INFO     
2009-03-08 20:50:02,105 INFO     Creating config file /etc/perl/XML/SAX/ParserDetails.ini with new version
2009-03-08 20:50:02,427 INFO     Replacing config file /etc/perl/XML/SAX/ParserDetails.ini with new version
2009-03-08 20:50:20,726 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,727 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,728 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,728 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,729 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,729 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,730 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,730 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,731 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,731 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,732 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,732 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,733 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,733 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,734 INFO     find: `/var/cache/fontconfig': No such file or directory
2009-03-08 20:50:20,734 INFO     find: `/var/cache/fonts': No such file or directory
2009-03-08 20:50:20,735 INFO     find: `/var/cache/anthy': No such file or directory
2009-03-08 20:50:20,735 INFO     find: `/var/lib/belocs': No such file or directory
2009-03-08 20:50:20,736 INFO     find: `/var/lib/gconf': No such file or directory
2009-03-08 20:50:20,736 INFO     find: `/var/lib/defoma': No such file or directory
2009-03-08 20:50:20,737 INFO     find: `/var/log/installer': No such file or directory
2009-03-08 20:50:20,737 INFO     find: `/cdrom': No such file or directory
2009-03-08 20:50:20,738 INFO     find: `/media/cdrom': No such file or directory
2009-03-08 20:50:20,738 INFO     find: `/usr/share/fonts': No such file or directory
2009-03-08 20:50:20,739 INFO     find: `/var/lib/anthy': No such file or directory
2009-03-08 20:50:20,739 INFO     find: `/var/lib/defoma': No such file or directory
2009-03-08 20:50:20,740 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,740 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,741 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,741 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,741 INFO     
2009-03-08 20:50:20,742 INFO     Current default timezone: 'Etc/UTC'
2009-03-08 20:50:20,742 INFO     Local time is now:      Sun Mar  8 22:50:18 UTC 2009.
2009-03-08 20:50:20,743 INFO     Universal Time is now:  Sun Mar  8 22:50:18 UTC 2009.
2009-03-08 20:50:20,743 INFO     Run 'dpkg-reconfigure tzdata' if you wish to change it.
2009-03-08 20:50:20,743 INFO     
2009-03-08 20:50:20,744 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:20,744 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-03-08 20:50:21,945 INFO     Updating certificates in /etc/ssl/certs....done.
2009-03-08 20:50:21,946 INFO     Running hooks in /etc/ca-certificates/update.d....done.
2009-03-08 20:50:22,425 INFO     grep: /proc/self/status: No such file or directory
2009-03-08 20:50:22,789 INFO     update-initramfs: deferring update (trigger activated)
2009-03-08 20:50:25,351 INFO     Copying to disk images
2009-03-08 20:50:36,188 INFO     Installing bootloader
2009-03-08 20:50:36,515 INFO     Unmounting target filesystem
2009-03-08 20:50:36,761 INFO     Converting /tmp/vmbuilderHE8-8J/disk0.img to qcow2, format /var/vm/vmtest1.example.com/disk0.qcow2
2009-03-08 20:51:00,233 INFO     Cleaning up

```

---

### Post by el_baby on 2009-03-10
bump?

---

### Post by el_baby on 2009-03-13
Well,

finally [moski](http://ubuntuforums.org/member.php?u=490525) from [ubuntu-ar](http://ubuntu-ar.org/) hinted me to remotely try **virt-viewer** which worked nicely (although very slowly)...

Now I have to check why the network's not working, but that's another thread...

---

