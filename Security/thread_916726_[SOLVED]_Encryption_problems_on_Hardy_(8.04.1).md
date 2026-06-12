---
title: "[SOLVED] Encryption problems on Hardy (8.04.1)"
date: 2008-09-11
forum: Security
---

### Post by tristicles on 2008-09-11
Hi there. First post here. Hope something good comes of it! Apologies if this is available in another thread. I couldn't see anything. If so, a pointer in the right direction would be appreciated.

I've been using Ubuntu since Feisty and was starting to feel quite adept with it. This has really blown the wind out of my sails. Anyway, the problem...

I've got a laptop that I want/have to encrypt. I've sliced up the hard drive as follows:

Location   Type      Mount            Size  Encrypted?
------------------------------------------------------
/dev/sda1  primary   /boot          250 MB      N
/dev/sda2  primary   swap             4 GB      Y
/dev/sda3  primary   /               20 GB      Y
/dev/sda5  extended  /home           10 GB      Y
/dev/sda6  extended  /media/data  40ish GB      Y

I set it up using [Stephan Jau's instructions on howtoforge.org]("http://www.howtoforge.org/encrypting-the-system-manually-upon-installation-ubuntu8.04"). This seems to work fine. I also ran through the steps of using a key file to unlock partitions which is linked to on P4 of the guide. I've shutdown and restarted a few times and it seems to work OK. It prompts me for the key for / and the swap partition which grates a bit. I'm sure I entered the details for the swap partition in the key file but that doesn't seem to work. Do I have to do something else with swap files?

Anyway, after a few boots, I let the system update go through. There were 111 of them, totaling 114MB. After a shutdown and restart, it starts to read the boot menu but doesn't prompt for any pass phrases. The Ubuntu splash screen appears with the bouncing orange bar for ages. Eventually, I get to the "BusyBox v1.3.3" shell with an "(initramfs)" prompt. Obviously something's seriously wrong here!! Upon doing an "ls" there's no boot folder. That must mean that I'm now looking at /dev/sda3 mounted as /, but it hasn't linked /dev/sda1 as /boot.

I found an article about grub sometimes changing the boot info in /boot/grub/menu.lst. The three entries at the end all read (hd0,0) before the trouble. After swapping to a live CD, mounting /dev/sda1 and having a look, they still do now.

Any suggestions? :o)

---

### Post by tristicles on 2008-09-11
Additional:

It's obviously reading /boot/grub/menu.lst as I can press esc to see the menu and change boot options (not that I've got a clue what to do!!!)

I'm not 100% sure on this, but shouldn't I see entries for the original 2.6.24-16 kernel as well as the updated 2.6.24-19 one? I can only see the latter. The original has gone.

---

### Post by hyper_ch on 2008-09-11
what do you have swap encrypted with a password? In my guide I don't do that ;)

Can you manually unlock the encrypted partitions? In the busybox run:

```

mkdir /tmp
cryptsetup luksOpen /dev/sda5 crypto_home
mount /dev/mapper/crypto_home /tmp

```

Does that unlock the home partition and mount it in /tmp?

---

### Post by tristicles on 2008-09-11
Got an error message now. When I go through the recovery option, it stops saying:

[COLOR="DarkRed"]Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/sda3_crypt does not exist. Dropping to a shell![/COLOR]

All the mappings between crypttab and fstab were working fine before the system update. Just wish I could work out which one has done this to me!!!

---

### Post by hyper_ch on 2008-09-11
ok, that looks now fun... in the busybox post the output of

```

fdisk -l

```
```

ls -al /dev/disk/by-uuid

```
```

cat /etc/fstab
[/cat]
[code]
cat /etc/crypttab

```

and put each output into [noparse]```

```[/noparse] brackets.

---

### Post by tristicles on 2008-09-11
Hi hyper_ch. Thanks for your help here.

Your first message:
When I enter cryptsetup luksOpen /dev/sda5 crypto_home, it asks for the passphrase. Unfortunately, I get this error message.
```

[COLOR="DarkRed"]Failed to set up dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda5 contains at least 258 sectors.
Failed to read from key storage
Command failed: No key available with this passphrase[/COLOR]

```
I tried it twice. Just in case I fluffed typing the phrase in.

Your second message:
```

fdisk -l
[COLOR="DarkRed"]/bin/sh: fdisk: not found[/COLOR]

```

```

ls -al /dev/disk/by-uuid
[COLOR="Blue"]lrwxrwxrwx 1 0 0 10 f3ad4409-b769-4afb-b5f4-6c726feeb99f -> ../../sda1
lrwxrwxrwx 1 0 0 10 0e667500-349c-438d-a7b5-723306e81f5f -> ../../sda2
lrwxrwxrwx 1 0 0 10 7ffca021-b865-404c-b25a-9a9acc006a9b -> ../../sda3
lrwxrwxrwx 1 0 0 10 6b1f1dc2-ee48-4bae-ab7c-88794ee3e9d6 -> ../../sda5
lrwxrwxrwx 1 0 0 10 f0ac37bf-9232-4f50-ae7a-4cb66d3c93fc -> ../../sda6
drwxr-xr-x 6 0 0 120 ..
drwxr-xr-x 2 0 0 140 .
[/COLOR]

```


```

cat /etc/fstab
[COLOR="DarkRed"]cat: /etc/fstab: No such file or directory[/COLOR]

```

```

cat /etc/crypttab
[COLOR="DarkRed"]cat: /etc/crypttab: No such file or directory[/COLOR]

```

The fact that it's not seeing the /etc files leads me to believe that it's not /dev/sda3 that I'm seeing mounted as /

---

### Post by hyper_ch on 2008-09-11
that was to be expected.... hmmm, problem seems that crypto-modules aren't being loaded in the initramfs...

Run the Desktop cd, then load those modules:

```

modprobe aes dm_mod dm-crypt sha256

```

If that gives errors then you first need to install some stuff:
```

apt-get install cryptsetup hashalot

```

If you have successfully loaded the modules, then try to mount the home dir again.

---

### Post by tristicles on 2008-09-11
```

ubuntu@ubuntu:~$ sudo apt-get install cryptsetup hashalot
[COLOR="DarkRed"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hashalot is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package hashalot has no installation candidate[/COLOR]

```

Another example of my inexperience here!! Do I have to add another software source for hashalot? Or do I not need to. Modprobe output below...

```

ubuntu@ubuntu:~$ sudo modprobe aes dm_mod dm-crypt sha256
[COLOR="DarkRed"]WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting geode_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/geode-aes.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting aes_generic (/lib/modules/2.6.24-19-generic/kernel/crypto/aes_generic.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting aes_i586 (/lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/COLOR]

```

---

### Post by hyper_ch on 2008-09-11
well, install cryptsetup alone then (not sure if hashalot is still required). Also try then to mount the modules one after the other.

---

### Post by tristicles on 2008-09-11
Hmmmmmm. Starting to think this system has got something against me!!! :)

```

ubuntu@ubuntu:~$ sudo apt-get install cryptsetup
[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cryptsetup
0 upgraded, 1 newly installed, 0 to remove and 123 not upgraded.
Need to get 88.7kB of archives.
After this operation, 414kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/main cryptsetup 2:1.0.5-2ubuntu12 [88.7kB]
Fetched 88.7kB in 0s (984kB/s)  
Selecting previously deselected package cryptsetup.
(Reading database ... 98423 files and directories currently installed.)
Unpacking cryptsetup (from .../cryptsetup_2%3a1.0.5-2ubuntu12_i386.deb) ...
Setting up cryptsetup (2:1.0.5-2ubuntu12) ...[/COLOR]
[COLOR="DarkRed"]update-initramfs is disabled since running on a live CD[/COLOR]

```

Modprobe gives the same output

```

ubuntu@ubuntu:~$ sudo modprobe aes dm_mod dm-crypt sha256
[COLOR="DarkRed"]WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting geode_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/geode-aes.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting aes_generic (/lib/modules/2.6.24-19-generic/kernel/crypto/aes_generic.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting aes_i586 (/lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/COLOR]

```

No joy mounting the partition
```

ubuntu@ubuntu:~$ mkdir ~/crypt_home
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 /home/ubuntu/crypto_home
Enter LUKS passphrase: 
[COLOR="DarkRed"]Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda5 contains at least 258 sectors.
Failed to read from key storage
Command failed: No key available with this passphrase.[/COLOR]

```

---

### Post by hyper_ch on 2008-09-11
as said, try to load the modules individually

---

### Post by tristicles on 2008-09-11
Ah ha. We're rocking and rolling now. Just been faffing with this live USB stick and have enabled additional software sources.
```

ubuntu@ubuntu:~$ sudo apt-get install hashalot
[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  hashalot
0 upgraded, 1 newly installed, 0 to remove and 123 not upgraded.
Need to get 16.3kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/universe hashalot 0.3-5 [16.3kB]
Fetched 16.3kB in 0s (374kB/s)  
Selecting previously deselected package hashalot.
(Reading database ... 98837 files and directories currently installed.)
Unpacking hashalot (from .../hashalot_0.3-5_i386.deb) ...
Setting up hashalot (0.3-5) ...[/COLOR]

ubuntu@ubuntu:~$ sudo apt-get install cryptsetup
[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 123 not upgraded.[/COLOR]

```

Bugger!
```

ubuntu@ubuntu:~$ modprobe aes dm_mod dm-crypt sha256
[COLOR="Red"]WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): Operation not permitted
WARNING: Error inserting geode_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/geode-aes.ko): Operation not permitted
WARNING: Error inserting aes_generic (/lib/modules/2.6.24-19-generic/kernel/crypto/aes_generic.ko): Operation not permitted
WARNING: Error inserting aes_i586 (/lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko): Operation not permitted[/COLOR]

```

---

### Post by tristicles on 2008-09-11
Sorry. Please forgive my stupidity. What do you mean by load the modules individually? :confused:

---

### Post by tristicles on 2008-09-11
As in...
```

ubuntu@ubuntu:~$ sudo modprobe aes
[COLOR="Red"]WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): No such device[/COLOR]
ubuntu@ubuntu:~$ sudo modprobe dm_mod
ubuntu@ubuntu:~$ sudo modprobe dm-crypt
ubuntu@ubuntu:~$ sudo modprobe sha256
[COLOR="Red"]WARNING: Error inserting padlock_sha (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko): No such device[/COLOR]

```
?

---

