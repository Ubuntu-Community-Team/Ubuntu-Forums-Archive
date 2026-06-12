---
title: "grub-pc : Depends: grub-common error"
date: 2017-02-03
forum: Server Platforms
---

### Post by wmoran on 2017-02-03
Hello,
I am running Ubuntu Server 16.04.1 LTS (GNU/Linux 4.4.0-45-generic i686)
Since last week the server will not update. I just get the error "The following packages have unmet dependencies". I have tried apt-get -f install & auto clean & auto remove but still the same error. The Server still works and boots as normal. 

```
$ sudo apt dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.

grub-pc : Depends: grub-common (= 2.02~beta2-36ubuntu3.7) but 2.02~beta2-36ubuntu3.6 is installed
grub-pc-bin : Depends: grub-common (= 2.02~beta2-36ubuntu3.7) but 2.02~beta2-36ubuntu3.6 is installed
grub2-common : Depends: grub-common (= 2.02~beta2-36ubuntu3.7) but 2.02~beta2-36ubuntu3.6 is installed
```

---

### Post by QIII on 2017-02-03
Hello!

Please do not include table formatting from Stack Exchange posts -- although it would be even more preferable if you would compose a new post specifically for the UF rather than cutting and pasting from elsewhere.

Also, please use code tags to enclose terminal commands and their results.

Thanks!

---

### Post by darkod on 2017-02-03
You are not out of free space right? Apt-get gets stuck in such cases. Check free space with df -h.
Also, what is the message from apt-get install -f?

---

### Post by wmoran on 2017-02-03
Thanks for your advised QIII. Sorry my error on the copy and paste from my other post. I will close the other post.

Below are the results from the commands. I am using 552G of the 1.2T hard disk


```

$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         737M     0  737M   0% /dev
tmpfs                        151M  4.8M  146M   4% /run
/dev/mapper/bigcat--vg-root  1.8T  552G  1.2T  32% /
tmpfs                        754M     0  754M   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                        754M     0  754M   0% /sys/fs/cgroup
/dev/sda1                    228M   57M  159M  27% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        151M     0  151M   0% /run/user/1000

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following packages will be upgraded:
  grub-common
1 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
3 not fully installed or removed.
Need to get 0 B/1,740 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 179332 files and directories currently installed.)
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.7_i386.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.7) over (2.02~beta2-36ubuntu3.6) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/grub-common_2.02~beta2-36ubuntu3.7_i386.deb (--unpack):
 cannot copy extracted data for './usr/bin/grub-fstest' to '/usr/bin/grub-fstest.dpkg-new': unexpected end of file or stream
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/grub-common_2.02~beta2-36ubuntu3.7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

---

### Post by darkod on 2017-02-04
OK, few things... I see you used the Guided LVM method of partitioning during installation. I don't know if you were aware, but that creates separate /boot partition and very small in size. I really don't know why Canonical hasn't changed this yet, they should have years ago. When HDDs were very small it was a good thing the automatic partitioning to create small /boot (not to use too much space on the HDD), but these days they should make it 1GB or 2GB at least. HDDs have much greater capacity.

You can see you are using 552GB of 1.8TB on root but also you are using 57MB out of 228MB on /boot. Watch out for this because believe me /boot will get filled very soon with new kernels being installed unless you clean up the old ones regularly.

If the server is still not in production and you have not done any important time consuming setup, I actually recommend to reinstall and use the manual partitioning to create larger /boot and LVM on the rest of the disk. Besides the way you are using it, do you really need LVM? I see you have single LV and you assigned all space to it already. True, this still gives you option to expand in the future. All of this is unrelated to the grub error, but if you decide to reinstall then there is no point continuing to talk about the error because I think the reinstall will sort it out...

Now, if you don't want to reinstall, you need to take a look why does it report data corrupt error during unpacking grub-common. If you look carefully (and I'm no expert with apt-get), it seems to me the package is already downloaded because it never says 'downloading'. It tries to unpack it and reports corruption. So the downloaded package might be corrupt but because it is already there it doesn't even try downloading it again. A quick fix to try might be to simply delete that downloaded package which is in /var/cache/apt/archives and then try the apt-get install -f again.

Second option would be to completely purge and then install grub, but it is little risky because if the purge finishes successfully but the install does not, the server can be left without bootloader. But that is unlikely to happen. However if it does happen, do not reboot until you successfully install grub. To do the purge and install you can try:
```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-initramfs -u
sudo grub-install /dev/sda
```

That should take care of it.

Let us know how it goes...

---

### Post by wmoran on 2017-02-04
Thanks for your help.

Your are correct about the /boot partition and the size. In the past I had to remove old packages as the server would not boot on restart.
This server is not in every day use, I just use it for 2nd backup for my desktop. A few months ago I removed a large number kernel packages to 
free up space on the boot partition. I may have removed some dependencies which caused this error. I will replace the disk and reinstall the OS.

Reinstall looks to be the best option. 


```
sudo apt-get purge grub-pc grub-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2) but it is not going to be installed
 grub-pc-bin : Depends: grub-common (= 2.02~beta2-36ubuntu3.7) but it is not going to be installed
 grub2-common : Depends: grub-common (= 2.02~beta2-36ubuntu3.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

