---
title: "Acer Extensa 4420 hangs with kernel 3.2"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-24
Nov 24 17:28:56 ventrical-Extensa-4420 kernel: [   18.524507] [drm]     TV1: INTERNAL_KLDSCP_DAC1
Nov 24 17:28:56 ventrical-Extensa-4420 kernel: [   18.538510] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
Nov 24 17:28:56 ventrical-Extensa-4420 kernel: [   18.581775]

 I was able to go back to 3.0-0.13 and gather the above. I have no screen or terminal with that (64bit) kernel.

---

### Post by Jordanwb on 2011-11-24
Stating the obvious here but it sounds like a regression in the kernel with the radeon module.

---

### Post by Harry33 on 2011-11-25
> **Jordanwb said:**
> Stating the obvious here but it sounds like a regression in the kernel with the radeon module.

The same topic has been discussed here elsewhere too.
The same results.

BTW, rc3 of the kernel 3.2 is out now.

---

### Post by ventrical on 2011-11-25
> **Harry33 said:**
> The same topic has been discussed here elsewhere too.
The same results.

BTW, rc3 of the kernel 3.2 is out now.

@harry33,jordanwb

Could you walk me through on how to remove the 3.2 kernel and post a link for the new rc kernel ??

thanks

---

### Post by Harry33 on 2011-11-25
> **ventrical said:**
> @harry33,jordanwb

Could you walk me through on how to remove the 3.2 kernel and post a link for the new rc kernel ??

thanks

Well here is the new 3.2 rc3 kernel (PP repos):
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4)

To remove 3.2 kernels, you need to have older (like 3.1) installed first.
Get it from here:
[https://launchpad.net/ubuntu/+source/linux/3.1.0-2.3](https://launchpad.net/ubuntu/+source/linux/3.1.0-2.3)

Then reboot and from the grub choose that 3.1 kernel.
Then it is perhaps the easiest way to uninstall 3.2 kernel (three packages per version) with Synaptic.

Note that if you play a lot with different kernel versions, you should uninstall the kernel meta packages. You don't need them anyway. They are only used to enable automatic upgrading of the kernel.

---

### Post by ventrical on 2011-11-25
> **Harry33 said:**
> Well here is the new 3.2 rc3 kernel (PP repos):
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-2.4)

