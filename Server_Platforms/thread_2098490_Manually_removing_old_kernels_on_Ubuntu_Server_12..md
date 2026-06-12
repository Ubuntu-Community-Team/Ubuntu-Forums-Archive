---
title: "Manually removing old kernels on Ubuntu Server 12.04"
date: 2012-12-26
forum: Server Platforms
---

### Post by ranger12 on 2012-12-26
Hello all, just a simple question. I want to remove only some of the old kernels out of the /boot directory on my Server 12.04 file server so I can update to the latest kernel. I was wondering which files in the /boot directory I can delete. This is the ls output from the command prompt:

abi-3.2.0-23-generic-pae         initrd.img-3.2.0-30-generic-pae
abi-3.2.0-24-generic-pae         initrd.img-3.2.0-31-generic-pae
abi-3.2.0-25-generic-pae         initrd.img-3.2.0-32-generic-pae
abi-3.2.0-26-generic-pae         initrd.img-3.2.0-33-generic-pae
abi-3.2.0-27-generic-pae         lost+found
abi-3.2.0-29-generic-pae         memtest86+.bin
abi-3.2.0-30-generic-pae         memtest86+_multiboot.bin
abi-3.2.0-31-generic-pae         System.map-3.2.0-23-generic-pae
abi-3.2.0-32-generic-pae         System.map-3.2.0-24-generic-pae
abi-3.2.0-33-generic-pae         System.map-3.2.0-25-generic-pae
config-3.2.0-23-generic-pae      System.map-3.2.0-26-generic-pae
config-3.2.0-24-generic-pae      System.map-3.2.0-27-generic-pae
config-3.2.0-25-generic-pae      System.map-3.2.0-29-generic-pae
config-3.2.0-26-generic-pae      System.map-3.2.0-30-generic-pae
config-3.2.0-27-generic-pae      System.map-3.2.0-31-generic-pae
config-3.2.0-29-generic-pae      System.map-3.2.0-32-generic-pae
config-3.2.0-30-generic-pae      System.map-3.2.0-33-generic-pae
config-3.2.0-31-generic-pae      vmlinuz-3.2.0-23-generic-pae
config-3.2.0-32-generic-pae      vmlinuz-3.2.0-24-generic-pae
config-3.2.0-33-generic-pae      vmlinuz-3.2.0-25-generic-pae
grub                             vmlinuz-3.2.0-26-generic-pae
initrd.img-3.2.0-23-generic-pae  vmlinuz-3.2.0-27-generic-pae
initrd.img-3.2.0-24-generic-pae  vmlinuz-3.2.0-29-generic-pae
initrd.img-3.2.0-25-generic-pae  vmlinuz-3.2.0-30-generic-pae
initrd.img-3.2.0-26-generic-pae  vmlinuz-3.2.0-31-generic-pae
initrd.img-3.2.0-27-generic-pae  vmlinuz-3.2.0-32-generic-pae
initrd.img-3.2.0-29-generic-pae  vmlinuz-3.2.0-33-generic-pae

I probably would like to remove just 23,24 and 25 for right now. Currently I am running 33 but that is outdated now. When I do this, do I need to update grub?

---

### Post by steeldriver on 2012-12-26
Hi I think rather than manually deleting things, it is better to remove/purge the corresponding linux-image package - see here

