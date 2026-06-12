---
title: "Removing OLD AND New Kernels?"
date: 2016-02-23
forum: Server Platforms
---

### Post by scott.bouch on 2016-02-23
Hi All,

My Ubuntu 14.04 webserver has an issue where It will only boot successfully with kernel 3.13.0-43-generic. I have a few newer and older kernels available in Grub, all of which hang at various points during boot.

*The server hardware is a second hand DELL CS24-SC. They are a bit of an oddball server, as they were custom built (legend has it for Facebook) and as such, not much information exists on them.*

I last performed a **dist-upgrade** and had new kernels some time ago, so can't speak for more modern kernel updates, as there may well be a newer one that happens to work with my hardware (perhaps?).

But my issue is, Grub selects the latest installed kernel, which never works and leaves the boot sequence hanging at some random point (depending on the kernel version used). I'm running this server headless in a remote location, and I don't want to have to plug in a monitor and keyboard every time I power it up, just to select a specific kernel from Grub.


[LIST]
[*]How can I remove all kernels, newer _**and**_ older than 3.13.0-43-generic? Most guides for removing kernels assume you're happy with the latest kernel and wish to remove all older versions, clearly this is not the case for me!
[/LIST]

Not knowing too much about kernels, are there any security risks / vulnerabilities with using older versions, as this is a web server? Am I missing out on anything groovy by staying with something historic? Is it good practice to stick with an older kernel when the hardware is a bit old?

Many thanks, Scott.

---

### Post by darkod on 2016-02-23
The kernel is basically a package and you can remove it as any other, directly.

You can get full list of installed kernels with something like:
```
dpkg --list | grep linux-image
```

At the top you will have the kernels in format linux-image-3.13.0-XX-generic (as an example). You can remove any with:
```
sudo apt-get purge linux-image-3.13.0-XX-generic
```

Of course, replace the XX with the one you want to remove. Go one by one and remove all you want. Just be careful not to leave your system unbootable. :)

On another thought, have you tried if 3.19 still has issues with your HW? If you started with 14.04 and 3.13 later it doesn't pass automatically to 3.19 even though Canonical makes it available (for example an install with the current 14.04.3 ISO will have 3.19 kernel, at least I think so).

Because LTS is supported 5 years and new kernels come along, installing this newer kernels is called LTS Enablement Stacks. To add 3.19 to your system you can try:
```
sudo apt-get install --install-recommends linux-generic-lts-wily
```

When I did that the current ubuntu was vivid so I used vivid instead of wily. I see they modified the instructions now: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If new kernels/stacks work good, your problem goes away, no? Of course, you can still select to use only specific 3.13 kernel.

PS. Actually when I did that with vivid it installed kernel 3.19 because that is the one from vivid I believe. If you use wily as per those instructions it might even install a newer one, like 4.X (I don't remember the exact kernel in wily because I don't use non-LTS releases). Give it a shot, nothing to lose. You will still have your 3.13.0-43.

---

### Post by scott.bouch on 2016-02-23
Hi Darko,

Many thanks for your advice, I'm just now giving it a go and will update when done.

Cheers, Scott.

---

### Post by scott.bouch on 2016-02-23
Hi, I've ran into a slight issue... I can't purge the unwanted kernels.. I started with the oldest, and also tried 3.13.0-37, same result.

Just typed this out, copied from the server screen:

*sudo apt-get purge linux-image-3.13.0-32-generic*Reading package lists... Done
Building dependency tree
Reading state information...  Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
linux-image-extra-3.13.0.32-generic : Depends: linux-image-3.13.0-32-generic but it is not going to be installed
linux-image-extra-3.13.0.32-generic : Depends: linux-image-3.13.0-32-generic but it is not going to be installed
linux-image-generic : Depends: linux-image-3.13.0-46-generic but it is not going to be installed
E: Unmet dependencies. try '-apt-get -f install' with no packages (or specify a solution).

