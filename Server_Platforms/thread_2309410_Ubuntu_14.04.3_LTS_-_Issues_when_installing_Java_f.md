---
title: "Ubuntu 14.04.3 LTS - Issues when installing Java for minecraft server."
date: 2016-01-10
forum: Server Platforms
---

### Post by Jamie_Harris on 2016-01-10
Hello all!

First of all I would like to mention that I am not the most experienced at Linux but I have been learning a lot over the past 12 months or so. (Google is my friend when it comes to running into errors for fixes)

I have searched google-wide for a fix to this but I can't seem to find something that works, so I thought it would be good to try here where the experts are at :)

So, I am trying to install a Minecraft Server on a dedicated server that I rent.

I install minecraft, screen etc perfectly until I come to Java.

So I follow these steps:

> sudo apt-get update

I run into this error: 

```

You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-73-generic : Depends: linux-image-3.13.0-73-generic but it is not installed
 linux-image-extra-3.13.0-74-generic : Depends: linux-image-3.13.0-74-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-74-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

When I check if I already have Java installed using:

> java -version

I get the following output:

```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: apt-get install <selected package>
```

so I do as it asks, I try to install "default-jre" and again I get the following error:

```

You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-73-generic : Depends: linux-image-3.13.0-73-generic but it is not installed
 linux-image-extra-3.13.0-74-generic : Depends: linux-image-3.13.0-74-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-74-generic but it is not installed
E: Unmet dependencies. Try using -f.
```


When I try to follow the instructions above, I get the following:

```

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-63 linux-headers-3.13.0-63-generic
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-headers-3.13.0-67 linux-headers-3.13.0-67-generic
  linux-headers-3.13.0-68 linux-headers-3.13.0-68-generic
  linux-headers-3.13.0-71 linux-headers-3.13.0-71-generic
  linux-headers-3.13.0-73 linux-headers-3.13.0-73-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-65-generic
  linux-image-3.13.0-66-generic linux-image-3.13.0-67-generic
  linux-image-3.13.0-68-generic linux-image-3.13.0-71-generic
  linux-image-3.13.0-73-generic linux-image-extra-3.13.0-63-generic
  linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-66-generic
  linux-image-extra-3.13.0-67-generic linux-image-extra-3.13.0-68-generic
  linux-image-extra-3.13.0-71-generic linux-image-extra-3.13.0-73-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-73-generic linux-image-3.13.0-74-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-73-generic linux-image-3.13.0-74-generic
0 to upgrade, 2 to newly install, 0 to remove and 43 not to upgrade.
7 not fully installed or removed.
Need to get 0 B/30.5 MB of archives.
After this operation, 85.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 326396 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-74-generic_3.13.0-74.118_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-74-generic (3.13.0-74.118) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-74-generic_3.13.0-74.118_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-74-generic' to '/boot/vmlinuz-3.13.0-74-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Preparing to unpack .../linux-image-3.13.0-73-generic_3.13.0-73.116_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-73-generic (3.13.0-73.116) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-73-generic_3.13.0-73.116_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-73-generic' to '/boot/System.map-3.13.0-73-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-73-generic /boot/vmlinuz-3.13.0-73-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-74-generic_3.13.0-74.118_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-73-generic_3.13.0-73.116_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So my question is do you know how this can be fixed? If so, would you be so kind as to telling me how I can fix this.

Thanks for reading and thanks in advance for any help provided.

Jamie

---

### Post by nerdtron on 2016-01-10
You're doing a pretty good job searching for answers and following the suggestions of Ubuntu. Keep it up.
From your apt-get -f output, looks like you don't have enough hard drive space on your /boot partition.
```
Unpacking linux-image-3.13.0-73-generic (3.13.0-73.116) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-73-generic_3.13.0-73.116_amd64.deb (--unpack):
cannot copy extracted data for './boot/System.map-3.13.0-73-generic' to '/boot/System.map-3.13.0-73-generic.dpkg-new': failed to write (No space left on device) 
```

What is the output of:
```
df -Th 
```

---

### Post by Jamie_Harris on 2016-01-10
```

Filesystem                     Type      Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-lv_root ext4      915G   19G  850G   3% /
none                           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                           devtmpfs  5.8G  4.0K  5.8G   1% /dev
tmpfs                          tmpfs     1.2G  608K  1.2G   1% /run
none                           tmpfs     5.0M     0  5.0M   0% /run/lock
none                           tmpfs     5.9G  1.1M  5.9G   1% /run/shm
none                           tmpfs     100M     0  100M   0% /run/user
/dev/md0                       ext4      232M  227M     0 100% /boot

```