[http://ubuntuforums.org/showthread.php?t=2097024](http://ubuntuforums.org/showthread.php?t=2097024)

I believe that will update grub / initramfs automatically as well

---

### Post by ranger12 on 2012-12-26
Thanks but that is not working and I don't understand why. This is the output after issuing the command:

administrator@server1:~$ sudo apt-get remove linux-image-3.2.0-23-generic-pae
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-34-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 
I tried apt-get -f install of course but it gives in the output that there is no space on device which I already knew that.

---

### Post by Primefalcon on 2012-12-26
Some advice, keep one or 2 older kernerls around, sometimes problems can happen, and having an older kernel to boot using can really be a life saver

---

### Post by ranger12 on 2012-12-27
As I said in my original post, I wasn't planning on deleting all of them - just some of them. I have all the old kernels and that is the problem - 23 - 33. 98% of the space in /boot is used up and that is what I am trying to do is get rid of some of the old ones so I can continue to update with the new ones. Remove and purge is not working becuase it keeps complaining about unmet dependencies. Other than this issue, everything is working great on the server.

---

### Post by cottfcfan on 2012-12-27
I had this problem the other day.
I think what you need to do is make sure everything is updated first, including the new kernel, then it should let you delete the older ones.

---

### Post by ranger12 on 2012-12-27
I can't update with the new kernel becuase it says there is not enough space on the device - menaing /boot. That is why I need to get rid of some of the old kernels so I can have enough space in /boot to update with the new kernel.

---

### Post by cottfcfan on 2012-12-27
I'd try using something like Bleachbit, to reclaim back unwanted space, then update everything & remove the unneeded kernels.
Ubuntu Tweak is also a good cleaning tool.

Edit.. sorry i have just reread your post, you must have separate /boot partition.
In that case try using Synaptic & remove them one by one.

---

### Post by ranger12 on 2012-12-27
I cannot use gui tools because this is Server 12.04 with no gui so Ubuntu Tweak or Synaptic is not an option.  This has to be done with command line. I just simply want to remove a few old kernels from the /boot directory so aptitude on the file server will install the newer kernels. It is up to 35 now but it won't install it because 34 could not be installed because there is not enough space in the /boot directory. I think that is why apt-get -f install is reporting unmet dependencies. I can install other updates to things since they do not go into the /boot directory just not the kernel.  I am thinking that doing it manually maybe the only option that is why I wanted to know which files in the /boot directory for each kernel version I need to take out and what utilities I need to run to update grub and such afterwards.

---

### Post by cottfcfan on 2012-12-27
You could see if any of these tutorials help:
[http://www.google.co.uk/#hl=en&tbo=d&sclient=psy-ab&q=ubuntu+cleaning+up+%2Fboot&oq=ubuntu+cleaning&gs_l=hp.1.1.0l4.2096.5381.0.8698.15.10.0.5.5.0.148.915.7j3.10.0.les%3B..0.0...1c.1.XeJmZ8sHWLY&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.d2k&fp=6a1904ffca346b5f&bpcl=40096503&biw=1120&bih=599](http://www.google.co.uk/#hl=en&tbo=d&sclient=psy-ab&q=ubuntu+cleaning+up+%2Fboot&oq=ubuntu+cleaning&gs_l=hp.1.1.0l4.2096.5381.0.8698.15.10.0.5.5.0.148.915.7j3.10.0.les%3B..0.0...1c.1.XeJmZ8sHWLY&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&bvm=bv.1355534169,d.d2k&fp=6a1904ffca346b5f&bpcl=40096503&biw=1120&bih=599)

---

### Post by steeldriver on 2012-12-27
OK well just for giggles I manually removed a couple of the initrd.img-3.x.x.x- image files from /boot (am going to re-image this box later anyway) to make some headroom, and then ran apt-get purge to see if it would fail / complain - it doesn't

Going to reboot now just to make sure it's happy... EDIT: yup, booted OK

```
$ sudo rm /boot/initrd.img-3.2.0-33-generic-pae 
$ sudo apt-get remove --purge linux-image-3.2.0-33-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.2.0-33-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 113 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 199122 files and directories currently installed.)
Removing linux-image-3.2.0-33-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-33-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-33-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-33-generic-pae /boot/vmlinuz-3.2.0-33-generic-pae
$ 
$ ls -l /boot
total 45500
-rw-r--r-- 1 root root   801759 Nov 15 07:22 abi-3.2.0-34-generic-pae
-rw-r--r-- 1 root root   801798 Dec  5 14:06 abi-3.2.0-35-generic-pae
-rw-r--r-- 1 root root   147452 Nov 15 07:22 config-3.2.0-34-generic-pae
-rw-r--r-- 1 root root   147452 Dec  5 14:06 config-3.2.0-35-generic-pae
drwxr-xr-x 3 root root     5120 Dec 27 10:33 grub
-rw-r--r-- 1 root root 14726182 Nov 30 06:29 initrd.img-3.2.0-34-generic-pae
-rw-r--r-- 1 root root 14729267 Dec 26 10:59 initrd.img-3.2.0-35-generic-pae
drwxr-xr-x 2 root root    12288 Oct  6 12:38 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2313866 Nov 15 07:22 System.map-3.2.0-34-generic-pae
-rw------- 1 root root  2314162 Dec  5 14:06 System.map-3.2.0-35-generic-pae
-rw------- 1 root root  5017504 Nov 15 07:22 vmlinuz-3.2.0-34-generic-pae
-rw------- 1 root root  5017984 Dec  5 14:06 vmlinuz-3.2.0-35-generic-pae
```

---

### Post by ranger12 on 2012-12-27
Okay gentlemen, I have solved the problem using a combination of aptitude and purge from the command line. The 34 kernel had been downloaded but not installed and was marked for installation. This was the hang up. I figured out within aptitude how to remove the downloaded 34 and then I was able to remove 23,24 and 25 with aptitude. I then used purge from the command line to remove the configuration files for those 3 kernels and rebooted. It boots up just fine so far. I looked under "Not Installed Packages" within aptitude and the 35 kernel is listed but I think I will wait until it gets updated to 36 and do it the "au to" way with aptitude like with the previous kernel updates. Thanks for the ideas and suggestions. No more 98% warning posted after I login at the server console now.

---

### Post by CharlesA on 2012-12-28
Easier way to remove (most) old kernels:

```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```

[Reference]("http://charlesa.net/scripts/linux/purgekernel.php")

---

