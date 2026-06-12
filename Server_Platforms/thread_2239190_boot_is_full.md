---
title: "boot is full"
date: 2014-08-12
forum: Server Platforms
---

### Post by daniel179 on 2014-08-12
dear all,

I'm new to the Forum and I have searched and found quite some interesting solution proposals to my problem in this forum but none helped me, so here I go:

the general problem is that my boot is full and it all started because I wanted to update my Skype (4.2. it doesn't want to connect) as well as install the newest updates of the OS. 

Here's how the space situation looks like:

daniel@daniel-SVS1512Z9EB:~$ df -h 
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  909G  803G   61G  93% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         3,9G  4,0K  3,9G   1% /dev
tmpfs                        787M  1,2M  786M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         3,9G  1,2M  3,9G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sda1                    228M  226M     0 100% /boot


As I have read that 228M should normally be enough for a /boot space as well as to increase the /boot space is a bit tricky, next thing I read was to see which kernels I have, which looks like this:

daniel@daniel-SVS1512Z9EB:~$ ls /boot/
abi-3.11.0-13-generic     config-3.8.0-19-generic       initrd.img-3.8.0-32-generic   System.map-3.8.0-32-generic
abi-3.11.0-14-generic     config-3.8.0-31-generic       lost+found                    vmlinuz-3.11.0-13-generic
abi-3.11.0-15-generic     config-3.8.0-32-generic       memtest86+.bin                vmlinuz-3.11.0-14-generic
abi-3.8.0-19-generic      grub                          memtest86+_multiboot.bin      vmlinuz-3.11.0-15-generic
abi-3.8.0-31-generic      initrd.img-3.11.0-13-generic  System.map-3.11.0-13-generic  vmlinuz-3.8.0-19-generic
abi-3.8.0-32-generic      initrd.img-3.11.0-14-generic  System.map-3.11.0-14-generic  vmlinuz-3.8.0-31-generic
config-3.11.0-13-generic  initrd.img-3.11.0-15-generic  System.map-3.11.0-15-generic  vmlinuz-3.8.0-32-generic
config-3.11.0-14-generic  initrd.img-3.8.0-19-generic   System.map-3.8.0-19-generic
config-3.11.0-15-generic  initrd.img-3.8.0-31-generic   System.map-3.8.0-31-generic

as well as:

total 224112
drwxr-xr-x  4 root root     2048 Aug 12 17:41 .
drwxr-xr-x 23 root root     4096 Aug 12 17:41 ..
-rw-r--r--  1 root root  1006439 Okt 23  2013 abi-3.11.0-13-generic
-rw-r--r--  1 root root  1006439 Nov 12  2013 abi-3.11.0-14-generic
-rw-r--r--  1 root root  1006496 Dez  9  2013 abi-3.11.0-15-generic
-rw-r--r--  1 root root   918917 Mai  1  2013 abi-3.8.0-19-generic
-rw-r--r--  1 root root   919745 Sep 10  2013 abi-3.8.0-31-generic
-rw-r--r--  1 root root   919745 Okt  2  2013 abi-3.8.0-32-generic
-rw-r--r--  1 root root   163255 Okt 23  2013 config-3.11.0-13-generic
-rw-r--r--  1 root root   163255 Nov 12  2013 config-3.11.0-14-generic
-rw-r--r--  1 root root   163245 Dez  9  2013 config-3.11.0-15-generic
-rw-r--r--  1 root root   154942 Mai  1  2013 config-3.8.0-19-generic
-rw-r--r--  1 root root   154960 Sep 10  2013 config-3.8.0-31-generic
-rw-r--r--  1 root root   154961 Okt  2  2013 config-3.8.0-32-generic
drwxr-xr-x  5 root root     1024 Jan 18  2014 grub
-rw-r--r--  1 root root 26820066 Nov 27  2013 initrd.img-3.11.0-13-generic
-rw-r--r--  1 root root 26825891 Dez 22  2013 initrd.img-3.11.0-14-generic
-rw-r--r--  1 root root 27013824 Jan 18  2014 initrd.img-3.11.0-15-generic
-rw-r--r--  1 root root 32026464 Sep 28  2013 initrd.img-3.8.0-19-generic
-rw-r--r--  1 root root 32097611 Sep 28  2013 initrd.img-3.8.0-31-generic
-rw-r--r--  1 root root 24683897 Okt 25  2013 initrd.img-3.8.0-32-generic
drwxr-xr-x  2 root root    12288 Sep 28  2013 lost+found
-rw-r--r--  1 root root   176500 Jun 17  2013 memtest86+.bin
-rw-r--r--  1 root root   178680 Jun 17  2013 memtest86+_multiboot.bin
-rw-------  1 root root  3286187 Okt 23  2013 System.map-3.11.0-13-generic
-rw-------  1 root root  3286278 Nov 12  2013 System.map-3.11.0-14-generic
-rw-------  1 root root  3293845 Dez  9  2013 System.map-3.11.0-15-generic
-rw-------  1 root root  3060094 Mai  1  2013 System.map-3.8.0-19-generic
-rw-------  1 root root  3062541 Sep 10  2013 System.map-3.8.0-31-generic
-rw-------  1 root root  3062477 Okt  2  2013 System.map-3.8.0-32-generic
-rw-------  1 root root  5600496 Okt 23  2013 vmlinuz-3.11.0-13-generic
-rw-------  1 root root  5601072 Nov 12  2013 vmlinuz-3.11.0-14-generic
-rw-------  1 root root  5631184 Dez  9  2013 vmlinuz-3.11.0-15-generic
-rw-------  1 root root  5356528 Mai  1  2013 vmlinuz-3.8.0-19-generic
-rw-------  1 root root  5362320 Sep 10  2013 vmlinuz-3.8.0-31-generic
-rw-------  1 root root  5363184 Okt  2  2013 vmlinuz-3.8.0-32-generic


In other threads they then go on to propose to remove some of the old kernels, which for example I'm trying to do as a test with one of the older kernels:

daniel@daniel-SVS1512Z9EB:~$ sudo apt-get purge linux-image-3.8.0-19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.8.0-19-generic' for regex 'linux-image-3.8.0-19'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.11.0-19-generic : Depends: linux-image-3.11.0-19-generic but it is not going to be installed
 linux-image-extra-3.11.0-26-generic : Depends: linux-image-3.11.0-26-generic but it is not going to be installed
 linux-image-extra-3.8.0-19-generic : Depends: linux-image-3.8.0-19-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.11.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

If I'm trying to do the apt-get-f install this is what I'm getting:

daniel@daniel-SVS1512Z9EB:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  openjdk-7-jre-lib
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-image-3.11.0-19-generic linux-image-3.11.0-26-generic
Suggested packages:
  fdutils linux-doc-3.11.0 linux-source-3.11.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.11.0-19-generic linux-image-3.11.0-26-generic
0 upgraded, 2 newly installed, 0 to remove and 272 not upgraded.
5 not fully installed or removed.
Need to get 0 B/28,9 MB of archives.
After this operation, 79,8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 428373 files and directories currently installed.)
Unpacking linux-image-3.11.0-26-generic (from .../linux-image-3.11.0-26-generic_3.11.0-26.45_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.11.0-26-generic_3.11.0-26.45_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.11.0-26-generic' to '/boot/System.map-3.11.0-26-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
Unpacking linux-image-3.11.0-19-generic (from .../linux-image-3.11.0-19-generic_3.11.0-19.33_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.11.0-19-generic_3.11.0-19.33_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.11.0-19-generic' to '/boot/System.map-3.11.0-19-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.11.0-26-generic_3.11.0-26.45_amd64.deb
 /var/cache/apt/archives/linux-image-3.11.0-19-generic_3.11.0-19.33_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


So here it also says there's no space left. 

Any solutions you propose how I can actually free up some space on /boot in this situation?

Sorry for being so long, but just though better to give a bit more info and get it done than less.

Thanks a lot in advance!

Daniel

---

### Post by sandyd on 2014-08-12
-rw-r--r-- 1 root root 1006439 Okt 23 2013 abi-3.11.0-13-generic
-rw-r--r-- 1 root root 1006439 Nov 12 2013 abi-3.11.0-14-generic
-rw-r--r-- 1 root root 1006496 Dez 9 2013 abi-3.11.0-15-generic
-rw-r--r-- 1 root root 918917 Mai 1 2013 abi-3.8.0-19-generic
-rw-r--r-- 1 root root 919745 Sep 10 2013 abi-3.8.0-31-generic

Your newest kernel is 3.11.0-15-generic.
Assuming that kernel actually works,

Lets remove everything else:
```

apt-get purge linux-image-3.11.0-13-generic linux-image-3.11.0-14-generic linux-image-3.8.0-19-generic linux-image-3.8.0-31-generic
apt-get autoremove #CHECK REMOVALS CAREFULLY.

```

---

### Post by daniel179 on 2014-08-12
Thanks for the quick suggestion! Understood what you're proposing.

When I put in the first command as root I get this:

daniel@daniel-SVS1512Z9EB:~$ sudo apt-get purge linux-image-3.11.0-13-generic linux-image-3.11.0-14-generic linux-image-3.8.0-19-generic linux-image-3.8.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.11.0-13-generic : Depends: linux-image-3.11.0-13-generic but it is not going to be installed
 linux-image-extra-3.11.0-14-generic : Depends: linux-image-3.11.0-14-generic but it is not going to be installed
 linux-image-extra-3.11.0-19-generic : Depends: linux-image-3.11.0-19-generic but it is not going to be installed
 linux-image-extra-3.11.0-26-generic : Depends: linux-image-3.11.0-26-generic but it is not going to be installed
 linux-image-extra-3.8.0-19-generic : Depends: linux-image-3.8.0-19-generic but it is not going to be installed
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.11.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

second command produces this:

daniel@daniel-SVS1512Z9EB:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.11.0-19-generic : Depends: linux-image-3.11.0-19-generic but it is not installed
 linux-image-extra-3.11.0-26-generic : Depends: linux-image-3.11.0-26-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.11.0-26-generic but it is not installed
E: Unmet dependencies. Try using -f.



Any further steps I could take?

Thanks again!

---

### Post by daniel179 on 2014-08-15
anyone got another hint?

thx

---

### Post by TheFu on 2014-08-16
Perhaps using **dpkg** to remove enough kernels so that **apt-get -f install** can work is needed? I've never tried it - just a thought.

Also - after you get that solved, cleaning up kernels more often would be smart - **aptitude** seems to handle this better than apt-get - or you could find/write a script like me.

OTOH, I've never let this become an issue on more recent system. I vaguely remember being burned with 10.04 systems and started a weekly kernel cleanup since then.

---

### Post by oldfred on 2014-08-16
I think any use of dpkg wants to update which includes a new kernel. And since you do not have room it will not run. 

The 3.8 kernels are probably from a previous version. Did you upgrade and not houseclean. Those 3.8 versions may not even be in your current dpkg list to easily uninstall. Then you have to manually delete, but that just moves kernels to root's trash still using space in /boot, and even with sudo you may not be able to empty trash. You may have to change ownership to allow you to eventually make space.
       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Using synaptic:
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

---

### Post by TheFu on 2014-08-16
Server forum, CLI only is my assumption. No GUI, no synaptic.

dpkg doesn't get hung up on dependencies like aptitude/apt-get do, that's why it was suggested.  As an example on one of my systems:
```
$ sudo dpkg -r linux-image-3.2.0-65-generic-pae 
(Reading database ... 339697 files and directories currently installed.)
Removing linux-image-3.2.0-65-generic-pae (3.2.0-65.99) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-65-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```
It does enough, but not TOO much with the package system.

---

