---
title: "[Ubuntu 20.04 server LTS] Low Disk Space on &quot;Boot&quot;"
date: 2023-05-08
forum: Server Platforms
---

### Post by johndid on 2023-05-08
Hi,

I have Ubuntu 20.04 server LTS running on a laptop. Today I ran it and got this message at the end of the boot:

[https://images2.imgbox.com/38/04/AIfphQZE_o.jpg](https://images2.imgbox.com/38/04/AIfphQZE_o.jpg)


I took a look at the Storage windows in cokcpit and saw this:

[https://images2.imgbox.com/f0/01/bG7ZUSef_o.jpg](https://images2.imgbox.com/f0/01/bG7ZUSef_o.jpg)

911/973 MiB, so it seems that the partition is almost full.

Do I need to free some space necessarily? If in case, How can I do it safely, I mean, without messing it up somehow? 

Thanks

---

### Post by TheFu on 2023-05-08
> **johndid said:**
> Hi,

I have Ubuntu 20.04 server LTS running on a laptop. Today I ran it and got this message at the end of the boot:

I took a look at the Storage windows in cokcpit and saw this:

911/973 MiB, so it seems that the partition is almost full.

Do I need to free some space necessarily? If in case, How can I do it safely, I mean, without messing it up somehow? 

Thanks

a) please don't post huge images when text from a command will do it.  For disk space, use **df -Th /boot** to show the issue.

b) Yes, you should delete older kernels and their dependencies.  **Synaptic** is often the easiest tool for GUI-centric users to do this.  Until you free some storage, no new kernels will be installed.  A few weeks ago, there was a really bad remote access kernel bug, so this isn't something to be delayed. Fix it ASAP.  There are lots of CLI methods for doing this too.

There should be enough room for 3 kernels - 2 old and 1 currently used in /boot.

---

### Post by LHammonds on 2023-05-08
Having a 1GB boot partition should be plenty of space for normal use.  However, normally the OS keeps 1 current kernel and 2 old kernels.   Since it is almost full, I suspect the automated purge system was not working...meaning you have a LOT of old kernels in there.  Or something was writing files to /boot that shouldn't be there (but I suspect the former).

```
apt list --installed | grep linux-image
```

This will show all the kernels installed.  Typically, you are running the latest version but since you have a full partition, its possible the latest did not install properly and you could be running on an older kernel.

To see which kernel you are booting from (so you know which kernel to NOT remove), type this command:

```
uname -r
```

If you can, try the automated method of cleaning up the boot drive:

```
sudo apt autoremove --purge
```

If that fails to work, find an old (and not currently active) kernel from the 1st command above.  For example, if "linux-image-5.15.0-1-generic" is installed and not the currently active kernel, then try to purge it with a command like this:

```
sudo apt purge linux-image-5.15.0-1-generic
```

If the space issues continue to prevent these commands from working, then you will have to resort to manually deleting the kernel files until the above commands begin to work because enough space has been cleared for the operation to work.

But keep track of the kernels you manually remove and be sure to issue the "apt purge" command for that kernel to get any other files that were installed with it that your manual removal might have missed.

I hope I am not giving incorrect commands / advice.  It's been a hot minute since I've been on a Linux server.

LHammonds

---

### Post by johndid on 2023-05-09
> **LHammonds said:**
> 
```
sudo apt purge linux-image-5.15.0-1-generic
```


LHammonds

ok

I first ran:


```

df -Th /boot

Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4  974M  912M     0 100% /boot

```


then:

```

apt list --installed | grep linux-image

linux-image-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-image-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-image-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-image-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-image-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-image-5.4.0-144-generic/focal-updates,focal-security,now 5.4.0-144.161 amd64 [installed,auto-removable]
linux-image-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-image-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-image-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-image-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed,automatic]


```



```
uname -r

5.4.0-148-generic
```