I tried the advice [COLOR=#000000]**apt-get -f install it gave **[/COLOR]loads of 404 not founds, and Failed to fetch.. it can't find the ip addresses. then tried the purge again but it didn't help... 

Same happens with **apt-get remove**...

So,I thought I'd run this by you before I carry on blindly and turn my server into a brick!

For info, I have 3.13.0-32, 37, 39, 40, 41, 43, 44, and 45 installed, of which only 43 works.

Cheers, Scott.

---

### Post by darkod on 2016-02-23
As it says, it has some broken dependanciaes so apt is refusing to continue. Usually it's safe to do the recommended:
```
sudo apt-get install -f
```

That will try to fix them. I have used it and in my case it didn't break anything. You can give it a shot, otherwise apt will never continue to work.

---

### Post by scott.bouch on 2016-02-23
I just tried **[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install -f[/FONT][/COLOR]**, and it failed....

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-41 linux-headers-3.13.0-41-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-37-generic
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-41-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-39-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-41-generic
  linux-image-extra-3.13.0-44-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic linux-headers-3.13.0-57 linux-headers-3.13.0-57-generic
  linux-headers-generic linux-image-3.13.0-46-generic
  linux-image-3.13.0-57-generic linux-image-extra-3.13.0-57-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-headers-3.13.0-57 linux-headers-3.13.0-57-generic
  linux-image-3.13.0-46-generic linux-image-3.13.0-57-generic
  linux-image-extra-3.13.0-57-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 5 to newly install, 0 to remove and 302 not to upgrade.
13 not fully installed or removed.
Need to get 6,284 B/76.5 MB of archives.
After this operation, 313 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.57.64
  404  Not Found [IP: 91.189.88.152 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-generic amd64 3.13.0.57.64
  404  Not Found [IP: 91.189.88.152 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-generic amd64 3.13.0.57.64
  404  Not Found [IP: 91.189.88.152 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic amd64 3.13.0.57.64
  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.57.64_amd64.deb  404  Not Found [IP: 91.189.88.152 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.57.64_amd64.deb  404  Not Found [IP: 91.189.88.152 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.57.64_amd64.deb  404  Not Found [IP: 91.189.88.152 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

This time using SSH to save re-typing!

The computer is on the network ok, as I can SSH to it.

---

### Post by scott.bouch on 2016-02-23
I'm an idiot - I've just done **sudo apt-get update** and now **apt-get install -f** works... but **apt-get purge** still has issues...

```
$ sudo apt-get purge linux-image-3.13.0-32-genericReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-32-generic : Depends: linux-image-3.13.0-32-generic but it is not going to be installed
 linux-image-extra-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic but it is not going to be installed
 linux-image-extra-3.13.0-79-generic : Depends: linux-image-3.13.0-79-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-79-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by darkod on 2016-02-23
OK. So did you run install -f? This last message also suggests to run it. Try it again...

First you need to repair the dependencies, only after that to try the purge.

---

### Post by scott.bouch on 2016-02-24
Yes, I  did, in reading it's results I found this (extract from results):

```
The following packages were automatically installed and are no longer required:  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-41 linux-headers-3.13.0-41-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-37-generic
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-41-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-39-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-41-generic
  linux-image-extra-3.13.0-44-generic linux-image-extra-3.13.0-46-generic
Use '**apt-get autoremove**' to remove them.



```


so, why not try autoremove...

```
$ **sudo apt-get autoremove**Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic but it is not installed
 linux-image-extra-3.13.0-79-generic : Depends: linux-image-3.13.0-79-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-79-generic but it is not installed
**E: Unmet dependencies. Try using -f.**
```


So again i tried -f install... have a look through the results, I've highlighted some points of interest:

```
$ **sudo apt-get -f install**Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
**The following packages were automatically installed and are no longer required:**
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-41 linux-headers-3.13.0-41-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-37-generic
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-41-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-39-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-41-generic
  linux-image-extra-3.13.0-44-generic linux-image-extra-3.13.0-46-generic
**Use 'apt-get autoremove' to remove them.**
The following extra packages will be installed:
  linux-image-3.13.0-46-generic linux-image-3.13.0-79-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-46-generic linux-image-3.13.0-79-generic
0 to upgrade, 2 to newly install, 0 to remove and 436 not to upgrade.
16 not fully installed or removed.
Need to get 0 B/30.3 MB of archives.
After this operation, 84.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 399022 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-79-generic_3.13.0-79.123_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-79-generic (3.13.0-79.123) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-79-generic_3.13.0-79.123_amd64.deb (--unpack):
 **cannot copy extracted data **for './boot/vmlinuz-3.13.0-79-generic' to '/boot/vmlinuz-3.13.0-79-generic.dpkg-new': failed to write **(No space left on device)**
**No apport report written because the error message indicates a disk full error**
**                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)**
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Preparing to unpack .../linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-46-generic (3.13.0-46.79) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-46-generic' to '/boot/vmlinuz-3.13.0-46-generic.dpkg-new': failed to write **(No space left on device)**
**No apport report written because the error message indicates a disk full error**
**                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)**
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
**Errors were encountered while processing:**
 /var/cache/apt/archives/linux-image-3.13.0-79-generic_3.13.0-79.123_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb
**E: Sub-process /usr/bin/dpkg returned an error code (1)**



```
 

Interestingly this identified **No space left on device.** I assume the device is the boot partition, from which I'm struggling to remove unwanted kernels from....

Can I manually browse to and remove unwanted kernels? **sudo rm...** perhaps? or will this screw things up?

This is the contents of /boot:

```
/boot$[B] ls
[/B]abi-3.13.0-32-generic  abi-3.13.0-44-generic     config-3.13.0-41-generic      initrd.img-3.13.0-37-generic  memtest86+.bin           System.map-3.13.0-40-generic  vmlinuz-3.13.0-37-generic  vmlinuz-3.13.0-45-generic
abi-3.13.0-37-generic  abi-3.13.0-45-generic     config-3.13.0-43-generic      initrd.img-3.13.0-39-generic  memtest86+.elf           System.map-3.13.0-41-generic  vmlinuz-3.13.0-39-generic
abi-3.13.0-39-generic  config-3.13.0-32-generic  config-3.13.0-44-generic      initrd.img-3.13.0-40-generic  memtest86+_multiboot.bin       System.map-3.13.0-43-generic  vmlinuz-3.13.0-40-generic
abi-3.13.0-40-generic  config-3.13.0-37-generic  config-3.13.0-45-generic      initrd.img-3.13.0-41-generic  System.map-3.13.0-32-generic  System.map-3.13.0-44-generic  vmlinuz-3.13.0-41-generic
abi-3.13.0-41-generic  config-3.13.0-39-generic  grub                   initrd.img-3.13.0-43-generic  System.map-3.13.0-37-generic  System.map-3.13.0-45-generic  vmlinuz-3.13.0-43-generic
abi-3.13.0-43-generic  config-3.13.0-40-generic  initrd.img-3.13.0-32-generic  lost+found             System.map-3.13.0-39-generic  vmlinuz-3.13.0-32-generic     vmlinuz-3.13.0-44-generic



```

I'm reluctant to completely reinstall Ubuntu as I've configured fstab, Apache, Zoneminder etc... and it would be a lot of work to re-do. I can't remember the locations of all the config files either as it was about 2 years ago when I got it running.

Thanks, Scott.

---

### Post by darkod on 2016-02-24
That would have been my next question, free space on / or /boot (if you have separate boot). Yes, apt process breaks when there is no free space on /boot and can't even do clean ups because it needs breathing space for that too. You shouldn't have let it become this bad, watch out the free space on /boot regularly. Especially if you assigned little space to /boot.

Yes, you can delete files directly with rm, just be careful not to delete the working kernel. The ls -l will show you more details including file size. The files with biggest size in /boot are vmlinuz (the kernel itself) and initrd.img. Delete them in pairs, for the same -XX- kernel version.

Try to make 75-100MB free on /boot and try the install -f again. Don't try the autoremove, ignore that message.

So basically you will be working with (not in this order, just throwing all commands in one code snippet):
```
ls -l (to check file size)
df -h (to check free space % on boot)
sudo rm <filename> (to remove files)
sudo apt-get install -f (to repair apt once you have 75-100MB free)
```

That should be it... Give it a go.

---

### Post by scott.bouch on 2016-02-24
Great advice, thank you.. I'm still learning, as you may have guessed!

Results pre-removal:

```
t$ **ls -l**total 228162
-rw-r--r-- 1 root root  1162712 Jul 15  2014 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1164489 Sep 22  2014 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164547 Oct 28  2014 abi-3.13.0-39-generic
-rw-r--r-- 1 root root  1164509 Nov 13  2014 abi-3.13.0-40-generic
-rw-r--r-- 1 root root  1164720 Nov 25  2014 abi-3.13.0-41-generic
-rw-r--r-- 1 root root  1164720 Dec  8  2014 abi-3.13.0-43-generic
-rw-r--r-- 1 root root  1164720 Dec 16  2014 abi-3.13.0-44-generic
-rw-r--r-- 1 root root  1164967 Jan 13  2015 abi-3.13.0-45-generic
-rw-r--r-- 1 root root   165611 Jul 15  2014 config-3.13.0-32-generic
-rw-r--r-- 1 root root   165712 Sep 22  2014 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct 28  2014 config-3.13.0-39-generic
-rw-r--r-- 1 root root   165745 Nov 13  2014 config-3.13.0-40-generic
-rw-r--r-- 1 root root   165745 Nov 25  2014 config-3.13.0-41-generic
-rw-r--r-- 1 root root   165745 Dec  8  2014 config-3.13.0-43-generic
-rw-r--r-- 1 root root   165748 Dec 16  2014 config-3.13.0-44-generic
-rw-r--r-- 1 root root   165748 Jan 13  2015 config-3.13.0-45-generic
drwxr-xr-x 5 root root     1024 Feb  5  2015 grub
-rw-r--r-- 1 root root 24618108 Oct 22  2014 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 24640819 Oct 22  2014 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 24642840 Oct 29  2014 initrd.img-3.13.0-39-generic
-rw-r--r-- 1 root root 24647909 Nov 26  2014 initrd.img-3.13.0-40-generic
-rw-r--r-- 1 root root 24673623 Dec 11  2014 initrd.img-3.13.0-41-generic
-rw-r--r-- 1 root root 24670931 Dec 12  2014 initrd.img-3.13.0-43-generic
drwx------ 2 root root    12288 Oct 21  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3381262 Jul 15  2014 System.map-3.13.0-32-generic
-rw------- 1 root root  3386945 Sep 22  2014 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct 28  2014 System.map-3.13.0-39-generic
-rw------- 1 root root  3387231 Nov 13  2014 System.map-3.13.0-40-generic
-rw------- 1 root root  3388792 Nov 25  2014 System.map-3.13.0-41-generic
-rw------- 1 root root  3388760 Dec  8  2014 System.map-3.13.0-43-generic
-rw------- 1 root root  3388834 Dec 16  2014 System.map-3.13.0-44-generic
-rw------- 1 root root  3389258 Jan 13  2015 System.map-3.13.0-45-generic
-rw------- 1 root root  5798112 Jul 15  2014 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  5808832 Sep 22  2014 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5808544 Oct 28  2014 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  5808960 Nov 13  2014 vmlinuz-3.13.0-40-generic
-rw------- 1 root root  5814112 Nov 25  2014 vmlinuz-3.13.0-41-generic
-rw------- 1 root root  5814080 Dec  8  2014 vmlinuz-3.13.0-43-generic
-rw------- 1 root root  5814496 Dec 16  2014 vmlinuz-3.13.0-44-generic
-rw------- 1 root root  5814112 Jan 13  2015 vmlinuz-3.13.0-45-generic
```


```
$** df -h**Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/6FC--vg-root  104G   19G   81G  19% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
udev                      3.0G  4.0K  3.0G   1% /dev
tmpfs                     597M  1.3M  596M   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      3.0G  187M  2.8G   7% /run/shm
none                      100M     0  100M   0% /run/user
/dev/sda1                 236M  230M     0 100% /boot
/dev/sdb1                 459G  385G   51G  89% /media/storage
```

Yes, /dev/sda1 is 100% full... Now for some deleting...

Thanks again...

---

### Post by scott.bouch on 2016-02-24
Ok, now we have:

```
$ **ls -l**total 35060
-rw-r--r-- 1 root root  1164720 Dec  8  2014 abi-3.13.0-43-generic
-rw-r--r-- 1 root root   165745 Dec  8  2014 config-3.13.0-43-generic
drwxr-xr-x 5 root root     1024 Feb  5  2015 grub
-rw-r--r-- 1 root root 24670931 Dec 12  2014 initrd.img-3.13.0-43-generic
drwx------ 2 root root    12288 Oct 21  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3388760 Dec  8  2014 System.map-3.13.0-43-generic
-rw------- 1 root root  5814080 Dec  8  2014 vmlinuz-3.13.0-43-generic



```

and

```
$ **df -h**Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/6FC--vg-root  104G   19G   81G  19% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
udev                      3.0G  4.0K  3.0G   1% /dev
tmpfs                     597M  1.7M  596M   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      3.0G  187M  2.8G   7% /run/shm
none                      100M     0  100M   0% /run/user
/dev/sda1                 236M   41M  183M  19% /boot
/dev/sdb1                 459G  385G   51G  89% /media/storage



```

183 mb now free in /boot!

```
$ sudo apt-get install -fReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-41 linux-headers-3.13.0-41-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-37-generic
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-41-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-39-generic
  linux-image-extra-3.13.0-40-generic linux-image-extra-3.13.0-41-generic
  linux-image-extra-3.13.0-44-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-46-generic linux-image-3.13.0-79-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-46-generic linux-image-3.13.0-79-generic
0 to upgrade, 2 to newly install, 0 to remove and 436 not to upgrade.
16 not fully installed or removed.
Need to get 0 B/30.3 MB of archives.
After this operation, 84.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 399022 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-79-generic_3.13.0-79.123_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-79-generic (3.13.0-79.123) ...
Preparing to unpack .../linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Setting up libfreetype6:amd64 (2.5.2-1ubuntu2.4) ...
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.13.0-44-generic (3.13.0-44.73) ...
**Internal Error: Could not find image (/boot/vmlinuz-3.13.0-44-generic)**
dpkg: error processing package linux-image-3.13.0-44-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.13.0-45-generic (3.13.0-45.74) ...
**Internal Error: Could not find image (/boot/vmlinuz-3.13.0-45-generic)**
dpkg: error processing package linux-image-3.13.0-45-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.13.0-79-generic (3.13.0-79.123) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /vmlinuz is a dangling linkto /boot/vmlinuz-3.13.0-45-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-3.13.0-79-generic (3.13.0-79.123) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.13.0.79.85) ...
Setting up linux-headers-3.13.0-79 (3.13.0-79.123) ...
Setting up linux-headers-3.13.0-79-generic (3.13.0-79.123) ...
Setting up linux-headers-generic (3.13.0.79.85) ...
Setting up linux-generic (3.13.0.79.85) ...
Setting up linux-headers-3.13.0-46 (3.13.0-46.75) ...
Setting up linux-headers-3.13.0-46-generic (3.13.0-46.75) ...
**No apport report written because the error message indicates it's a follow-up error from a previous failure.**
**                                                                                                            No apport report written because MaxReports has already been reached**
**                                                                                                                                                                                dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-44-generic:**
** linux-image-extra-3.13.0-44-generic depends on linux-image-3.13.0-44-generic; however:**
**  Package linux-image-3.13.0-44-generic is not configured yet.**


**dpkg: error processing package linux-image-extra-3.13.0-44-generic (--configure):**
** dependency problems - leaving unconfigured**
**dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-45-generic:**
** linux-image-extra-3.13.0-45-generic depends on linux-image-3.13.0-45-generic; however:**
**  Package linux-image-3.13.0-45-generic is not configured yet.**


dpkg: error processing package linux-image-extra-3.13.0-45-generic (--configure):
** dependency problems - leaving unconfigured**
Setting up linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-3.13.0-46-generic (3.13.0-46.75) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-libc-dev:amd64 (3.13.0-46.75) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
**Errors were encountered while processing:**
** linux-image-3.13.0-44-generic**
** linux-image-3.13.0-45-generic**
** linux-image-extra-3.13.0-44-generic**
** linux-image-extra-3.13.0-45-generic**
**E: Sub-process /usr/bin/dpkg returned an error code (1)**



```

However,  this has installed 3.13.0-46 and -79... I've updated grub, I'll try rebooting with -79 to see if it works

---

### Post by scott.bouch on 2016-02-24
It worked! thanks!!!

It's now booted successfully with 3.13.0-79!

```
$ uname -a

Linux 6FC 3.13.0-79-generic #123-Ubuntu SMP Fri Feb 19 14:27:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

Many many thanks go to Darko for your help! :o)

I have learnt a lot through this exercise, and I'm grateful for you holding my hand throughout.

Many thanks, Scott.

---

### Post by darkod on 2016-02-24
OK. The first step was to repair apt, even if the process installed a new kernel. After that you can use purge to remove what you don't want.

There is another option for your case. But I don't have time to discuss it in detail now. Basically you can use a custom grub entry that you will put on top, and it will always be first hence it will boot always from it. But don't try to manually add it in grub.cfg, there is a different process to do it.

---

### Post by darkod on 2016-02-24
Great... Now that apt is working you can also try the newer LTS Stack as we discussed. That will bring you to 3.19 or 4.x kernel... If you fee like trying it out too.

PS. If it works with latest 3.13 kernel you can ignore the post mentioning custom entry. You don't need it now.

---

### Post by scott.bouch on 2016-02-24
Hi Darko,

I've done as you suggested, and it appears to have installed ok...

```
$ [B]sudo apt-get install --install-recommends linux-generic-lts-wily
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.13.0-43
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic
  linux-headers-generic-lts-wily linux-image-4.2.0-30-generic
  linux-image-extra-4.2.0-30-generic linux-image-generic-lts-wily thermald
Suggested packages:
  fdutils linux-lts-wily-tools
The following NEW packages will be installed
  linux-generic-lts-wily linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic
  linux-headers-generic-lts-wily linux-image-4.2.0-30-generic
  linux-image-extra-4.2.0-30-generic linux-image-generic-lts-wily thermald
0 to upgrade, 8 to newly install, 0 to remove and 433 not to upgrade.
Need to get 66.1 MB of archives.
After this operation, 295 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-4.2.0-30-generic amd64 4.2.0-30.35~14.04.1 [17.2 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-4.2.0-30-generic amd64 4.2.0-30.35~14.04.1 [38.3 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic-lts-wily amd64 4.2.0.30.24 [2,270 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-4.2.0-30 all 4.2.0-30.35~14.04.1 [9,593 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-4.2.0-30-generic amd64 4.2.0-30.35~14.04.1 [781 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic-lts-wily amd64 4.2.0.30.24 [2,246 B]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic-lts-wily amd64 4.2.0.30.24 [1,798 B]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main thermald amd64 1.4.3-5~14.04.2 [202 kB]
Fetched 66.1 MB in 18s (3,601 kB/s)                                            
Selecting previously unselected package linux-image-4.2.0-30-generic.
(Reading database ... 149137 files and directories currently installed.)
Preparing to unpack .../linux-image-4.2.0-30-generic_4.2.0-30.35~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
Selecting previously unselected package linux-image-extra-4.2.0-30-generic.
Preparing to unpack .../linux-image-extra-4.2.0-30-generic_4.2.0-30.35~14.04.1_amd64.deb ...
Unpacking linux-image-extra-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
Selecting previously unselected package linux-image-generic-lts-wily.
Preparing to unpack .../linux-image-generic-lts-wily_4.2.0.30.24_amd64.deb ...
Unpacking linux-image-generic-lts-wily (4.2.0.30.24) ...
Selecting previously unselected package linux-headers-4.2.0-30.
Preparing to unpack .../linux-headers-4.2.0-30_4.2.0-30.35~14.04.1_all.deb ...
Unpacking linux-headers-4.2.0-30 (4.2.0-30.35~14.04.1) ...
Selecting previously unselected package linux-headers-4.2.0-30-generic.
Preparing to unpack .../linux-headers-4.2.0-30-generic_4.2.0-30.35~14.04.1_amd64.deb ...
Unpacking linux-headers-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
Selecting previously unselected package linux-headers-generic-lts-wily.
Preparing to unpack .../linux-headers-generic-lts-wily_4.2.0.30.24_amd64.deb ...
Unpacking linux-headers-generic-lts-wily (4.2.0.30.24) ...
Selecting previously unselected package linux-generic-lts-wily.
Preparing to unpack .../linux-generic-lts-wily_4.2.0.30.24_amd64.deb ...
Unpacking linux-generic-lts-wily (4.2.0.30.24) ...
Selecting previously unselected package thermald.
Preparing to unpack .../thermald_1.4.3-5~14.04.2_amd64.deb ...
Unpacking thermald (1.4.3-5~14.04.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-30-generic
W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-30-generic
W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-30-generic /boot/vmlinuz-4.2.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic-lts-wily (4.2.0.30.24) ...
Setting up linux-headers-4.2.0-30 (4.2.0-30.35~14.04.1) ...
Setting up linux-headers-4.2.0-30-generic (4.2.0-30.35~14.04.1) ...
Setting up linux-headers-generic-lts-wily (4.2.0.30.24) ...
Setting up linux-generic-lts-wily (4.2.0.30.24) ...
Setting up thermald (1.4.3-5~14.04.2) ...
thermald start/running, process 24014
Processing triggers for ureadahead (0.100.0-16) ...



```


Which resulted in:

```
$ [B]dpkg --list | grep linux-image
[/B]ii  linux-image-3.13.0-79-generic             3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic              4.2.0-30.35~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic       3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic        4.2.0-30.35~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.13.0.79.85                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-wily              4.2.0.30.24                                         amd64        Generic Linux kernel image



```

So, i'll update grub and go for a reboot...

---

### Post by scott.bouch on 2016-02-24
Hi Darko, all updated and working great on 4.2.0-30

```
$ uname -a
Linux 6FC 4.2.0-30-generic #35~14.04.1-Ubuntu SMP Fri Feb 19 14:48:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

Many thanks again for fixing it! I'll make sure I purge out old kernels in the future!

Now to resurrect my webserver I've got to reinstate my SSL security certificate, and find out why my RAM is overheating, but I'll mark this thread as [SOLVED] unless you can think of anything else I should do?

Many thanks again, Scott.

---

### Post by darkod on 2016-02-24
Well, it seems you have the kernel under control now, and the free space on /boot too. So as far as this thread is concerned, I can't think of anything else right now... :)

---

### Post by scott.bouch on 2016-02-24
Thank you again, I've learnt a lot from you!

---