### Post by hyper_ch on 2008-09-11
I just checked here, padlock-aes.ko and padlock-sha.ko are parts of the kernel:

```

hyper@xubi:~$ apt-file search padlock-aes.ko
linux-image-2.6.24-16-386: /lib/modules/2.6.24-16-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-generic: /lib/modules/2.6.24-16-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-openvz: /lib/modules/2.6.24-16-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-rt: /lib/modules/2.6.24-16-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-server: /lib/modules/2.6.24-16-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-virtual: /lib/modules/2.6.24-16-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-xen: /lib/modules/2.6.24-16-xen/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-386: /lib/modules/2.6.24-18-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-generic: /lib/modules/2.6.24-18-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-openvz: /lib/modules/2.6.24-18-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-rt: /lib/modules/2.6.24-18-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-server: /lib/modules/2.6.24-18-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-virtual: /lib/modules/2.6.24-18-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-xen: /lib/modules/2.6.24-18-xen/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-386: /lib/modules/2.6.24-19-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-generic: /lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-openvz: /lib/modules/2.6.24-19-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-rt: /lib/modules/2.6.24-19-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-server: /lib/modules/2.6.24-19-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-virtual: /lib/modules/2.6.24-19-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-xen: /lib/modules/2.6.24-19-xen/kernel/drivers/crypto/padlock-aes.ko
hyper@xubi:~$

```

Please check if you don't have them.

---

### Post by tristicles on 2008-09-11
OK. Have got the following.

```

ubuntu@ubuntu:~$ apt-file search padlock-aes.ko
linux-image-2.6.24-16-386: /lib/modules/2.6.24-16-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-generic: /lib/modules/2.6.24-16-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-openvz: /lib/modules/2.6.24-16-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-rt: /lib/modules/2.6.24-16-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-server: /lib/modules/2.6.24-16-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-virtual: /lib/modules/2.6.24-16-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-16-xen: /lib/modules/2.6.24-16-xen/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-386: /lib/modules/2.6.24-18-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-generic: /lib/modules/2.6.24-18-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-openvz: /lib/modules/2.6.24-18-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-rt: /lib/modules/2.6.24-18-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-server: /lib/modules/2.6.24-18-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-virtual: /lib/modules/2.6.24-18-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-18-xen: /lib/modules/2.6.24-18-xen/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-386: /lib/modules/2.6.24-19-386/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-generic: /lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-openvz: /lib/modules/2.6.24-19-openvz/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-rt: /lib/modules/2.6.24-19-rt/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-server: /lib/modules/2.6.24-19-server/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-virtual: /lib/modules/2.6.24-19-virtual/kernel/drivers/crypto/padlock-aes.ko
linux-image-2.6.24-19-xen: /lib/modules/2.6.24-19-xen/kernel/drivers/crypto/padlock-aes.ko

```

I'm still running off the live cd (well, usb stick). Should I go back to the BusyBox environment to check this?

---

### Post by hyper_ch on 2008-09-11
no, not running apt-file but looking into your directories on the live cd... do you have in the /lib/modules/..../drivers/crypto folder the according files?

---

### Post by tristicles on 2008-09-11
Really sorry. Not following you 100% here :oops: (pesky linux beginners!!). Are you looking for padlock-aes.ko on the live cd? if so...

```

ubuntu@ubuntu:/$ sudo locate padlock-aes.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko

```

---

### Post by hyper_ch on 2008-09-11
and the padlock-sha.ko file have yuo also in that folder?

---

### Post by tristicles on 2008-09-11
Sorry. This must be really painful for you!!! Yes, the file is there

```

ubuntu@ubuntu:/$ ls -l /lib/modules/2.6.24-19-generic/kernel/drivers/crypto/
total 32
-rw-r--r-- 1 root root 9592 2008-06-18 18:13 geode-aes.ko
-rw-r--r-- 1 root root 9852 2008-06-18 18:13 padlock-aes.ko
-rw-r--r-- 1 root root 7476 2008-06-18 18:13 padlock-sha.ko

```

---

### Post by hyper_ch on 2008-09-11
I wonder why you can't load the modules then... hmmm

can you try to unlock the root partition as I told you before with cryptsetup ?

---

### Post by tristicles on 2008-09-11
Second time lucky.

```

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypto_home
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.
ubuntu@ubuntu:~$ sudo mount /dev/mapper/crypto_home /home/ubuntu/crypt_home/
ubuntu@ubuntu:~$ ls /home/ubuntu/crypt_home/
lost+found  tris

```

Don't think I was sudo-ing before hence why it crapped out.

---

### Post by hyper_ch on 2008-09-11
Ok, now you need to mount the boot partition /dev/sda1

```

sudo mkdir /tmp/testboot
mount /dev/sda1 /tmp/testboot

```

Now let's unpack the initramfs
```

sudo mkdir /tmp/fakeroot
cd /tmp/fakeroot
zcat /tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv
cat conf/conf.d/cryptroot

```
post the output of the cryptroot file (you did print it with cat)

---