```

sudo apt autoremove --purge

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  docker-scan-plugin* libfwupdplugin1* libxmlb1* linux-headers-5.4.0-144* linux-headers-5.4.0-144-generic*
  linux-image-5.4.0-144-generic* linux-modules-5.4.0-144-generic* linux-modules-extra-5.4.0-144-generic* linux-tools-5.4.0-144*
  linux-tools-5.4.0-144-generic*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
After this operation, 419 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 406054 files and directories currently installed.)
Removing docker-scan-plugin (0.23.0~ubuntu-focal) ...
Removing libfwupdplugin1:amd64 (1.5.11-0ubuntu1~20.04.2) ...
Removing libxmlb1:amd64 (0.1.15-2ubuntu1~20.04.1) ...
Removing linux-headers-5.4.0-144-generic (5.4.0-144.161) ...
Removing linux-headers-5.4.0-144 (5.4.0-144.161) ...
Removing linux-modules-extra-5.4.0-144-generic (5.4.0-144.161) ...
Removing linux-image-5.4.0-144-generic (5.4.0-144.161) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-144-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-148-generic
Found initrd image: /boot/initrd.img-5.4.0-148-generic
Found linux image: /boot/vmlinuz-5.4.0-146-generic
Found initrd image: /boot/initrd.img-5.4.0-146-generic
Found linux image: /boot/vmlinuz-5.4.0-139-generic
Found initrd image: /boot/initrd.img-5.4.0-139-generic
Found linux image: /boot/vmlinuz-5.4.0-136-generic
Found initrd image: /boot/initrd.img-5.4.0-136-generic
Found linux image: /boot/vmlinuz-5.4.0-132-generic
Found initrd image: /boot/initrd.img-5.4.0-132-generic
Found linux image: /boot/vmlinuz-5.4.0-131-generic
Found initrd image: /boot/initrd.img-5.4.0-131-generic
Found linux image: /boot/vmlinuz-5.4.0-109-generic
Found initrd image: /boot/initrd.img-5.4.0-109-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
done
Removing linux-modules-5.4.0-144-generic (5.4.0-144.161) ...
Removing linux-tools-5.4.0-144-generic (5.4.0-144.161) ...
Removing linux-tools-5.4.0-144 (5.4.0-144.161) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
(Reading database ... 369586 files and directories currently installed.)
Purging configuration files for linux-modules-5.4.0-144-generic (5.4.0-144.161) ...
dpkg: warning: while removing linux-modules-5.4.0-144-generic, directory '/lib/modules/5.4.0-144-generic' not empty so not removed
Purging configuration files for linux-image-5.4.0-144-generic (5.4.0-144.161) ...
Purging configuration files for linux-modules-extra-5.4.0-144-generic (5.4.0-144.161) ...



```



again:

```

apt list --installed | grep linux-image

linux-image-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-image-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-image-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-image-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-image-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-image-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-image-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-image-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-image-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed,automatic]


```


Since the ***sudo apt autoremove --purge ***didn't seem it was doing a great job, I started to delete them one by one manually, and 
the last purge command I ran was:

```
 sudo apt purge linux-image-5.4.0-139-generic

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.4.0-139-generic* linux-modules-extra-5.4.0-139-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 215 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 348143 files and directories currently installed.)
Removing linux-modules-extra-5.4.0-139-generic (5.4.0-139.156) ...
Removing linux-image-5.4.0-139-generic (5.4.0-139.156) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-139-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-148-generic
Found initrd image: /boot/initrd.img-5.4.0-148-generic
Found linux image: /boot/vmlinuz-5.4.0-146-generic
Found initrd image: /boot/initrd.img-5.4.0-146-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
done
(Reading database ... 342783 files and directories currently installed.)
Purging configuration files for linux-modules-extra-5.4.0-139-generic (5.4.0-139.156) ...
Purging configuration files for linux-image-5.4.0-139-generic (5.4.0-139.156) ...
***rmdir: failed to remove '/lib/modules/5.4.0-139-generic': Directory not empty***


```

I ended up with this situation:



```

apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-image-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-image-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-image-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed,automatic]


df -Th /boot
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4  974M  333M  574M  37% /boot


```
Much better, I guess.

Anyway, what is this message about?

[I][B]rmdir: failed to remove '/lib/modules/5.4.0-139-generic': Directory not empty

[/B][/I]I got it for every image removed via the purge command.

Do I need to do something else now?

Thanks

---

### Post by ajgreeny on 2023-05-09
Looks as if all is OK now and all you need to do to avoid this situation again is to regularly run 
***sudo apt autoremove --purge***
particularly after every new kernel is installed.

I see that same message about the modules directory not being empty and have never bothered to do anything about it, nor have I investiged further to see what is in there but I will do so later and report back.

---

### Post by johndid on 2023-05-09
> **ajgreeny said:**
> Looks as if all is OK now and all you need to do to avoid this situation again is to regularly run 
***sudo apt autoremove --purge***
particularly after every new kernel is installed.

I see that same message about the modules directory not being empty and have never bothered to do anything about it, nor have I investiged further to see what is in there but I will do so later and report back.

Ok, thanks


ps: I have another ubuntu 20.04 server LTS running as a VM on VMware workstation, it hasn't gone through the same issue, but it has not such a **/boot** partition.

```

 df -Th /boot
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4   14G  9.2G  3.9G  71% /

uname -r
5.4.0-148-generic


apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-image-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed,automatic]
linux-image-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed]


 sudo apt autoremove --purge

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It is already "clean" apparently. Strange

---

### Post by MAFoElffen on 2023-05-09
Just FYI... 

When I install kernels, I notice it is not just one package, such as this:
```

 amd64/linux-headers-6.4.0-060400rc1-generic_6.4.0-060400rc1.202305072134_amd64.deb
amd64/linux-headers-6.4.0-060400rc1_6.4.0-060400rc1.202305072134_all.deb
amd64/linux-image-unsigned-6.4.0-060400rc1-generic_6.4.0-060400rc1.202305072134_amd64.deb
amd64/linux-modules-6.4.0-060400rc1-generic_6.4.0-060400rc1.202305072134_amd64.deb

```
Which has packages installed as
```

linux-headers-6.4.0-060400rc1
linux-headers-6.4.0-060400rc1
linux-image-unsigned-6.4.0-060400rc1-generic
linux-modules-6.4.0-060400rc1-generic

```
When I uninstall kernels, I search for any other packages that might be installed related to that kernel (not just linux-image*), such as headers and modules, so that I can uninstall them also.

Like this:
```

kversion="6.4.0"

apt list linux-*$kversion* --installed

```
...which will also come up with associated packages that were installed as dependencies by nVidia, as part of their dkms.

That way I can uninstall those other related packages. That might be "just me"... I'm wired like that. I like to make sure that I don't create and leave orphaned packages. At least, that makes sense to me. Right?

You might want to check for those other packages, and see if you need to remove them... Just a thought.

---

### Post by johndid on 2023-05-10
> **MAFoElffen said:**
> Just FYI... 
```

kversion="6.4.0"
apt list linux-*$kversion* --installed

```




```