This is the output I am getting.

Trying to learn Linux rather than just letting someone else do it for me, because I feel it is good knowledge to have!

I assume from what you have just shown me, I have to allocate more space to a partition.. the question then is, how :D

---

### Post by nerdtron on 2016-01-10
```
 /dev/md0 ext4 232M 227M 0 100% /boot  
```

Yup, your /boot is full. From the output of the apt-get -f command above, it looks like you are installing/updating to a new kernel. But since the kernels are saved to the /boot partition, which is already full, you'll get those errors. Now I think it will be difficult to increase the space on /boot. (unless you re-partition it, which could mean re-install). 

Maybe we'll wait for others to tell you how to "clean-up" the /boot and free up some space. I know you'll need to uninstall/remove the older kernels first. But it's been a long time since I did that.

---

### Post by Jamie_Harris on 2016-01-10
Thanks, you have been a great help! I will search google to see if I can find the solution whilst waiting for someone to respond here!

---

### Post by nerdtron on 2016-01-10
Three good links for cleaning-up /boot:
[http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition](http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition)
[http://www.dangtrinh.com/2015/02/clean-up-boot-partition-in-ubuntu-server.html](http://www.dangtrinh.com/2015/02/clean-up-boot-partition-in-ubuntu-server.html)
[http://discourse.ubuntu.com/t/how-do-you-clean-up-the-boot-partition/2173](http://discourse.ubuntu.com/t/how-do-you-clean-up-the-boot-partition/2173)


Always remember, DO NOT DELETE the currently running kernel. 
```
 uname -r 
``` 
will show you the currently in-used kernel.

---

### Post by Jamie_Harris on 2016-01-10
Thanks nerdtron for helping, this how now been solved!

By deleting the unrequired image / image-extra files using:

```
apt-get remove linux-image-3.13.0-74-generic
```
and
```
apt-get remove linux-image-extra-3.13.0-74-generic
```

Changing the version value for each and then running update / upgrade + autoremove.

I am now at 69% of my boot partition!

---

### Post by deadflowr on 2016-01-10
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") over quote tags when posting terminal output.

---

### Post by Jamie_Harris on 2016-01-10
Ok, my bad thanks deadflowr!

---

### Post by MAFoElffen on 2016-01-10
Biting tongue... If you look at some of your output from your first post:
```

The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-63 linux-headers-3.13.0-63-generic
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-headers-3.13.0-67 linux-headers-3.13.0-67-generic
  linux-headers-3.13.0-68 linux-headers-3.13.0-68-generic
  linux-headers-3.13.0-71 linux-headers-3.13.0-71-generic
  linux-headers-3.13.0-73 linux-headers-3.13.0-73-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-65-generic
  linux-image-3.13.0-66-generic linux-image-3.13.0-67-generic
  linux-image-3.13.0-68-generic linux-image-3.13.0-71-generic
  linux-image-3.13.0-73-generic linux-image-extra-3.13.0-63-generic
  linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-66-generic
  linux-image-extra-3.13.0-67-generic linux-image-extra-3.13.0-68-generic
  linux-image-extra-3.13.0-71-generic linux-image-extra-3.13.0-73-generic
Use 'apt-get autoremove' to remove them.

```
If you would have followed the instructions from your output
```

sudo apt-get autoremove

```
... then it would remove kernels 3.13.0-63, 3.13.0-65,  3.13.0-66, 3.13.0-67, 3.13.0-68, 3.13.0-71, 3.13.0-73. That kind of message also appears occasionally when you upgrade ... so this means you've ignored or not been aware of that for a long time.

Just doing that will save you allot of typing. That and (not many people no this) after doing that and then 
```

sudo apt-get install -f

```
... to finish installing your new kernel, you should end of with 3 kernels. The newly installed, the kernel you were running on when you installed the newest, and one more previous to that one.

Tip-- 3 apt-get commands to remember in a pinch:
```

sudo apt-get autoremove    # This command removes packages that were installed by other packages to satisfy (previous) dependencies and are no longer needed.
sudo apt-get install -f    # Fix; attempt to correct a system with broken dependencies in place. 
sudo apt-get autoclean   # This command removes .deb files for packages that are no longer installed on your system. Depending on your installation habits, removing these files from /var/cache/apt/archives may regain a significant amount of diskspace.

```

---

