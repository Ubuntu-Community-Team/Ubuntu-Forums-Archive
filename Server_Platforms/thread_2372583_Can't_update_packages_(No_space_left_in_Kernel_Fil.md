---
title: "Can't update packages (No space left in Kernel Files)"
date: 2017-09-26
forum: Server Platforms
---

### Post by mahtaran on 2017-09-26
I've got a problem.

After a recent update, my kernel images folder is full. However, the kernel image from the new version is (Or so I think) corrupted. Basically, if I reboot, it won't boot (*[COLOR=#000000][FONT=&amp]kernel panic-not syncing: VFS: unable to mount root fs on [/FONT][/COLOR]*[COLOR=#000000][FONT=&amp]*unknown block**(0,0)*)[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR] 
The log when doing sudo apt-get upgrade -f:
```
mahtaran@amuzilserver:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-4.4.0-91-generic linux-image-4.4.0-92-generic
The following packages have been kept back:
  libegl1-mesa libgbm1 libgl1-mesa-dri libmirclient9 libwayland-egl1-mesa
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
11 not fully installed or removed.
Need to get 0 B/79.8 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 483562 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-92-generic (4.4.0-92.115) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-92-gene                                                                                                                               ric_4.4.0-92.115_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-92-generic' to '/boot/vmli                                                                                                                               nuz-4.4.0-92-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dp                                                                                                                               kg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-92-generic /boot                                                                                                                               /vmlinuz-4.4.0-92-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-92-generic /boot/                                                                                                                               vmlinuz-4.4.0-92-generic
Preparing to unpack .../linux-image-4.4.0-91-generic_4.4.0-91.114_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-91-generic (4.4.0-91.114) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-91-generic_4.4.0-91.114_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-91-generic' to '/boot/vmlinuz-4.4.0-91-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-91-generic /boot/vmlinuz-4.4.0-91-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-91-generic /boot/vmlinuz-4.4.0-91-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-92-generic_4.4.0-92.115_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-91-generic_4.4.0-91.114_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried a lot, but I simply can't fix it.

Any ideas? If you need more information, I'll provide it ASAP.

---

### Post by darkod on 2017-09-26
Start with posting output of:
```
df -h
uname -r
ls /boot/
```

---

### Post by Bashing-om on 2017-09-26
Hello mahtaran; Welcome to the forum .

> 
'/boot/vmlinuz-4.4.0-91-generic.dpkg-new': failed to write (No space left on device)


Yes you do read aright . Need to get some space - somehow.
To do that we need to get to a terminal - somehow :)

So what results attempting to boot a older kernel from grub's boot menu ?
If you are able to boot up an older kernel.: what results when attempting terminal command:
```

sudo apt autoremove