linux-base/focal-updates,now 4.5ubuntu3.7 all [installed,automatic]
linux-firmware/focal-updates,now 1.187.38 all [installed,automatic]
linux-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed]
linux-headers-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-headers-5.4.0-109/focal-updates,focal-security,now 5.4.0-109.123 all [installed]
linux-headers-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-headers-5.4.0-131/focal-updates,focal-security,now 5.4.0-131.147 all [installed]
linux-headers-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-headers-5.4.0-132/focal-updates,focal-security,now 5.4.0-132.148 all [installed]
linux-headers-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-headers-5.4.0-136/focal-updates,focal-security,now 5.4.0-136.153 all [installed]
linux-headers-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-headers-5.4.0-139/focal-updates,focal-security,now 5.4.0-139.156 all [installed]
linux-headers-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-headers-5.4.0-146/focal-updates,focal-security,now 5.4.0-146.163 all [installed,automatic]
linux-headers-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-headers-5.4.0-148/focal-updates,focal-security,now 5.4.0-148.165 all [installed]
linux-headers-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-headers-5.4.0-96/focal-updates,focal-security,now 5.4.0-96.109 all [installed]
linux-headers-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed,automatic]
linux-image-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-image-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-image-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-image-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed,automatic]
linux-libc-dev/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed,automatic]
linux-modules-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-modules-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-modules-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-modules-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-modules-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-modules-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-modules-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-modules-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-modules-extra-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-modules-extra-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-modules-extra-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-tools-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-tools-5.4.0-109/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-tools-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-tools-5.4.0-131/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-tools-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-tools-5.4.0-132/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-tools-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-tools-5.4.0-136/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-tools-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-tools-5.4.0-139/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-tools-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-tools-5.4.0-146/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-tools-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-tools-5.4.0-148/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-tools-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-tools-5.4.0-96/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-tools-common/focal-updates,focal-security,now 5.4.0-148.165 all [installed,automatic]
linux-tools-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed]



```

and 
```

** dpkg --list | egrep 'linux-image|linux-headers'**


ii  linux-headers-5.4.0-109               5.4.0-109.123                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-109-generic       5.4.0-109.123                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-131               5.4.0-131.147                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-131-generic       5.4.0-131.147                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-132               5.4.0-132.148                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-132-generic       5.4.0-132.148                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-136               5.4.0-136.153                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-136-generic       5.4.0-136.153                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-139               5.4.0-139.156                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-139-generic       5.4.0-139.156                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-146               5.4.0-146.163                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-146-generic       5.4.0-146.163                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-148               5.4.0-148.165                     all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-148-generic       5.4.0-148.165                     amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-96                5.4.0-96.109                      all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-96-generic        5.4.0-96.109                      amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                 5.4.0.148.146                     amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-146-generic         5.4.0-146.163                     amd64        Signed kernel image generic
ii  linux-image-5.4.0-148-generic         5.4.0-148.165                     amd64        Signed kernel image generic
ii  linux-image-5.4.0-96-generic          5.4.0-96.109                      amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.148.146                     amd64        Generic Linux kernel image



```

---

### Post by MAFoElffen on 2023-05-10
So there are currently 3 active linux-images active:
```

linux-image-5.4.0-146-generic
linux-image-5.4.0-148-generic
linux-image-5.4.0-96-generic

```
But... many other versions of the header packages are still left there. Those are not needed anymore and can be safely removed. They are presently orphaned, and just taking up room. (Not in the /boot partition, but in the root system partition.)

---

### Post by johndid on 2023-05-10
> **MAFoElffen said:**
> So there are currently 3 active linux-images active:
```

linux-image-5.4.0-146-generic
linux-image-5.4.0-148-generic
linux-image-5.4.0-96-generic

```


I also deleted the 5.4.0-96-generic.

What are the exact commands to safely delete old headers, modules, and tools?
I found this one for the headers:
[B]sudo apt remove --purge linux-headers-[version]


Thanks
[/B]

---

### Post by MAFoElffen on 2023-05-10
Yes. Exactly. I didn't see any modules there but I didn't see the filters you used for your output... You can check for them with
```

apt list linux-modules* --installed

```

---

### Post by johndid on 2023-05-11
> **MAFoElffen said:**
> Yes. Exactly. I didn't see any modules there but I didn't see the filters you used for your output... You can check for them with
```

apt list linux-modules* --installed

```

Ok I deleted the old headers.
Here is the old modules and tools:

```

**apt list linux-modules* --installed**

Listing... Done
linux-modules-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-modules-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-modules-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-modules-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-modules-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-modules-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-modules-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-modules-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-modules-extra-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-modules-extra-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]