To remove 3.2 kernels, you need to have older (like 3.1) installed first.
Get it from here:
[https://launchpad.net/ubuntu/+source/linux/3.1.0-2.3](https://launchpad.net/ubuntu/+source/linux/3.1.0-2.3)

Then reboot and from the grub choose that 3.1 kernel.
Then it is perhaps the easiest way to uninstall 3.2 kernel (three packages per version) with Synaptic.

Note that if you play a lot with different kernel versions, you should uninstall the kernel meta packages. You don't need them anyway. They are only used to enable automatic upgrading of the kernel.


harry33,

 I cannot figure out how to line up that link.   Could you please present  those 3.1.0-2.3  like you did here for 3.2:
[http://ubuntuforums.org/showpost.php?p=11476899&postcount=11](http://ubuntuforums.org/showpost.php?p=11476899&postcount=11)

[http://ubuntuforums.org/showpost.php?p=11476899&postcount=11](http://ubuntuforums.org/showpost.php?p=11476899&postcount=11)

because when I go to those launchpad links I can't find those files that we are supposed to download.


thanks again...

 I don't mean to be a pest...  :)

---

### Post by Harry33 on 2011-11-25
Rigth, here you go. This is for kernel 3.2 rc3, including the libc-dev package.

32-bit:
[linux-libc-dev_3.2.0-2.4_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952347/+files/linux-libc-dev_3.2.0-2.4_i386.deb")
[linux-headers-3.2.0-2_3.2.0-2.4_all.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952347/+files/linux-headers-3.2.0-2_3.2.0-2.4_all.deb")
[linux-headers-3.2.0-2-generic_3.2.0-2.4_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952347/+files/linux-headers-3.2.0-2-generic_3.2.0-2.4_i386.deb")
[linux-image-3.2.0-2-generic_3.2.0-2.4_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952347/+files/linux-image-3.2.0-2-generic_3.2.0-2.4_i386.deb")

64-bit
[linux-libc-dev_3.2.0-2.4_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952345/+files/linux-libc-dev_3.2.0-2.4_amd64.deb")
[linux-headers-3.2.0-2_3.2.0-2.4_all.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952347/+files/linux-headers-3.2.0-2_3.2.0-2.4_all.deb")
[linux-headers-3.2.0-2-generic_3.2.0-2.4_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952345/+files/linux-headers-3.2.0-2-generic_3.2.0-2.4_amd64.deb")
[linux-image-3.2.0-2-generic_3.2.0-2.4_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-2.4/+build/2952345/+files/linux-image-3.2.0-2-generic_3.2.0-2.4_amd64.deb")

I have tested the 64-bit kernel architecture with nvidia-current_290.10 and it works very well and fast.

---

### Post by ventrical on 2011-11-25
@harry33 and all,

 I had just recently realized that I had forgotten to upgrade my repositories to Precise BEFORE I had installed the 3.2 kernel.

My apologies if I had inconvenienced anyone.

Thanks also for links :)

---

### Post by Harry33 on 2011-11-25
> **ventrical said:**
> @harry33 and all,

 I had just recently realized that I had forgotten to upgrade my repositories to Precise BEFORE I had installed the 3.2 kernel.

My apologies if I had inconvenienced anyone.

Thanks also for links :)

The kernel 3.2 rc3 is in Precise repos now.

---

### Post by ventrical on 2011-11-25
> **Harry33 said:**
> The kernel 3.2 rc3 is in Precise repos now.


The problem I think is definitly the fglrx restricted drivers. By default they are not installed along with the 64bit package (it appears) . I keep falling back into Unity 2D.

  I ran the code:

sudo apt-get install fglrx   and got the following output:

```
ventrical@ventrical-Extensa-4420:~$ sudo apt-get install fglrx
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx264-116 libmagickcore3 libmagickwand3 libjpeg62:i386
  libmagickcore3-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx-amdcccle lib32gcc1 libc6-i386
The following NEW packages will be installed:
  fglrx fglrx-amdcccle lib32gcc1 libc6-i386
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.4 MB of archives.
After this operation, 191 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libc6-i386 amd64 2.13-20ubuntu5 [3,851 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32gcc1 amd64 1:4.6.2-5ubuntu1 [54.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx amd64 2:8.911-0ubuntu1 [54.6 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/restricted fglrx-amdcccle amd64 2:8.911-0ubuntu1 [5,909 kB]
Fetched 64.4 MB in 4min 5s (262 kB/s)                                          
Selecting previously unselected package libc6-i386.
(Reading database ... 238739 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.13-20ubuntu5_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.2-5ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.911-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.911-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libc6-i386 (2.13-20ubuntu5) ...
Setting up lib32gcc1 (1:4.6.2-5ubuntu1) ...
Setting up fglrx (2:8.911-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.911 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-2-generic
Building for architecture x86_64
Building initial module for 3.2.0-2-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-2-generic/updates/dkms/

depmod.........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.911-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-2-generic
ventrical@ventrical-Extensa-4420:~$ 
```

So  all is working  except for the ATi Radeon driver. I have:01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]


Are there any ideas on how to install this correctly or , as it has been mentioned, are there still problems with the current drivers/repos?

thanks in advance..

---

### Post by ventrical on 2011-11-27
I can't seem to get rid of the old fglrx files and does anybody know what the heck is OpenCL ??

   I thought it was OpenGL. The files from the repos try to write an OpenCL.

Can't seem to get the right driver for this 64bit.

---

### Post by Jordanwb on 2011-11-28
> **ventrical said:**
> does anybody know what the heck is OpenCL ??

[http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)

---

### Post by ventrical on 2011-11-28
> **Jordanwb said:**
> [http://en.wikipedia.org/wiki/OpenCL](http://en.wikipedia.org/wiki/OpenCL)

 Thanks .. I finally found that a day or so ago :(  .

 Now if I could get these ATI drivers working on this beast .... :)

---

### Post by madjr on 2011-11-29
sub.

i also have an 4420 :o

seems every cycle there are new issues lol. Glad some of them are getting spotted early :D

---

### Post by ventrical on 2011-11-29
> **madjr said:**
> sub.

i also have an 4420 :o

seems every cycle there are new issues lol. Glad some of them are getting spotted early :D

 I guess I am going to have to do a fresh (64bit) install because the kernel will just not config to those drivers. I cleaned them , purged them, prayed at them and ever swore at them  and  no way I can get rid of them :)

---

### Post by cariboo on 2011-11-29
Are you purging the driver at the command line with lightdm/gdm stopped?

---

### Post by ventrical on 2011-11-29
> **cariboo907 said:**
> Are you purging the driver at the command line with lightdm/gdm stopped?

The link did not instruct me to do so.

 I'll look into that.

Thanks.

---

### Post by ventrical on 2011-11-29
> **cariboo907 said:**
> Are you purging the driver at the command line with lightdm/gdm stopped?


The link :  [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

assumes that I have stopped gdm but does not instruct on how to do so.

I used the terminal to purge and followed the instruction in the link above. Am I wayward on this ? or , how do I stop lightdm/gdm?

---

### Post by cariboo on 2011-11-29
> **ventrical said:**
> The link :  [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

assumes that I have stopped gdm but does not instruct on how to do so.

I used the terminal to purge and followed the instruction in the link above. Am I wayward on this ? or , how do I stop lightdm/gdm?

For GDM:

```
sudo service gdm stop
```

and for lightdm:

```
sudo service lightdm stop
```

---

### Post by ventrical on 2011-11-30
> **cariboo907 said:**
> For GDM:

```
sudo service gdm stop
```and for lightdm:

```
sudo service lightdm stop
```

I could only get the WSOD  when I tried to get to terminal.(White Screen of Death)

  I went to root terminal from GRUB recovery mode, entered this code:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*

 and got the errors:

W:Not using locking for read only lock file /var/lib/dpkg/lock
E: The package list or status file  could not be parsed or opened
etc.

Thanks anyways.

---

### Post by effenberg0x0 on 2011-11-30
> **ventrical said:**
> I could only get the WSOD  when I tried to get to terminal.(White Screen of Death)

  I went to root terminal from GRUB recovery mode, entered this code:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*

 and got the errors:

W:Not using locking for read only lock file /var/lib/dpkg/lock
E: The package list or status file  could not be parsed or opened
etc.

Thanks anyways.

The command "mount" will show you the mounted units. If / is mounted ro (read-only) this is one of the situations I pasted to your thread :)
Check this: [http://ubuntuforums.org/showpost.php?p=10125901&postcount=8](http://ubuntuforums.org/showpost.php?p=10125901&postcount=8)
It may relate as a temp. solution.

---

### Post by effenberg0x0 on 2011-11-30
Look at me, I'm an erased double post.[]("http://ubuntuforums.org/showpost.php?p=10125901&postcount=8")

---

### Post by cariboo on 2011-11-30
> **ventrical said:**
> I could only get the WSOD  when I tried to get to terminal.(White Screen of Death)

  I went to root terminal from GRUB recovery mode, entered this code:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*

 and got the errors:

W:Not using locking for read only lock file /var/lib/dpkg/lock
E: The package list or status file  could not be parsed or opened
etc.

Thanks anyways.

Did you check to see if the lock file in /var/lib/dpkg was stale? And if so, I'd suggest you remove it and try again.

---

### Post by ventrical on 2011-11-30
> **cariboo907 said:**
> Dis you check to see if the lock file in /var/lib/dpkg was stale? And if so, I'd suggest you remove it and try again.

 It has Zero bytes if that is what you mean by stale (the 'lock' file) and I cannot remove it - or do not know the commands to do so. I tried to log on as root in terminal but I still cannot remove it as it will not allow me the option to do so.

---

### Post by ventrical on 2011-11-30
> **effenberg0x0 said:**
> The command "mount" will show you the mounted units. If / is mounted ro (read-only) this is one of the situations I pasted to your thread :)
Check this: [http://ubuntuforums.org/showpost.php?p=10125901&postcount=8](http://ubuntuforums.org/showpost.php?p=10125901&postcount=8)
It may relate as a temp. solution.
```
root@ventrical-Extensa-4420:/var/lib/dpkg# mount
/dev/sda14 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ventrical/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ventrical)
/dev/sda8 on /media/138f5b6a-07f0-4af2-acc1-2ec7aece7ed2 type ext4 (rw,nosuid,nodev,uhelper=udisks)
root@ventrical-Extensa-4420:/var/lib/dpkg# 

```

---

### Post by Bowmore on 2011-11-30
@ventrical
> W:Not using locking for read only lock file /var/lib/dpkg/lock
E: The package list or status file could not be parsed or opened
etc.
Not sure it's about MergeLists but,
try remove the merge lists and recreate them again with:
```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by ventrical on 2011-11-30
That code did some stuff but I am not sure it worked. This may sound really dumb , but, I have completely forgot how to give myself permissions so I can remove that stale 'lock' file as Cariboo suggested.

---

### Post by cariboo on 2011-11-30
Try:

```
sudo -i
```

then

```
rm /var/lib/dpkg/lock
```

---

### Post by ventrical on 2011-11-30
> **cariboo907 said:**
> Try:

```
sudo -i
```then

```
rm /var/lib/dpkg/lock
```


I'll give this a shot.  So it's 'rm' eh ? Thanks for that Cariboo907.

I  did a successful (64bit) install on a pendrive. Unity 3D working fine. So It is something that I did or did not do  when I installed the 3.2.x-x kernel back a while ago that borked the system.  A fresh install would definetly be a lot quicker to solve this , but , nonetheless I like learning this code!!:)

Thanks again.

---

### Post by ventrical on 2011-11-30
> **cariboo907 said:**
> Try:

```
sudo -i
```then

```
rm /var/lib/dpkg/lock
```

  Ok.. I was able to get rid of that file but still get the same message when I log in to recovery terminal from GRUB and try to remove/purge fglrx, however I did get some activity, and some stuff was removed but got these messages also:


Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-amdcccle-updates is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed


and here is the log:

```
ventrical@ventrical-Extensa-4420:~$ sudo -i
[sudo] password for ventrical: 
root@ventrical-Extensa-4420:~# rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
root@ventrical-Extensa-4420:~# locate fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/jockey/handlers/fglrx.py
/var/cache/apt/archives/fglrx-amdcccle_2%3a8.911-0ubuntu1_amd64.deb
/var/cache/apt/archives/fglrx_2%3a8.911-0ubuntu1_amd64.deb
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sums
/var/lib/dpkg/info/fglrx.conffiles
/var/lib/dpkg/info/fglrx.list
/var/lib/dpkg/info/fglrx.md5sums
/var/lib/dpkg/info/fglrx.postinst
/var/lib/dpkg/info/fglrx.postrm
/var/lib/dpkg/info/fglrx.preinst
/var/lib/dpkg/info/fglrx.prerm
/var/lib/dpkg/info/fglrx.shlibs
root@ventrical-Extensa-4420:~# sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-amdcccle-updates is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libx264-116 libmagickcore3 libmagickwand3 libc6-i386 lib32gcc1
  libjpeg62:i386 libmagickcore3-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
root@ventrical-Extensa-4420:~# 
```so when I try t reinstall fglrx they are installed from disk and not downloaded from repos. am I assuming correctly that those above mentioned files have to be manually removed?

---

### Post by cariboo on 2011-11-30
The packages are archived in /var/cache/apt/archives, so unless there is a newer version, the system will use the files it has already downloaded. To clear the archived packages use:

```
sudo apt-get clean
```

---

### Post by ventrical on 2011-12-01
The WSOD is gone and I can get terminal now (switch between desktop and Ctrl+Alt+F1) but those files are still there and teh 'lock' file keeps comming back.
```

ventrical@ventrical-Extensa-4420:~$ sudo apt-get clean
[sudo] password for ventrical: 
ventrical@ventrical-Extensa-4420:~$ locate fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/jockey/handlers/fglrx.py
/var/cache/apt/archives/fglrx-amdcccle_2%3a8.911-0ubuntu1_amd64.deb
/var/cache/apt/archives/fglrx_2%3a8.911-0ubuntu1_amd64.deb
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sums
/var/lib/dpkg/info/fglrx.conffiles
/var/lib/dpkg/info/fglrx.list
/var/lib/dpkg/info/fglrx.md5sums
/var/lib/dpkg/info/fglrx.postinst
/var/lib/dpkg/info/fglrx.postrm
/var/lib/dpkg/info/fglrx.preinst
/var/lib/dpkg/info/fglrx.prerm
/var/lib/dpkg/info/fglrx.shlibs
ventrical@ventrical-Extensa-4420:~$ sudo apt-get clean
ventrical@ventrical-Extensa-4420:~$ sudo apt-get clean
ventrical@ventrical-Extensa-4420:~$ sudo -i
root@ventrical-Extensa-4420:~# rm /var/lib/dpkg/lock
root@ventrical-Extensa-4420:~# sudo apt-get clean
root@ventrical-Extensa-4420:~# locate fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/jockey/handlers/fglrx.py
/var/cache/apt/archives/fglrx-amdcccle_2%3a8.911-0ubuntu1_amd64.deb
/var/cache/apt/archives/fglrx_2%3a8.911-0ubuntu1_amd64.deb
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sums
/var/lib/dpkg/info/fglrx.conffiles
/var/lib/dpkg/info/fglrx.list
/var/lib/dpkg/info/fglrx.md5sums
/var/lib/dpkg/info/fglrx.postinst
/var/lib/dpkg/info/fglrx.postrm
/var/lib/dpkg/info/fglrx.preinst
/var/lib/dpkg/info/fglrx.prerm
/var/lib/dpkg/info/fglrx.shlibs
root@ventrical-Extensa-4420:~# 
```

so what may be the next step in this proceedure ??

I'll keep trying here. If I try to re-install fglrx it will only use the same archives and I will be back to square one.

---

### Post by ventrical on 2011-12-01
I decided to opt for a fresh install. It took 1/20th the time to re-install from the LiveCD to the old partition than it did trying to employ a work-a-round.

Thank you all for your help in this matter.

I will also make a note about fresh installs on the crash/recovery page.

My reason for the 64bit install was to test performance over 32bit installs. The response time is much snappier when loading programs and 64bit seems to handle SATA drives better.

Thanks all. for your help.

---

### Post by ventrical on 2011-12-01
Well, fresh install went really well. Then I updated sources list and then sudo apt-get update, sudo apt-get upgrade and I am right back where I started. No unity 3D, just roll back to Unity 2D.

Linux ventrical-Extensa-4420 3.2.0-2-generic #5-Ubuntu SMP Mon Nov 28 18:10:23 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux No WSOD though and terminal is working with Crtl+Alt+F1.

---