```

Autoremove failing ( lack of operational overhead ) then we do " something else" to get that space .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by darkod on 2017-09-26
autoremove should surely fail on a full disk, no? At least for me it has never worked when trying it in similar situation...

Best way out of this is manually deleting few (older) kernel files and apt-get can pick it up from there. Without making it too complicated like other similar threads I've seen. However, I asked for the above output not to start deleting files blindly.

---

### Post by mahtaran on 2017-09-26
Thank you all for the quick replies. The output:
```
mahtaran@amuzilserver:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted onudev                               5.8G     0  5.8G   0% /dev
tmpfs                              1.2G  114M  1.1G  10% /run
/dev/mapper/amuzilserver--vg-root  455G   28G  404G   7% /
tmpfs                              5.9G  4.0K  5.9G   1% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/sda1                          472M  466M     0 100% /boot
tmpfs                              1.2G     0  1.2G   0% /run/user/1000
/home/mahtaran/.Private            455G   28G  404G   7% /home/mahtaran
mahtaran@amuzilserver:~$ uname -r
4.4.0-83-generic
mahtaran@amuzilserver:~$ ls /boot/
abi-4.4.0-64-generic  config-4.4.0-64-generic  grub                         System.map-4.4.0-64-generic  vmlinuz-4.4.0-64-generic
abi-4.4.0-66-generic  config-4.4.0-66-generic  initrd.img-4.4.0-64-generic  System.map-4.4.0-66-generic  vmlinuz-4.4.0-66-generic
abi-4.4.0-70-generic  config-4.4.0-70-generic  initrd.img-4.4.0-66-generic  System.map-4.4.0-70-generic  vmlinuz-4.4.0-70-generic
abi-4.4.0-71-generic  config-4.4.0-71-generic  initrd.img-4.4.0-70-generic  System.map-4.4.0-71-generic  vmlinuz-4.4.0-71-generic
abi-4.4.0-72-generic  config-4.4.0-72-generic  initrd.img-4.4.0-71-generic  System.map-4.4.0-72-generic  vmlinuz-4.4.0-72-generic
abi-4.4.0-75-generic  config-4.4.0-75-generic  initrd.img-4.4.0-72-generic  System.map-4.4.0-75-generic  vmlinuz-4.4.0-75-generic
abi-4.4.0-78-generic  config-4.4.0-78-generic  initrd.img-4.4.0-75-generic  System.map-4.4.0-78-generic  vmlinuz-4.4.0-78-generic
abi-4.4.0-79-generic  config-4.4.0-79-generic  initrd.img-4.4.0-78-generic  System.map-4.4.0-79-generic  vmlinuz-4.4.0-79-generic
abi-4.4.0-83-generic  config-4.4.0-83-generic  initrd.img-4.4.0-79-generic  System.map-4.4.0-83-generic  vmlinuz-4.4.0-83-generic
abi-4.4.0-87-generic  config-4.4.0-87-generic  initrd.img-4.4.0-83-generic  System.map-4.4.0-87-generic  vmlinuz-4.4.0-87-generic
abi-4.4.0-89-generic  config-4.4.0-89-generic  lost+found                   System.map-4.4.0-89-generic  vmlinuz-4.4.0-89-generic
```

---

### Post by ian-weisser on 2017-09-26
> **mahtaran said:**
> I've tried a lot, but I simply can't fix it.

This has been asked (and answered) many, many times in the help forums and the wiki, and the fix is quite straightforward.

Use dpkg to uninstall one or two older, unused kernels. This will provide apt the headroom it needs to do the rest automatically.
Pro tip: DO NOT use 'rm' to clear space. You will simply make the apt problem worse.

Going forward, you must maintain your system a few times each year. Usually running apt autoremove is all you need to maintain.

---

### Post by mahtaran on 2017-09-26
I tried, but...
```
mahtaran@amuzilserver:~$ sudo dpkg --remove linux-image-4.4.0-64-generic
[sudo] password for mahtaran: 
dpkg: dependency problems prevent removal of linux-image-4.4.0-64-generic:
 linux-image-extra-4.4.0-64-generic depends on linux-image-4.4.0-64-generic.


dpkg: error processing package linux-image-4.4.0-64-generic (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-64-generic
mahtaran@amuzilserver:~$ sudo dpkg --remove linux-image-extra-4.4.0-64-generic 
(Reading database ... 483562 files and directories currently installed.)
Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-64-generic
```

---

### Post by ian-weisser on 2017-09-26
So you need to uninstall more than one old kernel package at a time. Not surprising.
Warning: DO NOT uninstall your currently running kernel. Doing so will render your system unbootable, and is rather a pain to fix.

dpkg can remove multiple packages in one command.
```
sudo dpkg --remove package1 package2
```

dpkg can remove multiple versions of multiple packages in one command.
```
sudo dpkg --remove package1.1.{43,44,45,46).x package2.1.{43,44,45,46}.y
```

Use those tricks to uninstall multiple kernel packages at once, providing the space that the system needs to update grub and generate the new initrd.img
DO NOT uninstall your currently-running kernel!

---

### Post by mahtaran on 2017-09-27
Oh wow, I really thought I already tried that!

I used [Remove Old Kernels via DPKG]("http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/"). Thanks all for your input!

---

### Post by LHammonds on 2017-09-29
That's a lot of old kernels.  Once everything is in working order, keep it that way by doing "**apt-get autoremove**" and "**apt-get autoclean**" once in a while.  Autoremove should clear out all the old kernels and headers.  The most recent version of the OS tends to keep the current kernel and 1 older kernel and removes everything older.  In the past, I have seen it remove all kernels other than current which is why I never let it do it by itself.  I always liked having 1 backup kernel.  I used manually remove old kernels and headers once a month with commands similar to "**apt-get remove linux-image-3.2.0-generic**" which makes space in /boot and "**apt-get purge linux-headers-3.2.0**" which makes space in /usr/src

LHammonds

---