### Post by tristicles on 2008-09-11
Not having much joy :(

```

ubuntu@ubuntu:/tmp/fakeroot$ zcat /tmp/fakeroot/initrd.img-2.6.24-19-generic | cpio -iv
gzip: /tmp/fakeroot/initrd.img-2.6.24-19-generic.gz: No such file or directory
cpio: premature end of archive

```

Do you want me to mount the encrypted root at /tmp/fakeroot? Sorry, I'm a bit of a simpleton and need these things explaining. Only been with linux since Feisty. This is my first venture into encryption.

---

### Post by hyper_ch on 2008-09-11
try

```

/tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv

```

---

### Post by tristicles on 2008-09-11
Think I've found the problem. You mentioned to create /tmp/testboot and /tmp/fakeroot. You then refer to /tmp/fakeboot. Do you mean /tmp/testboot?

---

### Post by hyper_ch on 2008-09-11
you have to folder: (1) where you are in: fakeroot and (2) where you mounted the boot partition to: fakeboot

The file you need to get and extract with this command is in the fakeboot folder.

---

### Post by tristicles on 2008-09-11
> **hyper_ch said:**
> Ok, now you need to mount the boot partition /dev/sda1

```

sudo mkdir /tmp/testboot
mount /dev/sda1 /tmp/testboot

```

Now let's unpack the initramfs
```

sudo mkdir /tmp/fakeroot
cd /tmp/fakeroot
zcat /tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv
cat conf/conf.d/cryptroot

```
post the output of the cryptroot file (you did print it with cat)

Es tud mir leid, mein Detusch sehr schlecht ist. Hier oben hast Du /tmp/**test**boot gesagt. Später, sagtest Du /tmp/**fake**boot. Sollen den Beiden dieselbe sein? Entweder fake oder test?

---

### Post by hyper_ch on 2008-09-11
in non loco-forums english should be the only language used. Further more read my last post.

---

### Post by tristicles on 2008-09-11
> **hyper_ch said:**
> you have to folder: (1) where you are in: fakeroot and (2) where you mounted the boot partition to: fakeboot

The file you need to get and extract with this command is in the fakeboot folder.

Your previous post asked me to mount /dev/sda1 in /tmp/testboot, not /tmp/fakeboot. The zcat command refers to /tmp/fakeboot which doesn't exist.

If I unmount /dev/sda1 from /tmp/testboot and remount it at /tmp/fakeboot..
```

ubuntu@ubuntu:/tmp/fakeroot$ zcat /tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv
cpio: init: Cannot open: Permission denied
init
cpio: usr: Cannot mkdir: Permission denied
usr
cpio: usr/lib: Cannot mkdir: No such file or directory
usr/lib
cpio: usr/lib/usplash: Cannot mkdir: No such file or directory
usr/lib/usplash
cpio: usr/lib/usplash/usplash-artwork.so: Cannot open: No such file or directory
usr/lib/usplash/usplash-artwork.so
cpio: scripts: Cannot mkdir: Permission denied
scripts
cpio: scripts/init-top: Cannot mkdir: No such file or directory
scripts/init-top
cpio: scripts/init-top/framebuffer: Cannot open: No such file or directory
scripts/init-top/framebuffer
cpio: scripts/init-top/console_setup: Cannot open: No such file or directory
scripts/init-top/console_setup
cpio: scripts/init-top/all_generic_ide: Cannot open: No such file or directory
scripts/init-top/all_generic_ide
cpio: scripts/init-top/brltty: Cannot open: No such file or directory
scripts/init-top/brltty
cpio: scripts/init-top/usplash: Cannot open: No such file or directory
scripts/init-top/usplash
cpio: scripts/casper-premount: Cannot mkdir: No such file or directory
scripts/casper-premount
cpio: scripts/local-premount: Cannot mkdir: No such file or directory
scripts/local-premount
cpio: scripts/local-premount/resume: Cannot open: No such file or directory
scripts/local-premount/resume
cpio: scripts/local-premount/ntfs_3g: Cannot open: No such file or directory
scripts/local-premount/ntfs_3g
cpio: scripts/nfs-bottom: Cannot mkdir: No such file or directory
scripts/nfs-bottom
cpio: scripts/nfs-premount: Cannot mkdir: No such file or directory
scripts/nfs-premount
cpio: scripts/local-bottom: Cannot mkdir: No such file or directory
scripts/local-bottom
cpio: scripts/local-bottom/cryptopensc: Cannot open: No such file or directory
scripts/local-bottom/cryptopensc
cpio: scripts/local-bottom/ntfs_3g: Cannot open: No such file or directory
scripts/local-bottom/ntfs_3g
cpio: scripts/nfs: Cannot open: No such file or directory
scripts/nfs
cpio: scripts/local: Cannot open: No such file or directory
scripts/local
cpio: scripts/nfs-top: Cannot mkdir: No such file or directory
scripts/nfs-top
cpio: scripts/nfs-top/udev: Cannot open: No such file or directory
scripts/nfs-top/udev
cpio: scripts/init-premount: Cannot mkdir: No such file or directory
scripts/init-premount
cpio: scripts/init-premount/ps3: Cannot open: No such file or directory
scripts/init-premount/ps3
cpio: scripts/init-premount/udev: Cannot open: No such file or directory
scripts/init-premount/udev
cpio: scripts/functions: Cannot open: No such file or directory
scripts/functions
cpio: scripts/init-bottom: Cannot mkdir: No such file or directory
scripts/init-bottom
cpio: scripts/init-bottom/udev: Cannot open: No such file or directory
scripts/init-bottom/udev
cpio: scripts/local-top: Cannot mkdir: No such file or directory
scripts/local-top
cpio: scripts/local-top/cryptopensc: Cannot open: No such file or directory
scripts/local-top/cryptopensc
cpio: scripts/local-top/cryptroot: Cannot open: No such file or directory
scripts/local-top/cryptroot
cpio: bin: Cannot mkdir: Permission denied
bin
cpio: bin/consolechars: Cannot open: No such file or directory
bin/consolechars
cpio: bin/mkdir: Cannot open: No such file or directory
bin/mkdir
cpio: bin/ln: Cannot open: No such file or directory
bin/ln
cpio: bin/busybox: Cannot open: No such file or directory
bin/busybox
cpio: bin/readlink: Cannot open: No such file or directory
bin/readlink
cpio: bin/true: Cannot open: No such file or directory
bin/true
cpio: bin/dd: Cannot open: No such file or directory
bin/dd
cpio: bin/nfsmount: Cannot open: No such file or directory
bin/nfsmount
cpio: bin/kbd_mode: Cannot open: No such file or directory
bin/kbd_mode
cpio: bin/mkfifo: Cannot open: No such file or directory
bin/mkfifo
cpio: bin/zcat: Cannot open: No such file or directory
bin/zcat
cpio: bin/kinit: Cannot open: No such file or directory
bin/kinit
cpio: bin/resume: Cannot open: No such file or directory
bin/resume
cpio: bin/dmesg: Cannot open: No such file or directory
bin/dmesg
cpio: bin/ntfs-3g: Cannot open: No such file or directory
bin/ntfs-3g
cpio: bin/uname: Cannot open: No such file or directory
bin/uname
cpio: bin/reboot: Cannot open: No such file or directory
bin/reboot
cpio: bin/halt: Cannot open: No such file or directory
bin/halt
cpio: bin/kinit.shared: Cannot open: No such file or directory
bin/kinit.shared
cpio: bin/loadkeys: Cannot open: No such file or directory
bin/loadkeys
cpio: bin/kill: Cannot open: No such file or directory
bin/kill
cpio: bin/fstype: Cannot open: No such file or directory
bin/fstype
cpio: bin/sh: Cannot open: No such file or directory
bin/sh
cpio: bin/sync: Cannot open: No such file or directory
bin/sync
cpio: bin/cat: Cannot open: No such file or directory
bin/cat
cpio: bin/mount: Cannot open: No such file or directory
bin/mount
cpio: bin/cpio: Cannot open: No such file or directory
bin/cpio
cpio: bin/gunzip: Cannot open: No such file or directory
bin/gunzip
cpio: bin/chroot: Cannot open: No such file or directory
bin/chroot
cpio: bin/mknod: Cannot open: No such file or directory
bin/mknod
cpio: bin/gzip: Cannot open: No such file or directory
bin/gzip
cpio: bin/insmod: Cannot open: No such file or directory
bin/insmod
cpio: bin/nuke: Cannot open: No such file or directory
bin/nuke
cpio: bin/umount: Cannot open: No such file or directory
bin/umount
cpio: bin/sleep: Cannot open: No such file or directory
bin/sleep
cpio: bin/poweroff: Cannot open: No such file or directory
bin/poweroff
cpio: bin/ipconfig: Cannot open: No such file or directory
bin/ipconfig
cpio: bin/sh.shared: Cannot open: No such file or directory
bin/sh.shared
cpio: bin/minips: Cannot open: No such file or directory
bin/minips
cpio: bin/run-init: Cannot open: No such file or directory
bin/run-init
cpio: bin/false: Cannot open: No such file or directory
bin/false
cpio: bin/pivot_root: Cannot open: No such file or directory
bin/pivot_root
cpio: etc: Cannot mkdir: Permission denied
etc
cpio: etc/console-setup: Cannot mkdir: No such file or directory
etc/console-setup
cpio: etc/console-setup/Lat15-VGA16.psf.gz: Cannot open: No such file or directory
etc/console-setup/Lat15-VGA16.psf.gz
cpio: etc/console-setup/boottime.kmap.gz: Cannot open: No such file or directory
etc/console-setup/boottime.kmap.gz
cpio: etc/modprobe.d: Cannot mkdir: No such file or directory
etc/modprobe.d
cpio: etc/modprobe.d/blacklist-framebuffer: Cannot open: No such file or directory
etc/modprobe.d/blacklist-framebuffer
cpio: etc/modprobe.d/isapnp: Cannot open: No such file or directory
etc/modprobe.d/isapnp
cpio: etc/modprobe.d/arch: Cannot mkdir: No such file or directory
etc/modprobe.d/arch
cpio: etc/modprobe.d/arch/i386: Cannot open: No such file or directory
etc/modprobe.d/arch/i386
cpio: etc/modprobe.d/lrm-video: Cannot open: No such file or directory
etc/modprobe.d/lrm-video
cpio: etc/modprobe.d/options: Cannot open: No such file or directory
etc/modprobe.d/options
cpio: etc/modprobe.d/libsane: Cannot open: No such file or directory
etc/modprobe.d/libsane
cpio: etc/modprobe.d/libpisock9: Cannot open: No such file or directory
etc/modprobe.d/libpisock9
cpio: etc/modprobe.d/blacklist-modem: Cannot open: No such file or directory
etc/modprobe.d/blacklist-modem
cpio: etc/modprobe.d/arch-aliases: Cannot open: No such file or directory
etc/modprobe.d/arch-aliases
cpio: etc/modprobe.d/blacklist: Cannot open: No such file or directory
etc/modprobe.d/blacklist
cpio: etc/modprobe.d/nvidia-kernel-nkc: Cannot open: No such file or directory
etc/modprobe.d/nvidia-kernel-nkc
cpio: etc/modprobe.d/fuse: Cannot open: No such file or directory
etc/modprobe.d/fuse
cpio: etc/modprobe.d/aliases: Cannot open: No such file or directory
etc/modprobe.d/aliases
cpio: etc/modprobe.d/blacklist-oss: Cannot open: No such file or directory
etc/modprobe.d/blacklist-oss
cpio: etc/modprobe.d/blacklist-watchdog: Cannot open: No such file or directory
etc/modprobe.d/blacklist-watchdog
cpio: etc/modprobe.d/toshiba_acpi.modprobe: Cannot open: No such file or directory
etc/modprobe.d/toshiba_acpi.modprobe
cpio: etc/modprobe.d/alsa-base: Cannot open: No such file or directory
etc/modprobe.d/alsa-base
cpio: etc/udev: Cannot mkdir: No such file or directory
etc/udev
cpio: etc/udev/udev.conf: Cannot open: No such file or directory
etc/udev/udev.conf
cpio: etc/udev/rules.d: Cannot mkdir: No such file or directory
etc/udev/rules.d
cpio: etc/udev/rules.d/05-udev-early.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-udev-early.rules
cpio: etc/udev/rules.d/61-persistent-storage-edd.rules: Cannot open: No such file or directory
etc/udev/rules.d/61-persistent-storage-edd.rules
cpio: etc/udev/rules.d/95-udev-late.rules: Cannot open: No such file or directory
etc/udev/rules.d/95-udev-late.rules
cpio: etc/udev/rules.d/65-dmsetup.rules: Cannot open: No such file or directory
etc/udev/rules.d/65-dmsetup.rules
cpio: etc/udev/rules.d/20-names.rules: Cannot open: No such file or directory
etc/udev/rules.d/20-names.rules
cpio: etc/udev/rules.d/40-basic-permissions.rules: Cannot open: No such file or directory
etc/udev/rules.d/40-basic-permissions.rules
cpio: etc/udev/rules.d/05-options.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-options.rules
cpio: etc/udev/rules.d/90-modprobe.rules: Cannot open: No such file or directory
etc/udev/rules.d/90-modprobe.rules
cpio: etc/udev/rules.d/80-programs.rules: Cannot open: No such file or directory
etc/udev/rules.d/80-programs.rules
cpio: etc/udev/rules.d/60-persistent-storage.rules: Cannot open: No such file or directory
etc/udev/rules.d/60-persistent-storage.rules
cpio: etc/usplash.conf: Cannot open: No such file or directory
etc/usplash.conf
cpio: etc/default: Cannot mkdir: No such file or directory
etc/default
cpio: etc/default/console-setup: Cannot open: No such file or directory
etc/default/console-setup
cpio: sbin: Cannot mkdir: Permission denied
sbin
cpio: sbin/depmod: Cannot open: No such file or directory
sbin/depmod
cpio: sbin/udevd: Cannot open: No such file or directory
sbin/udevd
cpio: sbin/usplash_write: Cannot open: No such file or directory
sbin/usplash_write
cpio: sbin/cryptsetup: Cannot open: No such file or directory
sbin/cryptsetup
cpio: sbin/modprobe: Cannot open: No such file or directory
sbin/modprobe
cpio: sbin/rmmod: Cannot open: No such file or directory
sbin/rmmod
cpio: sbin/mount.ntfs: Cannot open: No such file or directory
sbin/mount.ntfs
cpio: sbin/udevadm: Cannot open: No such file or directory
sbin/udevadm
cpio: sbin/brltty-setup: Cannot open: No such file or directory
sbin/brltty-setup
cpio: sbin/mount.ntfs-3g: Cannot open: No such file or directory
sbin/mount.ntfs-3g
cpio: sbin/mount.fuse: Cannot open: No such file or directory
sbin/mount.fuse
cpio: sbin/pkill: Cannot open: No such file or directory
sbin/pkill
cpio: sbin/usplash: Cannot open: No such file or directory
sbin/usplash
cpio: sbin/dmsetup: Cannot open: No such file or directory
sbin/dmsetup
cpio: conf: Cannot mkdir: Permission denied
conf
cpio: conf/arch.conf: Cannot open: No such file or directory
conf/arch.conf
cpio: conf/conf.d: Cannot mkdir: No such file or directory
conf/conf.d
cpio: conf/conf.d/resume: Cannot open: No such file or directory
conf/conf.d/resume
cpio: conf/modules: Cannot open: No such file or directory
conf/modules
cpio: conf/initramfs.conf: Cannot open: No such file or directory
conf/initramfs.conf
cpio: modules: Cannot mkdir: Permission denied
modules
cpio: lib: Cannot mkdir: Permission denied
lib
cpio: lib/libusplash.so.0: Cannot open: No such file or directory
lib/libusplash.so.0
cpio: lib/libgcrypt.so.11: Cannot open: No such file or directory
lib/libgcrypt.so.11
cpio: lib/libdl.so.2: Cannot open: No such file or directory
lib/libdl.so.2
cpio: lib/ld-linux.so.2: Cannot open: No such file or directory
lib/ld-linux.so.2
cpio: lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so: Cannot open: No such file or directory
lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so
cpio: lib/firmware: Cannot mkdir: No such file or directory
lib/firmware
cpio: lib/firmware/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/firmware/2.6.24-19-generic
cpio: lib/firmware/2.6.24-19-generic/ql2100_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2100_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2400_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2400_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2300_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2300_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2200_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2200_fw.bin
cpio: lib/firmware/2.6.24-19-generic/aic94xx-seq.fw: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/aic94xx-seq.fw
cpio: lib/firmware/2.6.24-19-generic/ql2322_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2322_fw.bin
cpio: lib/libpthread.so.0: Cannot open: No such file or directory
lib/libpthread.so.0
cpio: lib/libsepol.so.1: Cannot open: No such file or directory
lib/libsepol.so.1
cpio: lib/libproc-3.2.7.so: Cannot open: No such file or directory
lib/libproc-3.2.7.so
cpio: lib/librt.so.1: Cannot open: No such file or directory
lib/librt.so.1
cpio: lib/libctutils.so.0: Cannot open: No such file or directory
lib/libctutils.so.0
cpio: lib/libpopt.so.0: Cannot open: No such file or directory
lib/libpopt.so.0
cpio: lib/libcfont.so.0: Cannot open: No such file or directory
lib/libcfont.so.0
cpio: lib/udev: Cannot mkdir: No such file or directory
lib/udev
cpio: lib/udev/scsi_id: Cannot open: No such file or directory
lib/udev/scsi_id
cpio: lib/udev/pnp_modules: Cannot open: No such file or directory
lib/udev/pnp_modules
cpio: lib/udev/firmware_helper: Cannot open: No such file or directory
lib/udev/firmware_helper
cpio: lib/udev/usb_device_name: Cannot open: No such file or directory
lib/udev/usb_device_name
cpio: lib/udev/vol_id: Cannot open: No such file or directory
lib/udev/vol_id
cpio: lib/udev/watershed: Cannot open: No such file or directory
lib/udev/watershed
cpio: lib/udev/path_id: Cannot open: No such file or directory
lib/udev/path_id
cpio: lib/udev/ata_id: Cannot open: No such file or directory
lib/udev/ata_id
cpio: lib/udev/dvb_device_name: Cannot open: No such file or directory
lib/udev/dvb_device_name
cpio: lib/udev/ide_media: Cannot open: No such file or directory
lib/udev/ide_media
cpio: lib/udev/usb_id: Cannot open: No such file or directory
lib/udev/usb_id
cpio: lib/udev/edd_id: Cannot open: No such file or directory
lib/udev/edd_id
cpio: lib/udev/vio_type: Cannot open: No such file or directory
lib/udev/vio_type
cpio: lib/libconsole.so.0: Cannot open: No such file or directory
lib/libconsole.so.0
cpio: lib/libfuse.so.2: Cannot open: No such file or directory
lib/libfuse.so.2
cpio: lib/libdevmapper.so.1.02.1: Cannot open: No such file or directory
lib/libdevmapper.so.1.02.1
cpio: lib/libc.so.6: Cannot open: No such file or directory
lib/libc.so.6
cpio: lib/libntfs-3g.so.23: Cannot open: No such file or directory
lib/libntfs-3g.so.23
cpio: lib/modules: Cannot mkdir: No such file or directory
lib/modules
cpio: lib/modules/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic
cpio: lib/modules/2.6.24-19-generic/initrd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/initrd
cpio: lib/modules/2.6.24-19-generic/kernel: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel
cpio: lib/modules/2.6.24-19-generic/kernel/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko
cpio: lib/modules/2.6.24-19-generic/kernel/arch: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/lib: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib
cpio: lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko
cpio: lib/libselinux.so.1: Cannot open: No such file or directory
lib/libselinux.so.1
cpio: lib/libx86.so.1: Cannot open: No such file or directory
lib/libx86.so.1
cpio: lib/libuuid.so.1: Cannot open: No such file or directory
lib/libuuid.so.1
cpio: lib/libvolume_id.so.0: Cannot open: No such file or directory
lib/libvolume_id.so.0
cpio: lib/brltty: Cannot mkdir: No such file or directory
lib/brltty
cpio: lib/brltty/brltty.sh: Cannot open: No such file or directory
lib/brltty/brltty.sh
cpio: lib/libgpg-error.so.0: Cannot open: No such file or directory
lib/libgpg-error.so.0
cpio: var: Cannot mkdir: Permission denied
var
cpio: var/run: Cannot mkdir: No such file or directory
var/run
cpio: lib/modules/2.6.24-19-generic/initrd/vesafb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/initrd/vesafb.ko
42079 blocks

```

No files have been created in /tmp/fakeroot

```

ubuntu@ubuntu:/tmp/fakeroot$ cat conf/conf.d/cryptroot
cat: conf/conf.d/cryptroot: No such file or directory
ubuntu@ubuntu:/tmp/fakeroot$ ls -l
total 0

```

Same happens when I execute the command with "sudo"

```

ubuntu@ubuntu:/tmp/fakeroot$ sudo zcat /tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv
.
cpio: init: Cannot open: Permission denied
init
cpio: usr: Cannot mkdir: Permission denied
usr
cpio: usr/lib: Cannot mkdir: No such file or directory
usr/lib
cpio: usr/lib/usplash: Cannot mkdir: No such file or directory
usr/lib/usplash
cpio: usr/lib/usplash/usplash-artwork.so: Cannot open: No such file or directory
usr/lib/usplash/usplash-artwork.so
cpio: scripts: Cannot mkdir: Permission denied
scripts
cpio: scripts/init-top: Cannot mkdir: No such file or directory
scripts/init-top
cpio: scripts/init-top/framebuffer: Cannot open: No such file or directory
scripts/init-top/framebuffer
cpio: scripts/init-top/console_setup: Cannot open: No such file or directory
scripts/init-top/console_setup
cpio: scripts/init-top/all_generic_ide: Cannot open: No such file or directory
scripts/init-top/all_generic_ide
cpio: scripts/init-top/brltty: Cannot open: No such file or directory
scripts/init-top/brltty
cpio: scripts/init-top/usplash: Cannot open: No such file or directory
scripts/init-top/usplash
cpio: scripts/casper-premount: Cannot mkdir: No such file or directory
scripts/casper-premount
cpio: scripts/local-premount: Cannot mkdir: No such file or directory
scripts/local-premount
cpio: scripts/local-premount/resume: Cannot open: No such file or directory
scripts/local-premount/resume
cpio: scripts/local-premount/ntfs_3g: Cannot open: No such file or directory
scripts/local-premount/ntfs_3g
cpio: scripts/nfs-bottom: Cannot mkdir: No such file or directory
scripts/nfs-bottom
cpio: scripts/nfs-premount: Cannot mkdir: No such file or directory
scripts/nfs-premount
cpio: scripts/local-bottom: Cannot mkdir: No such file or directory
scripts/local-bottom
cpio: scripts/local-bottom/cryptopensc: Cannot open: No such file or directory
scripts/local-bottom/cryptopensc
cpio: scripts/local-bottom/ntfs_3g: Cannot open: No such file or directory
scripts/local-bottom/ntfs_3g
cpio: scripts/nfs: Cannot open: No such file or directory
scripts/nfs
cpio: scripts/local: Cannot open: No such file or directory
scripts/local
cpio: scripts/nfs-top: Cannot mkdir: No such file or directory
scripts/nfs-top
cpio: scripts/nfs-top/udev: Cannot open: No such file or directory
scripts/nfs-top/udev
cpio: scripts/init-premount: Cannot mkdir: No such file or directory
scripts/init-premount
cpio: scripts/init-premount/ps3: Cannot open: No such file or directory
scripts/init-premount/ps3
cpio: scripts/init-premount/udev: Cannot open: No such file or directory
scripts/init-premount/udev
cpio: scripts/functions: Cannot open: No such file or directory
scripts/functions
cpio: scripts/init-bottom: Cannot mkdir: No such file or directory
scripts/init-bottom
cpio: scripts/init-bottom/udev: Cannot open: No such file or directory
scripts/init-bottom/udev
cpio: scripts/local-top: Cannot mkdir: No such file or directory
scripts/local-top
cpio: scripts/local-top/cryptopensc: Cannot open: No such file or directory
scripts/local-top/cryptopensc
cpio: scripts/local-top/cryptroot: Cannot open: No such file or directory
scripts/local-top/cryptroot
cpio: bin: Cannot mkdir: Permission denied
bin
cpio: bin/consolechars: Cannot open: No such file or directory
bin/consolechars
cpio: bin/mkdir: Cannot open: No such file or directory
bin/mkdir
cpio: bin/ln: Cannot open: No such file or directory
bin/ln
cpio: bin/busybox: Cannot open: No such file or directory
bin/busybox
cpio: bin/readlink: Cannot open: No such file or directory
bin/readlink
cpio: bin/true: Cannot open: No such file or directory
bin/true
cpio: bin/dd: Cannot open: No such file or directory
bin/dd
cpio: bin/nfsmount: Cannot open: No such file or directory
bin/nfsmount
cpio: bin/kbd_mode: Cannot open: No such file or directory
bin/kbd_mode
cpio: bin/mkfifo: Cannot open: No such file or directory
bin/mkfifo
cpio: bin/zcat: Cannot open: No such file or directory
bin/zcat
cpio: bin/kinit: Cannot open: No such file or directory
bin/kinit
cpio: bin/resume: Cannot open: No such file or directory
bin/resume
cpio: bin/dmesg: Cannot open: No such file or directory
bin/dmesg
cpio: bin/ntfs-3g: Cannot open: No such file or directory
bin/ntfs-3g
cpio: bin/uname: Cannot open: No such file or directory
bin/uname
cpio: bin/reboot: Cannot open: No such file or directory
bin/reboot
cpio: bin/halt: Cannot open: No such file or directory
bin/halt
cpio: bin/kinit.shared: Cannot open: No such file or directory
bin/kinit.shared
cpio: bin/loadkeys: Cannot open: No such file or directory
bin/loadkeys
cpio: bin/kill: Cannot open: No such file or directory
bin/kill
cpio: bin/fstype: Cannot open: No such file or directory
bin/fstype
cpio: bin/sh: Cannot open: No such file or directory
bin/sh
cpio: bin/sync: Cannot open: No such file or directory
bin/sync
cpio: bin/cat: Cannot open: No such file or directory
bin/cat
cpio: bin/mount: Cannot open: No such file or directory
bin/mount
cpio: bin/cpio: Cannot open: No such file or directory
bin/cpio
cpio: bin/gunzip: Cannot open: No such file or directory
bin/gunzip
cpio: bin/chroot: Cannot open: No such file or directory
bin/chroot
cpio: bin/mknod: Cannot open: No such file or directory
bin/mknod
cpio: bin/gzip: Cannot open: No such file or directory
bin/gzip
cpio: bin/insmod: Cannot open: No such file or directory
bin/insmod
cpio: bin/nuke: Cannot open: No such file or directory
bin/nuke
cpio: bin/umount: Cannot open: No such file or directory
bin/umount
cpio: bin/sleep: Cannot open: No such file or directory
bin/sleep
cpio: bin/poweroff: Cannot open: No such file or directory
bin/poweroff
cpio: bin/ipconfig: Cannot open: No such file or directory
bin/ipconfig
cpio: bin/sh.shared: Cannot open: No such file or directory
bin/sh.shared
cpio: bin/minips: Cannot open: No such file or directory
bin/minips
cpio: bin/run-init: Cannot open: No such file or directory
bin/run-init
cpio: bin/false: Cannot open: No such file or directory
bin/false
cpio: bin/pivot_root: Cannot open: No such file or directory
bin/pivot_root
cpio: etc: Cannot mkdir: Permission denied
etc
cpio: etc/console-setup: Cannot mkdir: No such file or directory
etc/console-setup
cpio: etc/console-setup/Lat15-VGA16.psf.gz: Cannot open: No such file or directory
etc/console-setup/Lat15-VGA16.psf.gz
cpio: etc/console-setup/boottime.kmap.gz: Cannot open: No such file or directory
etc/console-setup/boottime.kmap.gz
cpio: etc/modprobe.d: Cannot mkdir: No such file or directory
etc/modprobe.d
cpio: etc/modprobe.d/blacklist-framebuffer: Cannot open: No such file or directory
etc/modprobe.d/blacklist-framebuffer
cpio: etc/modprobe.d/isapnp: Cannot open: No such file or directory
etc/modprobe.d/isapnp
cpio: etc/modprobe.d/arch: Cannot mkdir: No such file or directory
etc/modprobe.d/arch
cpio: etc/modprobe.d/arch/i386: Cannot open: No such file or directory
etc/modprobe.d/arch/i386
cpio: etc/modprobe.d/lrm-video: Cannot open: No such file or directory
etc/modprobe.d/lrm-video
cpio: etc/modprobe.d/options: Cannot open: No such file or directory
etc/modprobe.d/options
cpio: etc/modprobe.d/libsane: Cannot open: No such file or directory
etc/modprobe.d/libsane
cpio: etc/modprobe.d/libpisock9: Cannot open: No such file or directory
etc/modprobe.d/libpisock9
cpio: etc/modprobe.d/blacklist-modem: Cannot open: No such file or directory
etc/modprobe.d/blacklist-modem
cpio: etc/modprobe.d/arch-aliases: Cannot open: No such file or directory
etc/modprobe.d/arch-aliases
cpio: etc/modprobe.d/blacklist: Cannot open: No such file or directory
etc/modprobe.d/blacklist
cpio: etc/modprobe.d/nvidia-kernel-nkc: Cannot open: No such file or directory
etc/modprobe.d/nvidia-kernel-nkc
cpio: etc/modprobe.d/fuse: Cannot open: No such file or directory
etc/modprobe.d/fuse
cpio: etc/modprobe.d/aliases: Cannot open: No such file or directory
etc/modprobe.d/aliases
cpio: etc/modprobe.d/blacklist-oss: Cannot open: No such file or directory
etc/modprobe.d/blacklist-oss
cpio: etc/modprobe.d/blacklist-watchdog: Cannot open: No such file or directory
etc/modprobe.d/blacklist-watchdog
cpio: etc/modprobe.d/toshiba_acpi.modprobe: Cannot open: No such file or directory
etc/modprobe.d/toshiba_acpi.modprobe
cpio: etc/modprobe.d/alsa-base: Cannot open: No such file or directory
etc/modprobe.d/alsa-base
cpio: etc/udev: Cannot mkdir: No such file or directory
etc/udev
cpio: etc/udev/udev.conf: Cannot open: No such file or directory
etc/udev/udev.conf
cpio: etc/udev/rules.d: Cannot mkdir: No such file or directory
etc/udev/rules.d
cpio: etc/udev/rules.d/05-udev-early.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-udev-early.rules
cpio: etc/udev/rules.d/61-persistent-storage-edd.rules: Cannot open: No such file or directory
etc/udev/rules.d/61-persistent-storage-edd.rules
cpio: etc/udev/rules.d/95-udev-late.rules: Cannot open: No such file or directory
etc/udev/rules.d/95-udev-late.rules
cpio: etc/udev/rules.d/65-dmsetup.rules: Cannot open: No such file or directory
etc/udev/rules.d/65-dmsetup.rules
cpio: etc/udev/rules.d/20-names.rules: Cannot open: No such file or directory
etc/udev/rules.d/20-names.rules
cpio: etc/udev/rules.d/40-basic-permissions.rules: Cannot open: No such file or directory
etc/udev/rules.d/40-basic-permissions.rules
cpio: etc/udev/rules.d/05-options.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-options.rules
cpio: etc/udev/rules.d/90-modprobe.rules: Cannot open: No such file or directory
etc/udev/rules.d/90-modprobe.rules
cpio: etc/udev/rules.d/80-programs.rules: Cannot open: No such file or directory
etc/udev/rules.d/80-programs.rules
cpio: etc/udev/rules.d/60-persistent-storage.rules: Cannot open: No such file or directory
etc/udev/rules.d/60-persistent-storage.rules
cpio: etc/usplash.conf: Cannot open: No such file or directory
etc/usplash.conf
cpio: etc/default: Cannot mkdir: No such file or directory
etc/default
cpio: etc/default/console-setup: Cannot open: No such file or directory
etc/default/console-setup
cpio: sbin: Cannot mkdir: Permission denied
sbin
cpio: sbin/depmod: Cannot open: No such file or directory
sbin/depmod
cpio: sbin/udevd: Cannot open: No such file or directory
sbin/udevd
cpio: sbin/usplash_write: Cannot open: No such file or directory
sbin/usplash_write
cpio: sbin/cryptsetup: Cannot open: No such file or directory
sbin/cryptsetup
cpio: sbin/modprobe: Cannot open: No such file or directory
sbin/modprobe
cpio: sbin/rmmod: Cannot open: No such file or directory
sbin/rmmod
cpio: sbin/mount.ntfs: Cannot open: No such file or directory
sbin/mount.ntfs
cpio: sbin/udevadm: Cannot open: No such file or directory
sbin/udevadm
cpio: sbin/brltty-setup: Cannot open: No such file or directory
sbin/brltty-setup
cpio: sbin/mount.ntfs-3g: Cannot open: No such file or directory
sbin/mount.ntfs-3g
cpio: sbin/mount.fuse: Cannot open: No such file or directory
sbin/mount.fuse
cpio: sbin/pkill: Cannot open: No such file or directory
sbin/pkill
cpio: sbin/usplash: Cannot open: No such file or directory
sbin/usplash
cpio: sbin/dmsetup: Cannot open: No such file or directory
sbin/dmsetup
cpio: conf: Cannot mkdir: Permission denied
conf
cpio: conf/arch.conf: Cannot open: No such file or directory
conf/arch.conf
cpio: conf/conf.d: Cannot mkdir: No such file or directory
conf/conf.d
cpio: conf/conf.d/resume: Cannot open: No such file or directory
conf/conf.d/resume
cpio: conf/modules: Cannot open: No such file or directory
conf/modules
cpio: conf/initramfs.conf: Cannot open: No such file or directory
conf/initramfs.conf
cpio: modules: Cannot mkdir: Permission denied
modules
cpio: lib: Cannot mkdir: Permission denied
lib
cpio: lib/libusplash.so.0: Cannot open: No such file or directory
lib/libusplash.so.0
cpio: lib/libgcrypt.so.11: Cannot open: No such file or directory
lib/libgcrypt.so.11
cpio: lib/libdl.so.2: Cannot open: No such file or directory
lib/libdl.so.2
cpio: lib/ld-linux.so.2: Cannot open: No such file or directory
lib/ld-linux.so.2
cpio: lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so: Cannot open: No such file or directory
lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so
cpio: lib/firmware: Cannot mkdir: No such file or directory
lib/firmware
cpio: lib/firmware/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/firmware/2.6.24-19-generic
cpio: lib/firmware/2.6.24-19-generic/ql2100_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2100_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2400_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2400_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2300_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2300_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2200_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2200_fw.bin
cpio: lib/firmware/2.6.24-19-generic/aic94xx-seq.fw: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/aic94xx-seq.fw
cpio: lib/firmware/2.6.24-19-generic/ql2322_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2322_fw.bin
cpio: lib/libpthread.so.0: Cannot open: No such file or directory
lib/libpthread.so.0
cpio: lib/libsepol.so.1: Cannot open: No such file or directory
lib/libsepol.so.1
cpio: lib/libproc-3.2.7.so: Cannot open: No such file or directory
lib/libproc-3.2.7.so
cpio: lib/librt.so.1: Cannot open: No such file or directory
lib/librt.so.1
cpio: lib/libctutils.so.0: Cannot open: No such file or directory
lib/libctutils.so.0
cpio: lib/libpopt.so.0: Cannot open: No such file or directory
lib/libpopt.so.0
cpio: lib/libcfont.so.0: Cannot open: No such file or directory
lib/libcfont.so.0
cpio: lib/udev: Cannot mkdir: No such file or directory
lib/udev
cpio: lib/udev/scsi_id: Cannot open: No such file or directory
lib/udev/scsi_id
cpio: lib/udev/pnp_modules: Cannot open: No such file or directory
lib/udev/pnp_modules
cpio: lib/udev/firmware_helper: Cannot open: No such file or directory
lib/udev/firmware_helper
cpio: lib/udev/usb_device_name: Cannot open: No such file or directory
lib/udev/usb_device_name
cpio: lib/udev/vol_id: Cannot open: No such file or directory
lib/udev/vol_id
cpio: lib/udev/watershed: Cannot open: No such file or directory
lib/udev/watershed
cpio: lib/udev/path_id: Cannot open: No such file or directory
lib/udev/path_id
cpio: lib/udev/ata_id: Cannot open: No such file or directory
lib/udev/ata_id
cpio: lib/udev/dvb_device_name: Cannot open: No such file or directory
lib/udev/dvb_device_name
cpio: lib/udev/ide_media: Cannot open: No such file or directory
lib/udev/ide_media
cpio: lib/udev/usb_id: Cannot open: No such file or directory
lib/udev/usb_id
cpio: lib/udev/edd_id: Cannot open: No such file or directory
lib/udev/edd_id
cpio: lib/udev/vio_type: Cannot open: No such file or directory
lib/udev/vio_type
cpio: lib/libconsole.so.0: Cannot open: No such file or directory
lib/libconsole.so.0
cpio: lib/libfuse.so.2: Cannot open: No such file or directory
lib/libfuse.so.2
cpio: lib/libdevmapper.so.1.02.1: Cannot open: No such file or directory
lib/libdevmapper.so.1.02.1
cpio: lib/libc.so.6: Cannot open: No such file or directory
lib/libc.so.6
cpio: lib/libntfs-3g.so.23: Cannot open: No such file or directory
lib/libntfs-3g.so.23
cpio: lib/modules: Cannot mkdir: No such file or directory
lib/modules
cpio: lib/modules/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic
cpio: lib/modules/2.6.24-19-generic/initrd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/initrd
cpio: lib/modules/2.6.24-19-generic/kernel: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel
cpio: lib/modules/2.6.24-19-generic/kernel/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko
cpio: lib/modules/2.6.24-19-generic/kernel/arch: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/lib: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib
cpio: lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko
cpio: lib/libselinux.so.1: Cannot open: No such file or directory
lib/libselinux.so.1
cpio: lib/libx86.so.1: Cannot open: No such file or directory
lib/libx86.so.1
cpio: lib/libuuid.so.1: Cannot open: No such file or directory
lib/libuuid.so.1
cpio: lib/libvolume_id.so.0: Cannot open: No such file or directory
lib/libvolume_id.so.0
cpio: lib/brltty: Cannot mkdir: No such file or directory
lib/brltty
cpio: lib/brltty/brltty.sh: Cannot open: No such file or directory
lib/brltty/brltty.sh
cpio: lib/libgpg-error.so.0: Cannot open: No such file or directory
lib/libgpg-error.so.0
cpio: var: Cannot mkdir: Permission denied
var
cpio: var/run: Cannot mkdir: No such file or directory
var/run
cpio: lib/modules/2.6.24-19-generic/initrd/vesafb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/initrd/vesafb.ko
42079 blocks

```

Again, no files in /tmp/fakeroot

```

ubuntu@ubuntu:/tmp/fakeroot$ cat conf/conf.d/cryptroot
cat: conf/conf.d/cryptroot: No such file or directory
ubuntu@ubuntu:/tmp/fakeroot$ ls -l
total 0

```

---

### Post by hyper_ch on 2008-09-11
sudo apt-get install cpio

---

### Post by tristicles on 2008-09-11
Should the encrypted /dev/sda3 "/" partition be mounted at /tmp/fakeroot for this to work?

---

### Post by tristicles on 2008-09-11
```

ubuntu@ubuntu:/tmp/fakeroot$ sudo apt-get install cpio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 123 not upgraded.

```

---

### Post by hyper_ch on 2008-09-11
no, root partition should not be mounted

---

### Post by tristicles on 2008-09-11
Cool. Partition isn't mounted. Was just a thought!! :)

---

### Post by hyper_ch on 2008-09-11
thx to jdong I noticed that I made a mistake... first run:

```

sudo rmdir /tmp/fakeroot
mkdir /tmp/fakeroot

```

and then try that zcat / cpio command again.

P.S.: Start the irc client and come to #ubuntuforums on irc.freenode.org

---

### Post by tristicles on 2008-09-11
Same again I'm afraid :(

```

ubuntu@ubuntu:/tmpfakeroot$ sudo zcat /tmp/fakeboot/initrd.img-2.6.24-19-generic | cpio -iv
cpio: init: Cannot open: Permission denied
init
cpio: usr: Cannot mkdir: Permission denied
usr
cpio: usr/lib: Cannot mkdir: No such file or directory
usr/lib
cpio: usr/lib/usplash: Cannot mkdir: No such file or directory
usr/lib/usplash
cpio: usr/lib/usplash/usplash-artwork.so: Cannot open: No such file or directory
usr/lib/usplash/usplash-artwork.so
cpio: scripts: Cannot mkdir: Permission denied
scripts
cpio: scripts/init-top: Cannot mkdir: No such file or directory
scripts/init-top
cpio: scripts/init-top/framebuffer: Cannot open: No such file or directory
scripts/init-top/framebuffer
cpio: scripts/init-top/console_setup: Cannot open: No such file or directory
scripts/init-top/console_setup
cpio: scripts/init-top/all_generic_ide: Cannot open: No such file or directory
scripts/init-top/all_generic_ide
cpio: scripts/init-top/brltty: Cannot open: No such file or directory
scripts/init-top/brltty
cpio: scripts/init-top/usplash: Cannot open: No such file or directory
scripts/init-top/usplash
cpio: scripts/casper-premount: Cannot mkdir: No such file or directory
scripts/casper-premount
cpio: scripts/local-premount: Cannot mkdir: No such file or directory
scripts/local-premount
cpio: scripts/local-premount/resume: Cannot open: No such file or directory
scripts/local-premount/resume
cpio: scripts/local-premount/ntfs_3g: Cannot open: No such file or directory
scripts/local-premount/ntfs_3g
cpio: scripts/nfs-bottom: Cannot mkdir: No such file or directory
scripts/nfs-bottom
cpio: scripts/nfs-premount: Cannot mkdir: No such file or directory
scripts/nfs-premount
cpio: scripts/local-bottom: Cannot mkdir: No such file or directory
scripts/local-bottom
cpio: scripts/local-bottom/cryptopensc: Cannot open: No such file or directory
scripts/local-bottom/cryptopensc
cpio: scripts/local-bottom/ntfs_3g: Cannot open: No such file or directory
scripts/local-bottom/ntfs_3g
cpio: scripts/nfs: Cannot open: No such file or directory
scripts/nfs
cpio: scripts/local: Cannot open: No such file or directory
scripts/local
cpio: scripts/nfs-top: Cannot mkdir: No such file or directory
scripts/nfs-top
cpio: scripts/nfs-top/udev: Cannot open: No such file or directory
scripts/nfs-top/udev
cpio: scripts/init-premount: Cannot mkdir: No such file or directory
scripts/init-premount
cpio: scripts/init-premount/ps3: Cannot open: No such file or directory
scripts/init-premount/ps3
cpio: scripts/init-premount/udev: Cannot open: No such file or directory
scripts/init-premount/udev
cpio: scripts/functions: Cannot open: No such file or directory
scripts/functions
cpio: scripts/init-bottom: Cannot mkdir: No such file or directory
scripts/init-bottom
cpio: scripts/init-bottom/udev: Cannot open: No such file or directory
scripts/init-bottom/udev
cpio: scripts/local-top: Cannot mkdir: No such file or directory
scripts/local-top
cpio: scripts/local-top/cryptopensc: Cannot open: No such file or directory
scripts/local-top/cryptopensc
cpio: scripts/local-top/cryptroot: Cannot open: No such file or directory
scripts/local-top/cryptroot
cpio: bin: Cannot mkdir: Permission denied
bin
cpio: bin/consolechars: Cannot open: No such file or directory
bin/consolechars
cpio: bin/mkdir: Cannot open: No such file or directory
bin/mkdir
cpio: bin/ln: Cannot open: No such file or directory
bin/ln
cpio: bin/busybox: Cannot open: No such file or directory
bin/busybox
cpio: bin/readlink: Cannot open: No such file or directory
bin/readlink
cpio: bin/true: Cannot open: No such file or directory
bin/true
cpio: bin/dd: Cannot open: No such file or directory
bin/dd
cpio: bin/nfsmount: Cannot open: No such file or directory
bin/nfsmount
cpio: bin/kbd_mode: Cannot open: No such file or directory
bin/kbd_mode
cpio: bin/mkfifo: Cannot open: No such file or directory
bin/mkfifo
cpio: bin/zcat: Cannot open: No such file or directory
bin/zcat
cpio: bin/kinit: Cannot open: No such file or directory
bin/kinit
cpio: bin/resume: Cannot open: No such file or directory
bin/resume
cpio: bin/dmesg: Cannot open: No such file or directory
bin/dmesg
cpio: bin/ntfs-3g: Cannot open: No such file or directory
bin/ntfs-3g
cpio: bin/uname: Cannot open: No such file or directory
bin/uname
cpio: bin/reboot: Cannot open: No such file or directory
bin/reboot
cpio: bin/halt: Cannot open: No such file or directory
bin/halt
cpio: bin/kinit.shared: Cannot open: No such file or directory
bin/kinit.shared
cpio: bin/loadkeys: Cannot open: No such file or directory
bin/loadkeys
cpio: bin/kill: Cannot open: No such file or directory
bin/kill
cpio: bin/fstype: Cannot open: No such file or directory
bin/fstype
cpio: bin/sh: Cannot open: No such file or directory
bin/sh
cpio: bin/sync: Cannot open: No such file or directory
bin/sync
cpio: bin/cat: Cannot open: No such file or directory
bin/cat
cpio: bin/mount: Cannot open: No such file or directory
bin/mount
cpio: bin/cpio: Cannot open: No such file or directory
bin/cpio
cpio: bin/gunzip: Cannot open: No such file or directory
bin/gunzip
cpio: bin/chroot: Cannot open: No such file or directory
bin/chroot
cpio: bin/mknod: Cannot open: No such file or directory
bin/mknod
cpio: bin/gzip: Cannot open: No such file or directory
bin/gzip
cpio: bin/insmod: Cannot open: No such file or directory
bin/insmod
cpio: bin/nuke: Cannot open: No such file or directory
bin/nuke
cpio: bin/umount: Cannot open: No such file or directory
bin/umount
cpio: bin/sleep: Cannot open: No such file or directory
bin/sleep
cpio: bin/poweroff: Cannot open: No such file or directory
bin/poweroff
cpio: bin/ipconfig: Cannot open: No such file or directory
bin/ipconfig
cpio: bin/sh.shared: Cannot open: No such file or directory
bin/sh.shared
cpio: bin/minips: Cannot open: No such file or directory
bin/minips
cpio: bin/run-init: Cannot open: No such file or directory
bin/run-init
cpio: bin/false: Cannot open: No such file or directory
bin/false
cpio: bin/pivot_root: Cannot open: No such file or directory
bin/pivot_root
cpio: etc: Cannot mkdir: Permission denied
etc
cpio: etc/console-setup: Cannot mkdir: No such file or directory
etc/console-setup
cpio: etc/console-setup/Lat15-VGA16.psf.gz: Cannot open: No such file or directory
etc/console-setup/Lat15-VGA16.psf.gz
cpio: etc/console-setup/boottime.kmap.gz: Cannot open: No such file or directory
etc/console-setup/boottime.kmap.gz
cpio: etc/modprobe.d: Cannot mkdir: No such file or directory
etc/modprobe.d
cpio: etc/modprobe.d/blacklist-framebuffer: Cannot open: No such file or directory
etc/modprobe.d/blacklist-framebuffer
cpio: etc/modprobe.d/isapnp: Cannot open: No such file or directory
etc/modprobe.d/isapnp
cpio: etc/modprobe.d/arch: Cannot mkdir: No such file or directory
etc/modprobe.d/arch
cpio: etc/modprobe.d/arch/i386: Cannot open: No such file or directory
etc/modprobe.d/arch/i386
cpio: etc/modprobe.d/lrm-video: Cannot open: No such file or directory
etc/modprobe.d/lrm-video
cpio: etc/modprobe.d/options: Cannot open: No such file or directory
etc/modprobe.d/options
cpio: etc/modprobe.d/libsane: Cannot open: No such file or directory
etc/modprobe.d/libsane
cpio: etc/modprobe.d/libpisock9: Cannot open: No such file or directory
etc/modprobe.d/libpisock9
cpio: etc/modprobe.d/blacklist-modem: Cannot open: No such file or directory
etc/modprobe.d/blacklist-modem
cpio: etc/modprobe.d/arch-aliases: Cannot open: No such file or directory
etc/modprobe.d/arch-aliases
cpio: etc/modprobe.d/blacklist: Cannot open: No such file or directory
etc/modprobe.d/blacklist
cpio: etc/modprobe.d/nvidia-kernel-nkc: Cannot open: No such file or directory
etc/modprobe.d/nvidia-kernel-nkc
cpio: etc/modprobe.d/fuse: Cannot open: No such file or directory
etc/modprobe.d/fuse
cpio: etc/modprobe.d/aliases: Cannot open: No such file or directory
etc/modprobe.d/aliases
cpio: etc/modprobe.d/blacklist-oss: Cannot open: No such file or directory
etc/modprobe.d/blacklist-oss
cpio: etc/modprobe.d/blacklist-watchdog: Cannot open: No such file or directory
etc/modprobe.d/blacklist-watchdog
cpio: etc/modprobe.d/toshiba_acpi.modprobe: Cannot open: No such file or directory
etc/modprobe.d/toshiba_acpi.modprobe
cpio: etc/modprobe.d/alsa-base: Cannot open: No such file or directory
etc/modprobe.d/alsa-base
cpio: etc/udev: Cannot mkdir: No such file or directory
etc/udev
cpio: etc/udev/udev.conf: Cannot open: No such file or directory
etc/udev/udev.conf
cpio: etc/udev/rules.d: Cannot mkdir: No such file or directory
etc/udev/rules.d
cpio: etc/udev/rules.d/05-udev-early.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-udev-early.rules
cpio: etc/udev/rules.d/61-persistent-storage-edd.rules: Cannot open: No such file or directory
etc/udev/rules.d/61-persistent-storage-edd.rules
cpio: etc/udev/rules.d/95-udev-late.rules: Cannot open: No such file or directory
etc/udev/rules.d/95-udev-late.rules
cpio: etc/udev/rules.d/65-dmsetup.rules: Cannot open: No such file or directory
etc/udev/rules.d/65-dmsetup.rules
cpio: etc/udev/rules.d/20-names.rules: Cannot open: No such file or directory
etc/udev/rules.d/20-names.rules
cpio: etc/udev/rules.d/40-basic-permissions.rules: Cannot open: No such file or directory
etc/udev/rules.d/40-basic-permissions.rules
cpio: etc/udev/rules.d/05-options.rules: Cannot open: No such file or directory
etc/udev/rules.d/05-options.rules
cpio: etc/udev/rules.d/90-modprobe.rules: Cannot open: No such file or directory
etc/udev/rules.d/90-modprobe.rules
cpio: etc/udev/rules.d/80-programs.rules: Cannot open: No such file or directory
etc/udev/rules.d/80-programs.rules
cpio: etc/udev/rules.d/60-persistent-storage.rules: Cannot open: No such file or directory
etc/udev/rules.d/60-persistent-storage.rules
cpio: etc/usplash.conf: Cannot open: No such file or directory
etc/usplash.conf
cpio: etc/default: Cannot mkdir: No such file or directory
etc/default
cpio: etc/default/console-setup: Cannot open: No such file or directory
etc/default/console-setup
cpio: sbin: Cannot mkdir: Permission denied
sbin
cpio: sbin/depmod: Cannot open: No such file or directory
sbin/depmod
cpio: sbin/udevd: Cannot open: No such file or directory
sbin/udevd
cpio: sbin/usplash_write: Cannot open: No such file or directory
sbin/usplash_write
cpio: sbin/cryptsetup: Cannot open: No such file or directory
sbin/cryptsetup
cpio: sbin/modprobe: Cannot open: No such file or directory
sbin/modprobe
cpio: sbin/rmmod: Cannot open: No such file or directory
sbin/rmmod
cpio: sbin/mount.ntfs: Cannot open: No such file or directory
sbin/mount.ntfs
cpio: sbin/udevadm: Cannot open: No such file or directory
sbin/udevadm
cpio: sbin/brltty-setup: Cannot open: No such file or directory
sbin/brltty-setup
cpio: sbin/mount.ntfs-3g: Cannot open: No such file or directory
sbin/mount.ntfs-3g
cpio: sbin/mount.fuse: Cannot open: No such file or directory
sbin/mount.fuse
cpio: sbin/pkill: Cannot open: No such file or directory
sbin/pkill
cpio: sbin/usplash: Cannot open: No such file or directory
sbin/usplash
cpio: sbin/dmsetup: Cannot open: No such file or directory
sbin/dmsetup
cpio: conf: Cannot mkdir: Permission denied
conf
cpio: conf/arch.conf: Cannot open: No such file or directory
conf/arch.conf
cpio: conf/conf.d: Cannot mkdir: No such file or directory
conf/conf.d
cpio: conf/conf.d/resume: Cannot open: No such file or directory
conf/conf.d/resume
cpio: conf/modules: Cannot open: No such file or directory
conf/modules
cpio: conf/initramfs.conf: Cannot open: No such file or directory
conf/initramfs.conf
cpio: modules: Cannot mkdir: Permission denied
modules
cpio: lib: Cannot mkdir: Permission denied
lib
cpio: lib/libusplash.so.0: Cannot open: No such file or directory
lib/libusplash.so.0
cpio: lib/libgcrypt.so.11: Cannot open: No such file or directory
lib/libgcrypt.so.11
cpio: lib/libdl.so.2: Cannot open: No such file or directory
lib/libdl.so.2
cpio: lib/ld-linux.so.2: Cannot open: No such file or directory
lib/ld-linux.so.2
cpio: lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so: Cannot open: No such file or directory
lib/klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so
cpio: lib/firmware: Cannot mkdir: No such file or directory
lib/firmware
cpio: lib/firmware/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/firmware/2.6.24-19-generic
cpio: lib/firmware/2.6.24-19-generic/ql2100_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2100_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2400_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2400_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2300_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2300_fw.bin
cpio: lib/firmware/2.6.24-19-generic/ql2200_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2200_fw.bin
cpio: lib/firmware/2.6.24-19-generic/aic94xx-seq.fw: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/aic94xx-seq.fw
cpio: lib/firmware/2.6.24-19-generic/ql2322_fw.bin: Cannot open: No such file or directory
lib/firmware/2.6.24-19-generic/ql2322_fw.bin
cpio: lib/libpthread.so.0: Cannot open: No such file or directory
lib/libpthread.so.0
cpio: lib/libsepol.so.1: Cannot open: No such file or directory
lib/libsepol.so.1
cpio: lib/libproc-3.2.7.so: Cannot open: No such file or directory
lib/libproc-3.2.7.so
cpio: lib/librt.so.1: Cannot open: No such file or directory
lib/librt.so.1
cpio: lib/libctutils.so.0: Cannot open: No such file or directory
lib/libctutils.so.0
cpio: lib/libpopt.so.0: Cannot open: No such file or directory
lib/libpopt.so.0
cpio: lib/libcfont.so.0: Cannot open: No such file or directory
lib/libcfont.so.0
cpio: lib/udev: Cannot mkdir: No such file or directory
lib/udev
cpio: lib/udev/scsi_id: Cannot open: No such file or directory
lib/udev/scsi_id
cpio: lib/udev/pnp_modules: Cannot open: No such file or directory
lib/udev/pnp_modules
cpio: lib/udev/firmware_helper: Cannot open: No such file or directory
lib/udev/firmware_helper
cpio: lib/udev/usb_device_name: Cannot open: No such file or directory
lib/udev/usb_device_name
cpio: lib/udev/vol_id: Cannot open: No such file or directory
lib/udev/vol_id
cpio: lib/udev/watershed: Cannot open: No such file or directory
lib/udev/watershed
cpio: lib/udev/path_id: Cannot open: No such file or directory
lib/udev/path_id
cpio: lib/udev/ata_id: Cannot open: No such file or directory
lib/udev/ata_id
cpio: lib/udev/dvb_device_name: Cannot open: No such file or directory
lib/udev/dvb_device_name
cpio: lib/udev/ide_media: Cannot open: No such file or directory
lib/udev/ide_media
cpio: lib/udev/usb_id: Cannot open: No such file or directory
lib/udev/usb_id
cpio: lib/udev/edd_id: Cannot open: No such file or directory
lib/udev/edd_id
cpio: lib/udev/vio_type: Cannot open: No such file or directory
lib/udev/vio_type
cpio: lib/libconsole.so.0: Cannot open: No such file or directory
lib/libconsole.so.0
cpio: lib/libfuse.so.2: Cannot open: No such file or directory
lib/libfuse.so.2
cpio: lib/libdevmapper.so.1.02.1: Cannot open: No such file or directory
lib/libdevmapper.so.1.02.1
cpio: lib/libc.so.6: Cannot open: No such file or directory
lib/libc.so.6
cpio: lib/libntfs-3g.so.23: Cannot open: No such file or directory
lib/libntfs-3g.so.23
cpio: lib/modules: Cannot mkdir: No such file or directory
lib/modules
cpio: lib/modules/2.6.24-19-generic: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic
cpio: lib/modules/2.6.24-19-generic/initrd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/initrd
cpio: lib/modules/2.6.24-19-generic/kernel: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel
cpio: lib/modules/2.6.24-19-generic/kernel/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc
cpio: lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/sunrpc/sunrpc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4
cpio: lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/ipv4/inet_lro.ko
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet
cpio: lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/net/packet/af_packet.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/sha256_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/cbc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/crypto/blkcipher.ko
cpio: lib/modules/2.6.24-19-generic/kernel/arch: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/arch/x86/crypto/aes-i586.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/yellowfin.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sunhme.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ne2k-pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e1000/e1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/forcedeth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/hp100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/ns83820.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/myri10ge/myri10ge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/e100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/3c59x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/fealnx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/natsemi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/epic100.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem_phy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/slhc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139cp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/dl2k.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sundance.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/bnx2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tlan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/s2io.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/mii.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8390.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sis900.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de2104x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/winbond-840.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/xircom_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/tulip.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/de4x5.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tulip/dmfe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/pcnet32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/8139too.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/sungem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/eql.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/r8169.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/tg3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/defxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/via-velocity.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/netconsole.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/skge.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/starfire.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/net/qla3xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_pci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/virtio/virtio_ring.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vgastate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/vga16fb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/bitblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/fbcon.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/font.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/softcursor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/video/console/tileblit.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/cdrom/cdrom.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/sbp2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/fan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/acpi/processor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/pcmcia/pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-crypt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/md/dm-mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptscsih.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptspi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptbase.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/fusion/mptfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/message/i2o/i2o_block.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/loop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cciss.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cryptoloop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck6.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/dstr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/bpck.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/ktti.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on20.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/frpw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/comm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/aten.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/paride.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/fit3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/kbic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/on26.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/epat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/pf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/paride/friq.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/sx8.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/cpqarray.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/virtio_blk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/pktcdvd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/umem.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/DAC960.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/aoe/aoe.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/xd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/block/nbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla1280.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/u14-34f.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fd_mcs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-xxxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dtc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsas/libsas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_tgt.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sym53c416.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sg.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_spi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/53c700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ibmmca.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aacraid/aacraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dc395x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libiscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_debug.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ultrastor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/initio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/raid_class.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dmx3191d.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/libsrp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR53c406a.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sr_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/seagate.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/eata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ide-scsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/a100u2w.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sim710.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/hptiop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/sd_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/gdth.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/osst.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1740.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/3w-9xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ch.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/stex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha1542.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aha152x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/lpfc/lpfc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/t128.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/pas16.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/imm.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/megaraid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_fc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/atp870u.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/in2000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/fdomain.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_srp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/tmscsim.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/BusLogic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/iscsi_tcp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/nsp32.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_sas.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_D700.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ips.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/NCR_Q720_mod.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ipr.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_wait_scan.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/psi240i.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/qlogicfas408.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/dpt_i2o.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/advansys.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/st.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/ppa.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/scsi/wd7000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/parport/parport.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/hid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/hid/usbhid/usbhid.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ssb/ssb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pdc2027x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_pcmcia.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_acpi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_nv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_serverworks.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_mv.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_marvell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/libata.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it8213.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_oldpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sl82c105.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_triflex.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_artop.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_jmicron.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_amd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_vsc.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_netcell.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sx4.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ahci.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt3x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sis.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_rz1000.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pdc_adma.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_it821x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_svw.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_efar.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_promise.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_inic162x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_piix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_qdi.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_via.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_uli.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil24.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_mpiix.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_sil.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_sil680.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/ata_generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/sata_qstor.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5520.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ata/pata_cs5536.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/qd65xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ht6560b.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/dtc2278.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ali14xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/umc8672.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/legacy/ide_platform.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-core.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-tape.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt34x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/delkin_cb.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/ns87415.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5530.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/hpt366.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cy82c693.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/aec62xx.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cmd64x.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/cs5535.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/atiixp.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/alim15x3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/opti621.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/sc1200.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/tc86c001.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/trm290.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/pci/pdc202xx_old.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-disk.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-cd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-generic.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/ide/ide-floppy.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/libusual.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/storage/usb-storage.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/core/usbcore.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ohci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/uhci-hcd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf
cpio: lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/udf/udf.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/isofs/isofs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jbd/jbd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/reiserfs/reiserfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext2/ext2.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/jfs/jfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs_common/nfs_acl.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_iso8859-1.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nls/nls_cp437.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/vfat/vfat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/nfs/nfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fuse/fuse.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd
cpio: lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/lockd/lockd.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat
cpio: lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/fat/fat.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/configfs/configfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs
cpio: lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/xfs/xfs.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/mbcache.ko
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3
cpio: lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/fs/ext3/ext3.ko
cpio: lib/modules/2.6.24-19-generic/kernel/lib: Cannot mkdir: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib
cpio: lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/kernel/lib/crc-ccitt.ko
cpio: lib/libselinux.so.1: Cannot open: No such file or directory
lib/libselinux.so.1
cpio: lib/libx86.so.1: Cannot open: No such file or directory
lib/libx86.so.1
cpio: lib/libuuid.so.1: Cannot open: No such file or directory
lib/libuuid.so.1
cpio: lib/libvolume_id.so.0: Cannot open: No such file or directory
lib/libvolume_id.so.0
cpio: lib/brltty: Cannot mkdir: No such file or directory
lib/brltty
cpio: lib/brltty/brltty.sh: Cannot open: No such file or directory
lib/brltty/brltty.sh
cpio: lib/libgpg-error.so.0: Cannot open: No such file or directory
lib/libgpg-error.so.0
cpio: var: Cannot mkdir: Permission denied
var
cpio: var/run: Cannot mkdir: No such file or directory
var/run
cpio: lib/modules/2.6.24-19-generic/initrd/vesafb.ko: Cannot open: No such file or directory
lib/modules/2.6.24-19-generic/initrd/vesafb.ko
42079 blocks

```

---

### Post by hyper_ch on 2008-09-11
come into irc

---

### Post by tristicles on 2008-09-11
This is not my day!!! I'm too stupid to even work out how to do that (I don't go in for social networking and instant messaging!!!).

I've fired up Pidgin and created a new irc account, pointing to irc.freenode.org. I've sent a message to "hyper_ch". Did you receive it?

---

### Post by tristicles on 2008-09-11
I think I'm in. I missed the all important #ubuntuforums bit. I've found hyper_ch and have sent you a "hello".

---

### Post by tristicles on 2008-09-11
For anyone else who may be following this thread, I've logged in to the chat room (eventually!!!) and unutb1 has helped me out a lot more.

The previous command was failing as the piped cpio command needed root privs as well. Running "sudo su" or "sudo -i" will give you a command prompt as root. Do that, then run the zcat command and you're laughing

It extracted all the files and folders from /tmp/fakeboot into /tmp/fakeroot

hyper_ch wanted to have a look at /tmp/fakeroot/conf/conf.d/cryptroot

It's not there. This leads me to believe that one of the update processes has wiped the file.

If anyone can shed any light on this, please let me know.

It's now 21:20 here in sunny UK. I've been dealing with this all day and have had enough!!! I'm gonna take it back to work, nuke it and rebuild it tomorrow. I'll then look out for this conf/conf.d/cryptroot file and back it up.

You've got 12 hours to save this laptop build!!! Seriously, any info really appreciated.

Cheers,
T

---

### Post by bodhi.zazen on 2008-09-11
Did you use LVM ? if so, you need to install lvm and then use lvm to mount your partitions.

```
sudo apt-get install lvm2
```

Then :

```
sudo vgscan --mknodes[FONT=monospace]
[/FONT]sudo vgchange -ay
```

---

### Post by tristicles on 2008-09-12
I don't think so (please forgive my ignorance). The guide (see link in the first post) uses "Physical Voume for Encryption", with the encryption method of "Device Mapper (dm-crypt)". I didn't touch any of the given LVM options.

Gonna nuke it and try again. Then look for the file we couldn't find previously

---

### Post by tristicles on 2008-09-12
Back to the drawing board. I've nuked the laptop and rebuilt in the same way. The crytroot file referred to in the previous threads is not present in conf/conf.d/cryptroot anywhere.

I've had a quick look and come up with:
```

root@bespin:/# locate cryptroot
/usr/share/initramfs-tools/hooks/cryptroot
/usr/share/initramfs-tools/scripts/local-top/cryptroot

```

Thinking about this, the system update was the problem. In particular the kernel. I've therefore re-applied all the system updates except the kernel and initramfs related ones. It still works fine. Brave, or what?!!!

So the issue here is updating the kernel with an encrypted file system. I found a [post on the forums here]("http://ubuntuforums.org/showthread.php?p=4398688") that suggests adding the hardy repository and installing cryptsetup and dmsetup. I've tried that but it won't update. It reports I'm already on the latest version

---

### Post by hyper_ch on 2008-09-12
I read in the chat that you have now successfully unpacked the initramfs into the /tmp/fakeroot folder and that it had no "cryptroot" file?

---

### Post by tristicles on 2008-09-12
Solved. Having followed [a thread on Launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213279"), I've managed to resolve the problem. The applicable section was:

> 
```

cp /usr/share/initramfs-tools/hooks/cryptroot /etc/initramfs-tools/hooks/cryptroot
cp /usr/share/initramfs-tools/scripts/local-top/cryptroot /etc/initramfs-tools/scripts/local-top/cryptroot
update-initramfs -u


```
Solved the problem on my machine.


I've since updated the kernel and it's working fine.

Thanks everyone for your help.

---