**apt list linux-tools* --installed**
Listing... Done
linux-tools-5.4.0-109-generic/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-tools-5.4.0-109/focal-updates,focal-security,now 5.4.0-109.123 amd64 [installed]
linux-tools-5.4.0-131-generic/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-tools-5.4.0-131/focal-updates,focal-security,now 5.4.0-131.147 amd64 [installed]
linux-tools-5.4.0-132-generic/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-tools-5.4.0-132/focal-updates,focal-security,now 5.4.0-132.148 amd64 [installed]
linux-tools-5.4.0-136-generic/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-tools-5.4.0-136/focal-updates,focal-security,now 5.4.0-136.153 amd64 [installed]
linux-tools-5.4.0-139-generic/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-tools-5.4.0-139/focal-updates,focal-security,now 5.4.0-139.156 amd64 [installed]
linux-tools-5.4.0-146-generic/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-tools-5.4.0-146/focal-updates,focal-security,now 5.4.0-146.163 amd64 [installed,automatic]
linux-tools-5.4.0-148-generic/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-tools-5.4.0-148/focal-updates,focal-security,now 5.4.0-148.165 amd64 [installed]
linux-tools-5.4.0-96-generic/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-tools-5.4.0-96/focal-updates,focal-security,now 5.4.0-96.109 amd64 [installed]
linux-tools-common/focal-updates,focal-security,now 5.4.0-148.165 all [installed,automatic]
linux-tools-generic/focal-updates,focal-security,now 5.4.0.148.146 amd64 [installed]


```


I am supposed to run these two commands to delete them, I guess

[B]sudo apt remove --purge linux-modules-[version]

[/B]and

[B]sudo apt remove --purge linux-tools-[version]


[/B]Thanks

---

### Post by MAFoElffen on 2023-05-11
Yes...

---

### Post by ajgreeny on 2023-05-11
When I remove an old kernel version j do it myself manually whenever a new kernel version appears, keeping just the two most recent. 

For example to remove the version you spoke about last I would use command ```
sudo apt purge *5.4.0-96*
``` having found all current versions still on my system with command```
ls /boot |grep vmlinuz
```
The ability of apt to use the * wildcard means that the command will immediately list any kernel related packages of the same version, ie, headers, modules, tools, etc, and purge them with the kernel.

---

### Post by johndid on 2023-05-12
> **ajgreeny said:**
> When I remove an old kernel version j do it myself manually whenever a new kernel version appears, keeping just the two most recent. 

For example to remove the version you spoke about last I would use command ```
sudo apt purge *5.4.0-96*
``` having found all current versions still on my system with command```
ls /boot |grep vmlinuz
```
The ability of apt to use the * wildcard means that the command will immediately list any kernel related packages of the same version, ie, headers, modules, tools, etc, and purge them with the kernel.


Very helpful. Thanks

---

### Post by TheFu on 2023-05-12
If you use **synaptic**, you can select groups of kernel headers, modules and kernels to be removed easily.
I'm good with using CLI tools and use them myself, but synaptic's GUI really does make this stuff easier.

---

### Post by ajgreeny on 2023-05-12
> **TheFu said:**
> If you use **synaptic**, you can select groups of kernel headers, modules and kernels to be removed easily.
I'm good with using CLI tools and use them myself, but synaptic's GUI really does make this stuff easier.
A very good point, and worth making.

In the past, before I became so command line oriented, synaptic was what I used for everything related to package management, ie installation uninstallation and updating; all done using synaptic.  When I first started using Ubuntu it was, I think, the only GUI package management application available, possibly not even a GUI specifically for system updating but I honestly can't remember as it was 18 years ago with Ubuntu 5.04.  I now seldom see a need for the GUI for such things except maybe package searching which I admit is easier with synaptic than cli.

---

### Post by MAFoElffen on 2023-05-12
LOL -- I can remember that I was sooo upset when Ubuntu decided "not" to include Synaptic as a default installed application on a Desktop install. 

To this day, synaptic is one of the the first applications I install on a fresh install.

---

