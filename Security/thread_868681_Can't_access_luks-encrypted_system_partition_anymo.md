---
title: "Can't access luks-encrypted system partition anymore"
date: 2008-07-24
forum: Security
---

### Post by slabo on 2008-07-24
Newbie-Alert: Please point out any mistakes i'm making.

On booting, the system doesn't accept my password for unlocking the encrypted system partition anymore.

Setup: Ubuntu Hardy Heron, set up on 07/16, last updated (working) via synaptic on 07/20 (?). /dev/sda3 is an encrypted partition, which hosts a logical volume, which in turn hosts volume groups for / and swap. /boot is unencrypted. I encrypted via the alternate installer CD. This setup had worked fine until yesterday.

What happened? I'm not sure. I can't access the partition since last evening. At noon, i updated via synaptic, i think it concerned gvfs. (One problem is that i'm not certain that this update ran through.) The update-process seems to have left /boot untouched.

All in all, the system acts like my password is wrong, but i'm confident it is correct. I'm trying to access with the help of a Xubuntu-live-CD (7.10).

Output of [COLOR="Red"]sudo cryptsetup luksDump /dev/sda3[/COLOR]: [http://pastebin.com/m2be5ccf](http://pastebin.com/m2be5ccf) Looks okay to me.

[Only thread i've found so far that looks similar. (Link)]("http://ubuntuforums.org/showthread.php?t=609444") Does anybody have an idea why that suddenly just worked again?

- How can i find out, what was installed in yesterdays update via synaptic? 
- If /boot was unaltered and the partition header of the encrypted partition looks okay, what in the world could be causing trouble?
- Any hints/ideas for further diagnosis?

---

### Post by hyper_ch on 2008-07-24
can you manually unlock it from the Desktop CD?

On a side note, why did you encrypt a logical volume and not the partitions within it individually?

---

### Post by slabo on 2008-07-24
I tried to unlock it with [COLOR="Sienna"]sudo cryptsetup luksOpen /dev/sda5 cryptdisc[/COLOR]. It prompts me for my password, but doesn't accept it. Mount outputs: "mount: unknown filesystem type 'crypto_LUKS'"


I encrypted / and swap together so that i only have to enter one password. I found some howtos which suggested that.

---

### Post by hyper_ch on 2008-07-24
up there you said it's /dev/sda3 which is encrypted then you say it's /dev/sda5....

---

### Post by slabo on 2008-07-24
Oops, sorry. It is /dev/sda3. /dev/sda5 is my /boot. (But actually trying to open that with luksOpen also prompts me for a password, i just found out. Anyway, luksDump recognises sda3 as a luks-partition.)

---

### Post by tact on 2008-07-24
Hi slabo

- First up - boot from desktop liveCD and make sure you have an internet connection.
- Now you have to install some stuff thats not there in the liveCD.  Pull up a terminal (Applications>Accessories>Terminal)
- type "sudo su"  
- type "apt-get install lvm2 cryptsetup
- type "mkdir /media/test"
- type "modprobe dm-crypt"
- type "cryptsetup luksOpen /dev/sda5 test"
(enter password...  are you set up on sda3 or sda5?  change as needed)
(you should get a command successful message...  continue:)
- type "vgchange -ay" 
(this will reveal your volume group name)
- type "mount /dev/("volume group name")/home /media/test
- type "nautilus /media/test"
(and now your encrypted /home should open in a window.)

If all that works...  manually mounting the partition...  then its not the encrypted header or partition thats got a problem.  So close it all up...
-  close nautilus
-  type "umount /media/test"
-  type "cryptsetup luksClose /dev/sda5



Unmount it all and

---

### Post by slabo on 2008-07-24
Hi tact, and thx for your answer,

i already tried that. This is precisely what i tried so far:
- Started Xubuntu 7.10 Live-CD
- sudo aptitude -y install cryptsetup initramfs-tools hashalot lvm2 (following [this HOWTO]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto"))
- modprobe aes-i586<enter> modprobe dm-crypt<enter>modprobe dm-mod<enter>
- *sudo cryptsetup luksOpen /dev/sda3 cryptdisc*, result: "Command failed: No key available with this passphrase." Thus the same result that comes up during boot. (This message however comes also up, if one tries to unlock a partition that is not a luks-partition.) However, i am positive that i know the passphrase, i have it on a note right in front of me and it worked for a week.
- *sudo cryptsetup luksDump /dev/sda3* however results in a seemingly valid description of the header of the partition, see above.

---

### Post by tact on 2008-07-24
you will get the same error message if trying to open a non-luks partition.

just to be sure could you please boot up from the CD again and execute the following in a terminal and post back the results?

```
sudo fdisk -l /dev/sda
```
(that is a lowercase "L" after "fdisk")

Result should look something like this...
===
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b182c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       14593   116969265    5  Extended
/dev/sda5              32       14593   116969233+  83  Linux
===

In the above example the correct partition to cryptsetup luksOpen would be /dev/sda5

Cheers

---

### Post by slabo on 2008-07-24
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa7a99c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1532    12305758+  83  Linux
/dev/sda2            1533        1824     2345490    5  Extended
/dev/sda3            1825        9733    63529042+  83  Linux
/dev/sda5            1533        1581      393561   83  Linux
/dev/sda6            1582        1824     1951866   83  Linux
```
This is what the disk looks like in gparted:
[[IMG]http://img232.imageshack.us/img232/2521/gpartedam5.th.png[/IMG]](http://img232.imageshack.us/my.php?image=gpartedam5.png)
This needs explanation:
[LIST]
[*]/dev/sda1 i left free for a later minimal Windows install. (Don't know why i put ext3 on it, but ntfs wasn't supported, and i think the installer required me to format it.)
[*]/dev/sda5 is the boot partition, positively
[*]/dev/sda6 is a spare swap-partition, in case i would encounter problems with the encrypted swap, like i did on my Xubuntu notebook.
[*]/dev/sda3 is the encrypted volume. On it is a LVM and VGs for / (not /home) and swap.
[/LIST]

---

### Post by tact on 2008-07-24
Ok...  so to confirm you positively ran these steps and cannot open the crypt-volume?

- boot from desktop liveCD and make sure you have an internet connection.
- Pull up a terminal (Applications>Accessories>Terminal)
```
sudo su  
apt-get install lvm2 cryptsetup
mkdir /media/test
modprobe dm-crypt
cryptsetup luksOpen /dev/sda3 test

```

Nothing fails until you get to this point....and it is at this point you get the "Command failed: No key available with this passphrase." message.

Correct?

---

### Post by tact on 2008-07-24
When you boot up, press "esc" when the grub menu comes up...  do you have a choice of kernels there?   Try choosing to boot with any/all of the older kernels you have listed in the grub-boot menu at boot time.

---

### Post by slabo on 2008-07-25
Yes, the description in the before post is correct. I have an older kernel on there, i'll try that and post results. (Can't do it right now.)

---

### Post by slabo on 2008-07-25
So, i was wrong: I only have a recovery kernel in the grub-menu. With that, it doesn't work either.
```
Enter LUKS passphrase:
[54.566755] padlock: VIA PadLock Hash Engine not detected.
modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-sha.ko): No such device

Enter LUKS passphrase: *I enter that 3 times and then...*
Command failed: No key available with this passphrase.

cryptsetup: cryptsetup failed, bad password or options?
Enter LUKS passphrase:
```

I'm not sure, but i believe that i have not seen the padlock-error on that system before. Curiously enough, it always appears on my encrypted Xubuntu-8.04-notebook while booting, but only after entering the passphrase, and despite the error it then boots correctly.

---

### Post by tact on 2008-07-25
Don't worry about the via-padlock thing.  Its not part of the problem.  You can google around and get more info if needed.

Ok I am at a bit of a loss now how to advise you.  Booting an older kernel would have just helped eliminate one possible problem.  But you don't have one available.  Its beyond my limited linux skills to take this further.

I hope someone else might be able to step up.

---

### Post by slabo on 2008-07-25
It does look pretty weird. Since nothing really changed on the bootpartition, the only thing i can think of is a physical defect on the disk, but that's a shot in the dark.

Thanks for trying to help anyway. I'll keep on trying for now, so if anybody else has an idea, i'd be grateful.

---

### Post by tact on 2008-07-25
what exactly happened between it working and then stopped working?  anything of note?

---

### Post by slabo on 2008-07-26
The (possibly unfinished) update, which concerned gvfs, the last time the system worked. Otherwise, nothing that i noticed.

---

### Post by Moop on 2008-07-27
I'm not trying to hijack this thread but I'm having the same problem accessing a luks encrypted disk. I used the full disk encryption on the alternate install cd. By following the instructions here 
> **tact said:**
> Ok...  so to confirm you positively ran these steps and cannot open the crypt-volume?

- boot from desktop liveCD and make sure you have an internet connection.
- Pull up a terminal (Applications>Accessories>Terminal)
```
sudo su  
apt-get install lvm2 cryptsetup
mkdir /media/test
modprobe dm-crypt
cryptsetup luksOpen /dev/sda3 test

```Nothing fails until you get to this point....and it is at this point you get the "Command failed: No key available with this passphrase." message.

Correct?

I enter the passphrase and get a command successful message. How do mount the disk? If I use ```
mount  /dev/sdc5 /media/test
``` I get a message "mount: unknown filesystem type 'crypto_LUKS'"

---

### Post by slabo on 2008-07-28
You should then be able to mount /dev/*mapper*/test to a directory of your choice.

---

### Post by dchky on 2008-12-12
Thanks Tact, Slabo, if I had the first clue how the thankyou thing works, I'd thank you.

"Works for me"

---

### Post by John Wiersba on 2009-01-09
For some reason, I cannot load dm-crypt.  I booted the 8.10 live cd and ran sudo modprobe dm-crypt:
FATAL: Module dm_crypt not found.

---

### Post by hyper_ch on 2009-01-09
did you install cryptsetup?

---

### Post by John Wiersba on 2009-01-09
Hyper_ch (what does that mean, BTW?): Yes, I installed cryptsetup with apt-get install.  Can you give me the exact list of commands from an 8.10 Desktop Live CD, after connecting to the network and opening a terminal window?  apt-get this, modprobe that.  The instructions I've tried following seem to work for others, but not for me, so I must be missing something.

BTW, this is a laptop I installed from the 8.10 alternate CD, creating two partitions: boot + an encrypted partition with LVM inside containing 4 logical partitions: /, home, swap, and a spare-/.  

I used this configuration because I intend to be able to do the following major administration tasks:

[LIST=1]
[*]Normal operation: Cold boot, prompt for passphrase/USBkey, then automatically log into my user account with everything unlocked (including wireless keychain).  That is, I want to enter credentials only once (at the post-grub prompt for unlocking my encrypted partition).

[*]Boot from Live Desktop CD, load modules, etc., and use it as a rescue CD where I can still access the logical LVM partitions described above.

[*]Create a Live Rescue CD which includes all the prerequisites for doing #2 already on the CD (so I don't need a network).

[*]My plan for upgrading to a the next Ubuntu release is to do a fresh install instead of an upgrade.  For this I will want to install the new version of Ubuntu (Jaunty) in the spare-/ logical partition I've set aside above, in order to try Jaunty out.  To do that I will need to be able to install into an already existing logical partition inside an encrypted partition.  After installation, I will need to be able to switch at boot time (from the grub menu) to either the old / partition (8.10) or the new / partition (9.4) at will.  The old / will mount my home partition on /home, but the new / will not (it will be self-contained within one partition).  Once I'm confident that everything is working in the Jaunty install, I will shuffle things around a bit and then mount my home partition onto /home in the Jaunty partition and make that my default.
[/LIST]

Thanks for your help!

---

### Post by hyper_ch on 2009-01-09
also install:  loop-aes-utils

---

### Post by scorp123 on 2009-01-09
Please forgive me jumping in .... But I just happened to have this link amongst my bookmarks:

"Rescue LUKS-encrypted LVM"
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

... maybe it's useful to this discussion here?

---

### Post by jaygo on 2009-02-02
TY scorp! I found my solution on that page ... just had to "modprobe dm-crypt" (as root) at the terminal before the cryptsetup commands worked right.

---

### Post by Tubes6al4v on 2009-02-02
Congrats! Can you mark the thread as Solved so others can benefit from the thread?

---

### Post by John Wiersba on 2009-02-02
It turns out that I didn't need loop-aes-utils.  For whatever reason I'm able to follow the standard procedure after rebooting from a 8.10 Live CD.  My cheatsheet, based on [http://ubuntuforums.org/showthread.php?t=940904](http://ubuntuforums.org/showthread.php?t=940904), is:
```

# /dev/sda1 is my /boot.  /dev/sda2 is my crypto partition, containing 
# volume group vg1 with logical partitions lvswap, lvroot, lvdata

# need packages cryptsetup (encrypted partition tools) and lvm2 (logical
# volume manager); install from internet (apt-get) or from local .deb files

# either use direct package installation (I pre-downloaded into /boot/rescue)...
sudo mkdir /media/boot
sudo mount /dev/sda1 /media/boot
sudo dpkg -i /media/boot/rescue/cryptsetup*.deb /media/boot/rescue/lvm2*.deb

# or use network-based package download/installation
sudo apt-get install cryptsetup lvm2                      

# insert kernel modules that we will need
sudo modprobe dm-crypt
sudo modprobe dm-mod

# unlock the sda2 partition and call it MYTAG
sudo cryptsetup luksOpen /dev/sda2 MYTAG
  Enter LUKS passphrase:
  key slot 0 unlocked.
  Command successful.

# now that we have unlocked the encryption, deal with the lvm

sudo vgscan                      # scan for all volume groups
  Reading all physical volumes. This may take a while...
  Found volume group "vg1" using metadata type lvm2

# make the vg1 volume group active; if you don't give it a volume group as
# an argument it'll make them all active
sudo vgchange -ay [vg1]

sudo lvscan             # list logical volumes and their /dev path
ACTIVE '/dev/vg1/lvswap' [2.00 GB] inherit
ACTIVE '/dev/vg1/lvroot' [10.00 GB] inherit
ACTIVE '/dev/vg1/lvdata' [60.00 GB] inherit

# mount a logical volume; don't do this if you need to run fsck on it
sudo mkdir /media/root
sudo mount /dev/vg1/lvroot /media/root

# to reverse the process and unmount everything, do the following

sudo umount /media/root

# the following command will issue a somewhat confusing message
sudo vgchange -an [vg1]
  0 logical volume(s) in volume group "vg1" now active

sudo cryptsetup luksClose MYTAG

#---------------------------------------------------------------
# to rescue master boot record, use:  sudo grub-install /dev/hda
# or, boot from live cd and then (hd0,0 is my boot partition /sda1):
sudo grub
> find /grub/stage1
  (hd0,0)
> root (hd0,0)
> setup (hd0)
> quit



```

---

### Post by John Wiersba on 2009-02-02
Hyper_ch, I use an encrypted lvm on my laptop because I only need to manage one passphrase -- once I've decrypted my lvm partition, I can have everything open automatically.  I get no advantage from separately encrypting each partition within the lvm.

---

### Post by F W Adams on 2009-02-21
tact, your post #6, slabo, any help, totally confused.

I set up a completely new encrypted system ( except for boot ). It works booting from the hard drive, just enter the password and off we go.

Then I wanted to boot from the desktop CD so I could make some changes. This is what I get. The encrypted partition is sda2, sdb is not in use yet.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c3674ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19        9729    78003607+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78ec3f2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          24      192748+  83  Linux
/dev/sdb2              25        2456    19535040   83  Linux
/dev/sdb3            2457        3672     9767520   83  Linux
/dev/sdb4            3673       15830    97659135   83  Linux
root@ubuntu:/home/ubuntu# apt-get install lvm2 cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cryptsetup lvm2
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 414kB of archives.
After this operation, 1331kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/main cryptsetup 2:1.0.5-2ubuntu12 [88.7kB]
Get:2 http://archive.ubuntu.com hardy/main lvm2 2.02.26-1ubuntu9 [325kB]
Fetched 414kB in 3s (118kB/s)
Selecting previously deselected package cryptsetup.
(Reading database ... 98542 files and directories currently installed.)
Unpacking cryptsetup (from .../cryptsetup_2%3a1.0.5-2ubuntu12_i386.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.26-1ubuntu9_i386.deb) ...
Setting up cryptsetup (2:1.0.5-2ubuntu12) ...
update-initramfs is disabled since running on a live CD

Setting up lvm2 (2.02.26-1ubuntu9) ...
Backing up any LVM2 metadata that may exist...done.
update-initramfs is disabled since running on a live CD

root@ubuntu:/home/ubuntu# mkdir /media/test
root@ubuntu:/home/ubuntu# modprobe dm-crypt
root@ubuntu:/home/ubuntu# cryptsetup luksOpen /dev/sda2 test
Enter LUKS passphrase: 
Enter LUKS passphrase: 
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

root@ubuntu:/home/ubuntu# 


```

I've tried this several times, if I do a normal boot, not from the CD, then the above code works. My fingers are well used to keying in the password so I don't think it's finger trouble.

Any suggestions?

---

### Post by John Wiersba on 2009-02-22
Have you tried sudo modprobe dm-mod ?

Here's my cheatsheet for off-the-live-cd LUKS/LVM decryption:

# RESCUE ENCRYPTED PARTITION

# download and copy cryptsetup and lvm2 .deb files to /boot/rescue
# apt-get -d install cryptsetup lvm2
# see package files in /var/cache/apt/archives

# /dev/sda1 is my /boot.  /dev/sda2 is my crypto partition, containing
# volume group vg1 with logical partitions lvswap, lvroot, lvdata

# need packages cryptsetup (encrypted partition tools) and lvm2 (logical
# volume manager); install from internet (apt-get) or from local .deb files

# either use direct package installation (I pre-downloaded into /boot/rescue)...
sudo mkdir /media/boot
sudo mount /dev/sda1 /media/boot
sudo dpkg -i /media/boot/rescue/cryptsetup*.deb /media/boot/rescue/lvm2*.deb

# or use network-based package download/installation
sudo apt-get install cryptsetup lvm2

# insert kernel modules that we will need
sudo modprobe dm-crypt
sudo modprobe dm-mod

# unlock the sda2 partition and call it MYTAG
sudo cryptsetup luksOpen /dev/sda2 MYTAG
  Enter LUKS passphrase:
  key slot 0 unlocked.
  Command successful.

# now that we have unlocked the encryption, deal with the lvm

sudo vgscan                      # scan for all volume groups
  Reading all physical volumes. This may take a while...
  Found volume group "vg1" using metadata type lvm2

# make the vg1 volume group active; if you don't give it a volume group as
# an argument it'll make them all active
sudo vgchange -ay [vg1]

sudo lvscan             # list logical volumes and their /dev path
ACTIVE '/dev/vg1/lvswap' [2.00 GB] inherit
ACTIVE '/dev/vg1/lvroot' [10.00 GB] inherit
ACTIVE '/dev/vg1/lvdata' [60.00 GB] inherit

# mount a logical volume; don't do this if you need to run fsck on it
sudo mkdir /media/root
sudo mount /dev/vg1/lvroot /media/root

# to reverse the process and unmount everything, do the following

sudo umount /media/root

# the following command will issue a somewhat confusing message
sudo vgchange -an [vg1]
  0 logical volume(s) in volume group "vg1" now active

sudo cryptsetup luksClose MYTAG

---

### Post by F W Adams on 2009-02-23
Hi John,

I solved my #30 problem. As expected I felt a bit ridiculous.

Symtoms:
Boot up as normal, enter the password and get in.
Boot up from CD, not able to get access.

Solution:
There was an "@" sign in the password, and I am in the UK. These two things together caused the problem. It seems that on the main system this was fine, I'm not sure at what stage the kb was set up as a uk one. Anyway it was never a problem.

Booting from the CD at no stage is the kb changed to uk ( of course ). When I typed the @ it came out as ", I couldn't see it on the screen so didn't realise. This means I was always entering the wrong password even when hitting the right keys. Big relief now, I can get to change things from the CD now.

Your list looks useful, I'll take a copy, thanks.

---

