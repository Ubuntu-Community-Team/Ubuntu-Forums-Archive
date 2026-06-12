---
title: "HOWTO: install and reinstall on an encrypted LUKS/LVM system"
date: 2009-07-05
forum: Tutorials
---

### Post by John Wiersba on 2009-07-05
**Introduction**

This HOWTO describes how to encrypt your entire hard disk (except for the /boot partition) with separate partitions for swap, root, and /home.  Also described is a procedure for reinstalling the operating system without overwriting the separate /home partition.

Whole-disk encryption is especially useful for protecting personal data on a laptop, since a laptop can be easily stolen.  Once stolen, all the data on an unencrypted hard disk is easily recoverable by the thief.  The method shown here creates a LUKS-encrypted hard disk partition and uses LVM to create logical partitions within the encrypted physical partition for swap, root, and /home.  The encrypted partition is unlocked at boot time by GRUB running from a separate, unencrypted /boot partition.

For data security, it is important that the entire hard disk be encrypted (except for /boot), including the swap and root partitions.  This avoids problems associated with unencrypted confidential data leaking into swap or, for example, /tmp.  Having an LVM-managed swap partition inside the LUKS-encrypted partition is easier to setup and maintain than having separately-encrypted swap and root partitions.

Rather than upgrading the operating system when a new version is released, many people like to reinstall the entire operating system from scratch.  When reinstalling the operating system, there are two common choices:

   [LIST=1]
   [*] Reinstall the complete workstation
      - Backup the user data in /home
      - Backup various system configuration settings
      - Reinstall the entire workstation from scratch
      - Restore the user data to /home
      - Restore the system configuration settings


   [*] Reinstall the operating system only
      - Backup the user data in /home
      - Backup various system configuration settings
      - Reinstall the root partition only, not the /home partition
      - Restore the system configuration settings
   [/LIST]
Choice #1 (reinstalling the complete workstation) is simpler in concept, but may be slower than choice #2 if there is a lot of user data in /home, and it places 100% reliance on the system used to backup /home.  Choice #2 (reinstalling only the root partition) may be faster than choice #1 if there is a lot of user data in /home, and it places slightly less stress on the system used to backup /home, since it is not used during the reinstallation.

This HOWTO is a guide for those people who want to reinstall the operating system only, without restoring /home from backup (choice #2 above).  This requires creating a separate partition for /home, so that it is independent from the operating system contained in the root partition.

The current Ubuntu installers do not directly support reinstalling the operating system into a pre-existing encrypted partition.  This HOWTO shows you how to reinstall the operating system into a separate, LVM-managed root partition, while keeping the LVM-managed /home partition intact.

This HOWTO is based on MaddMatt's post at _[HOWTO: re-install / upgrade over existing dm-crypt / LUKS system]("http://ubuntuforums.org/showthread.php?t=1034910")_, which gives a similar process, but without some of the specific details.  I created this detailed list while testing MaddMatt's instructions in preparation for upgrading my laptop from Ubuntu 8.10 to 9.04.  The instructions have been tested on Ubuntu 8.10, 9.04, 9.10, 10.04 and are substantially the same.

[INDENT]**NOTE:  Whenever you perform a major alteration to your installation, such as reinstalling the operating system, you really _MUST_ be prepared for accidental failure.  This means that you _MUST_ back up your data before reinstalling!  This HOWTO shows you how to avoid restoring your home directory from backup, but it does not remove the need to back up your irreplacible data!**[/INDENT]

**Original install of Ubuntu 8.10, 9.04, 9.10, 10.04**

   [LIST=1]
   [*] Boot from Alternate Installer CD (not Desktop Installer)
   [*] Language: English
   [*] Main Menu: Install Ubuntu
   [*] Choose language: English
   [*] Choose a country: United States
   [*] Detect keyboard layout: No
   [*] Origin of the keyboard: USA
   [*] Keyboard layout: USA
   [*] [INSTALLATION CONTINUES]
   [*] Hostname: ubuntu
   [*] Time Zone: Eastern (or whatever)
      - [10.04] The time zone is detected slightly differently
   [*] Partition disks
      [LIST=1]
      [*] Select: Manual
      [*] Display shows:
         - Guided partitioning
         - ...
         - SCSI1 (0,0,0) (sda) - 80.0 GB ...
         - pri/log 80.0 GB FREE SPACE
         - ...
      [*] Select: pri/log 80.0 GB FREE SPACE
      [*] Select: Create a new partition
         [LIST=1]
         [*] New parition size: 200 MB
         [*] Select: Primary
         [*] Select: Beginning
         [*] Options for partition #1 of SCSI1 (0,0,0) (sda)
            [LIST=1]
            [*] Use as: Ext3 (or Ext4)
            [*] Format the partition: yes, format it
               - [10.04] Sometimes, this choice is not available
            [*] Mount point: /boot
            [*] Label: boot
            [*] Select: Done setting up the partition
            [/LIST]
      [*] Select: pri/log 79.8 GB FREE SPACE
         [LIST=1]
         [*] Select: Create a new partition
         [*] New parition size: 79.8 GB (i.e. all the rest of the space)
         [*] Select: Logical
         [*] Options for partition #5 of SCSI1 (0,0,0) (sda)
            [LIST=1]
            [*] Use as: Physical volume for encryption
            [*] Select: Done setting up the partition
            [/LIST]
            [/LIST]
      [*] Select: Configure encrypted volumes
         [LIST=1]
         [*] Write the changes to disk and configure encrypted volumes: Yes
            - [9.10, 10.04] Encrypted configuration actions: Finish
         [*] Encryption passphrase: [YOUR PASSPHRASE HERE]
         [*] Re-enter passphrase to verify: [YOUR PASSPHRASE HERE]
         [/LIST]
      [*] Select: "#1 79.8 GB" under "Encrypted volume (sda5_crypt)"
         [LIST=1]
         [*] Use as: Physical volume for LVM
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: Configure the Logical Volume Manager
         [LIST=1]
         [*] [10.04] Keep current partition layout and configure LVM: Yes
         [*] Select: Create volume group
            [LIST=1]
            [*] Volume group name: vg1
            [*] Devices for the new volume group:
               - use [SPACEBAR] to select /dev/mapper/sda5_crypt
               [/LIST]
         [*] Select: Create logical volume
            [LIST=1]
            [*] Select: vg1
            [*] Logical volume name: lvswap
            [*] Logical volume size: 2048 MB
            [/LIST]
         [*] Select: Create logical volume
            [LIST=1]
            [*] Select: vg1
            [*] Logical volume name: lvroot
            [*] Logical volume size: 10240 MB
            [/LIST]
         [*] Select: Create logical volume
            [LIST=1]
            [*] Select: vg1
            [*] Logical volume name: lvhome
            [*] Logical volume size: 66936 MB (i.e. all the rest)
            [/LIST]
         [*] Select: Finish
         [/LIST]
      [*] Select: "#1 66.9 GB" under "LVM VG vg1, LV lvhome"
         [LIST=1]
         [*] Use as: Ext3 (or Ext4)
         [*] Mount point: /home
         [*] Label: home
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: "#1 10.7 GB" under "LVM VG vg1, LV lvroot"
         [LIST=1]
         [*] Use as: Ext3 (or Ext4)
         [*] Mount point: / (root)
         [*] Label: root
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: "#1 2.1 GB" under "LVM VG vg1, LV lvswap"
         [LIST=1]
         [*] Use as: swap area
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: Finish partitioning and write changes to disk
      [*] Write the changes to disks: Yes
      [/LIST]
  [*] This will create
      - /dev/sda1: /boot
      - /dev/sda2: extended partition
      - /dev/sda5: encrypted logical partition
      - /dev/mapper/vg1-lvswap: swap
      - /dev/mapper/vg1-lvroot: / (root)
      - /dev/mapper/vg1-lvhome: /home
  [*] [INSTALLATION CONTINUES]
  [*] Full name for the new user: [YOUR NAME HERE]
  [*] Username for your account: [YOUR USERNAME HERE]
  [*] Choose a password for the new user: [YOUR PASSWORD HERE]
  [*] Re-enter password to verify: [YOUR PASSWORD HERE]
  [*] Set up an encrypted private directory: No
  [*] [INSTALLATION CONTINUES]
  [*] HTTP proxy information: [LEAVE BLANK]
  [*] [INSTALLATION CONTINUES]
  [*] [10.04] Install the GRUB boot loader to the master boot record: Yes
  [*] Is the system clock set to UTC: Yes
  [*] Installation is complete: Continue
  [*] [REBOOT]
  [*] Enter passphrase to unlock ... (sda5_crypt): [YOUR PASSPHRASE HERE]
      - [10.04] Unlocking the disk /dev/disk/by-uuid/... (sda5_crypt)
      - [10.04] Enter passphrase:  [YOUR PASSPHRASE HERE]
  [*] Enjoy your Ubuntu installation!
  [/LIST]
  [/LIST]
**Reinstall Ubuntu 9.04, 9.10, 10.04 over existing encrypted LUKS/LVM partitions**

Following your encrypted LUKS/LVM installation (above), you decide to reinstall the operating system, perhaps to upgrade to a different version.  In order to avoid restoring your /home directory from backup, you can use the following procedure.  This procedure will overwrite the root and /boot partitions, but will not overwrite /home.  Of course, you still _**MUST**_ make a backup (or two!) of /home before proceeding, just in case.

Before proceeding with the reinstallation, you need to know which physical partition is your encrypted partition.  In the sample installation above, it is sda5.  This information is available to you in the prompt, during the boot process, when you are asked to enter the passphrase.  For example, if sda5_crypt is being unlocked by GRUB during the boot process, sda5 is the encrypted partition.

Ultimately, you will need to know the UUID corresponding to the encrypted partition (sda5 in this case), in order to generate an entry in /etc/crypttab.  The easiest way to prepare to generate the /etc/crypttab entry is shown in the steps below, which must be completed before starting the reinstallation.  An alternate way to generate the entry in /etc/crypttab is shown in step 15 of the Repair section below, but you still need to know the name of your encrypted partition in order to use it.

   [LIST=1]
   [*] First, boot your current installation, in order to save a copy of /etc/crypttab, which will be restored after the reinstall.  Since /etc/crypttab is kept in the root partition, and the root partition is overwritten during the reinstall, this step needs to be completed before reinstalling.  The contents of crypttab look like:

         ```

# <target name>   <source device>   <key file>   <options>
sda5_crypt /dev/disk/by-uuid/[HEX UUID] none luks
```
Run the following command line from a Terminal window (Applications -> Accessories -> Terminal):

         ```

$ sudo cp /etc/crypttab /home/crypttab_copy
```
This file (/home/crypttab_copy) can be deleted once the reinstallation is complete.


   [*] Now, start the reinstallation.  Boot from the Alternate Installer CD (not the desktop Installer) for the new version you want to install (e.g. 10.04)
   [*] Language: English
   [*] Main Menu: Rescue a broken system
   [*] Choose language: English
   [*] Choose a country: United States
   [*] Detect keyboard layout: No
   [*] Origin of the keyboard: USA
   [*] Keyboard layout: USA
  [*] Hostname: ubuntu
  [*] Time Zone: Eastern (or whatever)
      - [10.04] The time zone is detected slightly differently
  [*] Passphrase for /dev/sda5: [YOUR PASSPHRASE HERE]
  [*] Device to use as root file system: /dev/vg1/lvroot
  [*] Rescue operations: [Go Back]
  [*] Device to use as root file system: [Go Back]
  [*] Select: Partition disks
      [LIST=1]
      [*] Select: Manual
      [*] Select: "#1 primary 197.4 MB B ext3" under SCSI1 (0,0,0) (sda)"
         [LIST=1]
         [*] Use as: Ext4
         [*] Mount point: /boot
         [*] Label: boot
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: "#1 10.7 GB ext3" under "LVM VG vg1, LV lvroot"
         [LIST=1]
         [*] Use as: Ext4
         [*] [10.04] Format the partition, if necessary
         [*] Mount point: / (root)
         [*] Label: root
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Select: "#1 66.9 GB ext3" under "LVM VG vg1, LV lvhome"
         [LIST=1]
         [*] Note the current filesystem type: Ext3 or Ext4
         [*] Use as: (Select the same current value: Ext3 or Ext4)
         [*] Format the partition: **no, keep existing data !!**

[INDENT]**Do not format your existing /home partition !!**[/INDENT]

         [*] Mount point: /home
         [*] Select: Done setting up the partition
         [/LIST]
      [*] Finish partitioning and write changes to disk
      [*] Write the changes to disks: Yes
      [/LIST]
  [*] [INSTALLATION CONTINUES]
  [*] Full name for the new user: [YOUR NAME HERE]
  [*] Username for your account: [YOUR USERNAME HERE]
  [*] Choose a password for the new user: [YOUR PASSWORD HERE]
  [*] Re-enter password to verify: [YOUR PASSWORD HERE]
  [*] [INSTALLATION CONTINUES]
  [*] HTTP proxy information: [LEAVE BLANK]
  [*] [INSTALLATION CONTINUES]
  [*] Choose software to install: use [SPACEBAR] to select Ubuntu desktop
  [*] [INSTALLATION CONTINUES]
  [*] Install GRUB: Yes
  [*] Is the system clock set to UTC: Yes
  [*] [INSTALLATION COMPLETE]
  [*] Alternate Installer CD is ejected, but do not remove it
  [*] Select: Continue with reboot
  [/LIST]
**Repair the boot image after reinstallation to unlock LUKS encrypted partition**

Now it is time to repair the /boot/initrd image to automatically unlock the encrypted partition during the GRUB boot process.  In step 15 below, you will need to modify /etc/crypttab with the data kept in /home/crypttab_copy, which was created above before starting the reinstallation.  If you did not make a copy of /etc/crypttab, you can regenerate it by following the alternate procedure given in step 15.

   [LIST=1]
   [*] Boot from the Alternate Installer CD again (not desktop Installer)
   [*] Language: English
   [*] Main Menu: Rescue a broken system
   [*] Choose language: English
   [*] Choose a country: United States
   [*] Detect keyboard layout: No
   [*] Origin of the keyboard: USA
   [*] Keyboard layout: USA
   [*] Hostname: ubuntu
  [*] Time Zone: Eastern (or whatever)
      - [10.04] The time zone is detected slightly differently
  [*] Passphrase for /dev/sda5: [YOUR PASSPHRASE HERE]
  [*] Device to use as root file system: /dev/vg1/lvroot
  [*] Rescue operations: Execute a shell in /dev/vg1/lvroot
  [*] Select: Continue
  [*] Enter the following commands (running as root):

```

# mount

         # NOTE: Depending on the version of the installer, the
         # output may show that:
         #  - /boot is mounted from /dev/sda1, and
         #  - /home is mounted from /dev/mapper/vg1-lvhome
         # However, they might NOT be mounted, so ...

# ls -l /boot     # shows no files, so not really mounted
# mount /boot     # may "fail" if already mounted; that's ok
# mount /home     # may "fail" if already mounted; that's ok

         # NOTE: if you did not save a copy of crypttab in a
         # previous step, follow the instructions given just below
         # to recreate the entry in /etc/crypttab

# cat /home/crypttab_copy >>/etc/crypttab    # restore from backup
# cat /etc/crypttab              # to check the contents of crypttab
# update-initramfs -k all -c -v

         # watch the output to make sure update-initramfs succeeded

# exit   # exit busybox back to the Rescue menu

```
If you did not save a copy of /etc/crypttab before reinstallation, you can still recreate it, if you know the name of the encrypted partition (e.g. sda5).

         ```

# ls -l /dev/disk/by-uuid | grep sda5
lrwxrwxrwx 1 root root 10 May 19 09:10 [HEX UUID] -> ../../sda5

         # This hex UUID is what is needed to recreate /etc/crypttab

# crypttab_entry="sda5_crypt /dev/disk/by-uuid/[HEX UUID] none luks"
# echo $crypttab_entry  # to check that you've typed it right
# echo $crypttab_entry >>/etc/crypttab
# cat /etc/crypttab     # to check the contents of crypttab
```

  [*] Select: Reboot the system
  [*] Quickly remove the Alternate Installer CD, since it won't be released before rebooting
  [*] After rebooting, you can delete /home/crypttab_copy
  [/LIST]
**How to manually unlock and mount an encrypted LUKS/LVM partition**

This procedure might come in handy if you have to rescue your data from an encrypted backup or from your workstation, if it won't boot properly.

   [LIST=1]
   [*] Boot from an Ubuntu Live CD (Desktop Installer) with a working connection to the internet
   [*] Open a Terminal window (Applications -> Accessories -> Terminal).  Use the Terminal window to type the following commands

   ```

$ sudo apt-get install cryptsetup lvm2
# - This requires a live internet connection
# - Answer yes to continue if prompted

$ sudo cryptsetup luksOpen /dev/sda5 MYTAG
# - This command opens the encrypted partition
# - Enter your passphrase when prompted

$ sudo vgchange -ay
# - Makes all volume groups active
# - If you don't want to make them all active, you can run vgscan to get the
#   name of your volume group, followed by vgchange for a specific volume group.
#     $ sudo vgscan
#     $ sudo vgchange -ay [VOLUME GROUP NAME]

$ sudo lvscan
# - Note the name of the logical volume containing the partition you want to mount

$ sudo mount /dev/[VOLUME GROUP NAME]/[LOGICAL VOLUME NAME] /mnt

```
   [*] Now you can explore the mounted partition under /mnt.  When you are done, you can unmount it by typing the following commands in a Terminal window

```

$ sudo umount /mnt
$ sudo vgchange -an
# - Makes all volume groups inactive
# - Or use a specific volume group name if you want:
#     $ sudo vgchange -an [VOLUME GROUP NAME]

$ sudo cryptsetup luksClose MYTAG
# - This command closes the encrypted partition

```
      [/LIST]

---

### Post by jpeddicord on 2009-07-07
Very well organized lists. :) Approved, and thank you for contributing to Tutorials & Tips.

---

### Post by ducksun43 on 2009-07-07
[http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html](http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html) is also quite good; there is also a link to page that shows howto setup ecryptfs

---

### Post by phip on 2009-07-08
I am trying to follow the second set of instructions, "Install Ubuntu 9.04 (Jaunty Jackalope) over existing encrypted LUKS/LVM partitions" to install over partitions created by Fedora. I can't get past step 12 however, it keeps prompting me for the passphrase over and over.

I know that these partitions were set up with cryptsetup cypher aes-cbc-essiv:sha256. I also notice that if I drop into installer shell and issue cat /proc/crypto, it only reports stdrng and md5. By comparison, my Fedora 11 box reports: sha256, sha224, cbc(aes), ecb(arc4), arc4, xts(aes), aes, stdrng, crc32c, sha1, md5.

Could this be the problem? The kernel included with 9.04 alternate cd does not include the crypto modules I need?

---

### Post by John Wiersba on 2009-07-08
My procedure was tested as written on an encrypted partition from Hardy.  I don't know how that may be different from what Fedora has.  As you suggest, it's probably different crypto/cipher settings.  Maybe dmesg from the command line would tell you (or you could look at the logs in /var/log).  Here's my Jaunty /proc/crypto:

$ cat /proc/crypto
name         : ecb(arc4)
driver       : ecb(arc4-generic)
module       : ecb
priority     : 0
refcnt       : 3
selftest     : passed
type         : blkcipher
blocksize    : 1
min keysize  : 1
max keysize  : 256
ivsize       : 0
geniv        : <default>

name         : arc4
driver       : arc4-generic
module       : arc4
priority     : 0
refcnt       : 3
selftest     : passed
type         : cipher
blocksize    : 1
min keysize  : 1
max keysize  : 256

name         : sha256
driver       : sha256-generic
module       : sha256_generic
priority     : 0
refcnt       : 1
selftest     : passed
type         : digest
blocksize    : 64
digestsize   : 32

name         : sha224
driver       : sha224-generic
module       : sha256_generic
priority     : 0
refcnt       : 1
selftest     : passed
type         : digest
blocksize    : 64
digestsize   : 28

name         : cbc(aes)
driver       : cbc(aes-asm)
module       : kernel
priority     : 200
refcnt       : 2
selftest     : passed
type         : givcipher
async        : yes
blocksize    : 16
min keysize  : 16
max keysize  : 32
ivsize       : 16
geniv        : chainiv

name         : cbc(aes)
driver       : cbc(aes-asm)
module       : cbc
priority     : 200
refcnt       : 2
selftest     : passed
type         : blkcipher
blocksize    : 16
min keysize  : 16
max keysize  : 32
ivsize       : 16
geniv        : <default>

name         : aes
driver       : aes-asm
module       : aes_i586
priority     : 200
refcnt       : 3
selftest     : passed
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

name         : aes
driver       : aes-generic
module       : aes_generic
priority     : 100
refcnt       : 1
selftest     : passed
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

name         : stdrng
driver       : krng
module       : kernel
priority     : 200
refcnt       : 2
selftest     : passed
type         : rng
seedsize     : 0

name         : md5
driver       : md5-generic
module       : kernel
priority     : 0
refcnt       : 1
selftest     : passed
type         : digest
blocksize    : 64
digestsize   : 16

---

### Post by Colt45 on 2010-05-01
could someone update this thread for lucid?

---

### Post by Colt45 on 2010-05-01
BE VERY CAREFUL when using this guide with Ubuntu 10.04.  If you have a hardware RAID controller attached to your system that doesn't allow booting off arrays, this is important for you.

The Ubuntu installer may assign the RAID controller device as /dev/sda.  If that happens you will need to pay careful attention to the last step when running the manual installer.

Once you come to the final steps of John's guide, in Ubuntu 10.04 a grub2 prompt will appear. You are forced with choosing yes/no to "install grub on master boot record"  Choose NO.

The issue here is that choosing yes causes Ubuntu installer to automatically write Grub2 to the MBR on the first recognized device which in this case was the RAID controller array(/dev/sda).  If your RAID controller does not allow for booting from an array, you're now caught in a situation where grub2 entry in the MBR located on /dev/sda (RAID controller, which can't be used a boot device). This results in the bootloader being inaccessible and a black screen on every reboot.

The solution here is...

1. write down the device (/dev/sdb etc) you will install Ubuntu on.

2. when you get to the final step where the installer asks if you want to install to the MBR, choose NO.  This will put you at a screen "configuring grub-pc".

3. Here you will enter the the device you installed Ubuntu on.  In this case it was "/dev/sdb".

4. continue install, Ubuntu will finish, then reboot.

---

### Post by John Wiersba on 2010-05-05
The procedure remains essentially the same with Lucid 10.04 as with previous versions.  I will update this post soon to include the minor changes.

I will also add a note to be careful if you're using a RAID configuration (which I haven't tested).

---

### Post by holocene on 2010-05-12
Could someone direct me to info on how to change the boot password for whole disk encryption on Lucid Lynx? This is the encryption installed from the text based installer. 

Best Regards
Steve.

---

### Post by John Wiersba on 2010-05-13
> **holocene said:**
> Could someone direct me to info on how to change the boot password for whole disk encryption on Lucid Lynx? This is the encryption installed from the text based installer.

Steve, I believe this is what you're talking about (from my notes):

To change encryption passphrase:

# note: the device name is whatever shows up as /dev/mapper/sda2_crypt

# add a key
sudo cryptsetup -y luksAddKey /dev/sda2

# remove a key
sudo cryptsetup luksRemoveKey /dev/sda2

---

### Post by holocene on 2010-05-16
John,

I will try this but I am scared it will hose the system. I need to make a backup! In 9.04, I encrypted my home directory upon install, and after a glitch (now fixed I think), I never saw it again. I know this is a different issue though. 

I have a related question, I think. If you go to System | Administration | Disk Utility, then select the line (3rd down on mine) corresponding to the actual hard drive (called 320 GB Hard Disk and then ATA WDC ...), there is an option at the bottom called "Change Passphrase". 

I searched help on this but did not really get a good idea of what it does. Do you know? 

Is this an alternative way (to the way you explained) to change the passphrase? 

Thanks so much.
Steve. 



> **John Wiersba said:**
> Steve, I believe this is what you're talking about (from my notes):

To change encryption passphrase:

# note: the device name is whatever shows up as /dev/mapper/sda2_crypt

# add a key
sudo cryptsetup -y luksAddKey /dev/sda2

# remove a key
sudo cryptsetup luksRemoveKey /dev/sda2

---

### Post by John Wiersba on 2010-05-16
Steve, 

I don't have "Disk Utility" show up in my version (currently running 9.04), but I'd guess that it does something similar to what my command lines do.

I test all these commands on a separate crash-n-burn machine several times before trying them on my day-to-day machine.  Like you, I'd be scared to test them on a machine that I need to keep running.

And you're right.  Having a backup is key to your peace of mind.  Buy an external drive (or two!), create an encrypted partition on it, and rsync your data to it.  Test that you can remount it from a different machine.

-- John

---

### Post by radiobuzzer on 2010-06-30
Thanks, this tutorial has been very helpful. Unfortunately I followed it and the new system doesn't do any hibernation. This obviously has to do with the fact that we encrypted the swap disk.

I 've seen many posts in many forums that say that this is possible, mainly but directly editing specific ubuntu conf files.

Is there any hint on how exactly this would be possible, given the instructions above?

---

### Post by John Wiersba on 2010-06-30
Radiobuzzer,

Sorry, but I don't know the solution to your hibernation issue.  The method I showed (above) is pretty standard for creating a fully-encrypted installation.  The tricky part is reinstalling the OS without needing to restore /home.  

However, once you have a fully-encrypted installtion, there may be tweaks needed to get things like hibernation working on your hardware.  Indeed, you may need to directly edit various configuration files.  You could try searching for some variation of "encrypted hibernation" for more information on this.  

If, for some reason, you can't get hibernation working when your swap is encrypted, you could consider not encrypting swap by creating a extra partition for swap outside the LUKS-encrypted container.  This weakens the security of your installation, but you may consider a working hibernation feature more important than an encrypted swap.

---

### Post by omelette on 2010-07-18
Being curious, I opted for home-folder encryption when installing 10.04, and when the key was generated, thought I read that I could retrieve it again from the command-line - so never bothered saving it.  After more idiocy on my part, I managed to screw up my installation so badly that I had to reinstall it from a backup.

So all is well again.  However, said-backup also has the encrypted home-folder, (obviously!) so my question is, did I read right at the time - once logged in, can I retrieve the key from the command-line so I can write it down this time?

---

### Post by John Wiersba on 2010-07-18
> **omelette said:**
> Can I retrieve the key from the command-line so I can write it down this time?

Unfortunately, I don't have any experience with encrypted home directories, since it's not a useful feature in a single-user, fully-encrypted installation (such as a laptop).  Maybe someone else will know how to retrieve the decryption key.  Also, I would suggest using full encryption for your backups, as opposed to encrypting only certain files/directories.

---

### Post by omelette on 2010-07-18
Thanks for the reply.  As it is my laptop that is at issue, I am surprised to hear that directory-level encryption is inadequate - as the laptop is used only be myself, I would have thought everything was perfectly secured, bar file-access logs etc. stored in /vars, /etc and the like!

I was just responding to the supplied Ubuntu installation disk's responses which doesn't offer the option of disk-level encryption - but then I guess you know that, hence your HOWTO! :)

---

### Post by John Wiersba on 2010-07-18
IMHO, directory-level encryption is inadequate for a laptop that has sensitive data on it (that you would be worried about if your laptop was stolen).  For example, swap and /tmp will not be encrypted.

But I don't see any extra benefit of directory-level encryption when the entire hard disk is already encrypted; it just creates extra failure points (as you discovered).

---

### Post by omelette on 2010-07-18
Ah yes, I forgot about swap & tmp - good point!

btw, I have just taken the not-too-tedious route of re-installing Ubuntu from scratch again (still just home-directory encryption) and yes, the encryption key can be retrieved from the command-line - simply;

***"ecryptfs-unwrap-passphrase"***

---

### Post by Phoenix_Swelter on 2010-10-11
Thanks so much for this guide. Everything is working like a charm on Lucid. But I would like to make one minor change to my setup - perhaps someone here could lead me through the steps.

When setting up the encrypted LUKS volume, and it was time to set up the user accounts, while following the steps, I chose to create an unencrypted account for myself. I have decided now that, because I have other users on my system, I would like to encrypt my home directory. Can anyone lead me through the necessary steps to make that change my ~/ directory from unencrypted to encrypted?

---

### Post by John Wiersba on 2010-10-12
> **Phoenix_Swelter said:**
> I have decided now that, because I have other users on my system, I would like to encrypt my home directory. Can anyone lead me through the necessary steps to make that change my ~/ directory from unencrypted to encrypted?

I would suggest that you probably don't need an encrypted home directory, if you already are using encrypted LUKS volumes.  The primary use case (in my opinion) for these encrypted directories and volumes is to prevent a thief from stealing your data if he is able to steal your hardware.  Your encrypted LUKS volumes already take care of that.  To protect yourself from other legitimate concurrent system users, file system permissions would normally be the tool of choice.

If another user can gain root on your system (via sudo or any other means), file system permissions won't be sufficient.  However, neither will any other method, including encrypted home directories.  So, I would suggest sticking with file system permissions.  However, if you want to look further at encrypted home directories, you could reference this page: [https://wiki.ubuntu.com/EncryptedHomeFolder]("https://wiki.ubuntu.com/EncryptedHomeFolder")

---

### Post by Phoenix_Swelter on 2010-10-12
> **John Wiersba said:**
> I would suggest sticking with file system permissions.[]("https://wiki.ubuntu.com/EncryptedHomeFolder")

Yep - I do believe you are correct. Thank-you.

---

### Post by tomgibson on 2011-02-22
Has anyone successfully followed this HowTo booting from MDADM Raid partitions? I am able to boot from MDADM + LVM or LVM + Encryption, but not all three. Having created two MD devices, one unecrypted for /boot (md0) and one for the encrypted VG (md1), the system doesn't properly assemble the encrypted VG array and goes to an initramfs shell with md1 assembled but inactive. "mdadm --stop /dev/md1" followed by "mdadm --scan --assemble" correctly assembles and activates md1 then the system can boot, but is there any way to avoid this?

EDIT: Have verified that in fact this works when using the 10.04.2 installation disk. Previously I was using 10.04.1. Also updating an installation using the MDADM + LUKS + LVM combination from a 10.04.1 disk or earlier to the latest packages fixes the problem too.

---

### Post by Widgit on 2011-03-18
Hi Guys,

I'm having a real headache with this.  I've followed these instructions multiple times using the ubuntu 10.10 alternative release to try and setup a new install on a laptop.

I'm getting an error that says something very similar to:

"error couldn't read file.

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)"

If you guys could provide any assistance with this I'd be extremely grateful.

---

### Post by within on 2011-04-07
Thanks very much for the well done HOWTO.

Works like a charm on my brand new laptop with Lucid.

---

### Post by vangop on 2011-11-17
awesome guide really.
Just one question - can someone explain the difference when mounting /dev/vg1/root and /dev/mapper/vg1-root
I've read that encrypted partition should be addressed via /dev/mapper/xxx, but here we use /dev/vg1/xxx

---

### Post by John Wiersba on 2011-11-17
> **vangop said:**
> Just one question - can someone explain the difference when mounting /dev/vg1/root and /dev/mapper/vg1-root
I've read that encrypted partition should be addressed via /dev/mapper/xxx, but here we use /dev/vg1/xxx

On my current system:

[FONT="Courier New"]$ ls -l /dev/vg1/lvroot /dev/mapper/vg1-lvroot /dev/dm-2
brw-rw---- 1 root disk 252, 2 Nov 17 20:03 /dev/dm-2
lrwxrwxrwx 1 root root      7 Nov 17 20:03 /dev/mapper/vg1-lvroot -> ../dm-2
lrwxrwxrwx 1 root root      7 Nov 17 20:03 /dev/vg1/lvroot -> ../dm-2[/FONT]

/dev/mapper/vg1-lvroot and /dev/vg1/lvroot are the same; both are symlinks to /dev/dm-2.  Does that help answer your question?

---

### Post by vangop on 2011-11-18
Thanks, it surely does :)

---

### Post by madone1 on 2012-01-17
Hi
I have problem booting my LVM after i have tryed steps for Reinstalling Ubuntu 9.04, 9.10, 10.04 over existing encrypted LUKS/LVM partitions.
Every command described here is coming true without error including update of initramfs. Re using existing /home works. When i mount it manuly i see files on it. But i cant boot in LVM
I am geting this error

```
Loading initial ramdisk...
Volume group "ubuntu" not found
Skiping volume group "ubuntu"
and same error for all logical volumes ubuntu/root ubuntu/swap
then
ALERT! /dev/mapper/ubuntu-root does not exist ! Dropin in to shell !
```
and i end up in busybox initramfs

---

### Post by John Wiersba on 2013-01-13
From [http://ubuntuforums.org/showthread.php?t=2077346]("http://ubuntuforums.org/showthread.php?t=2077346"):

[INDENT]Ubuntu no longer has an alternate install CD but the other versions still do. You can get Lubuntu's alternate CD and the install the package ubuntu-desktop to get Ubuntu. You can grab the torrent for Lubuntu's alternate CD here: [http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/]("http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/")

Another option might be to try doing the same thing with the server image.[/INDENT]

---

### Post by tuliouel on 2013-03-06
This didn't work for me. 
The  solution described using the alternate  install was done and the system was installed but, since my user  directory was encrypted in /home/username/.Private using encryptfs, it  failed to mount, and I didn't find a workaround yet, since no username  nor any passwork seems to work, even typing the exact terms I entered  during install. So I can only access a Guest account, which dosn't allow  me to access any Terminal nor sudo neither any graphical interface that  requires root.
It seems that alternate install doesn't have the necessary packages to deal with encryptfs, since it doesn't understands its partition type. I tried to get into recovery other times to try to figure out something in the fstab, but nothing works. Even adding /home/username/.Private /home/username encryptfs defaults 0 0 makes the installed system to tells me it is not a valid partition.
Maybe you should advise people, by editing the thread, not to try this in this case, or sugesting a workaround, that maybe would be copying no only cryptfs but also fstab, or maybe installing other packages. All I know is that more people is having a hard time with this thing, and in times when ubuntu wants to go to the crowd, in cell phones, things like these shouldn't happen anymore. The closer canonical gets from people willing to pay for it, the least it can just rely in the "use it in an 'as is' basis" clause.

---

### Post by John Wiersba on 2013-03-07
Tuliouel, I'm not sure of the scenario where one would want to use an encrypted user directory given that one is also using whole disk encryption.  Unless I'm misunderstanding how the encrypted user directories work, I don't think it provides any additional security.  But in any case, it is an allowed scenario and you seem to have hit an issue with it.  I would like to add a comment in my original tutorial warning about the possibility of data loss in this scenario, but I'm no longer able to edit my original post.  The powers that be are suggesting that tutorials be moved to one of the wikis instead of being maintained in the forums.  Maybe someday I'll add an up-to-date version of this tutorial to the wiki.  In the meantime, hopefully other users will see your post and be warned about this scenario.

---

### Post by jscordia on 2013-05-01
[SIZE=3][SIZE=2][SIZE=2]Hi everybody, hi John [SIZE=2]Wiersba[/SIZE], I have just installed a working Kubuntu 13.04[SIZE=2], w[SIZE=2]hile keeping my encr[SIZE=2]ypted par[SIZE=2]ti[SIZE=2]tions (some encapsulated in a Logical [SIZE=2]Volume Manager), only [SIZE=2]form[SIZE=2]atting / and /boot. As I have used the hints of John, and another tip corresponding to a[SIZE=2]n Ubuntu bug (see b[SIZE=2]elow),[/SIZE][/SIZE] [SIZE=2]here is m[SIZE=2]y summary of the installation**:**[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

[SIZE=3]**Installation of Kubuntu through Lubuntu**[/SIZE]

At the beginning, my idea was to use the Kubuntu 13.04 installer, using the tip explained at [https://wiki.kubuntu.org/RaringRingtail/Alpha2/Kubuntu](https://wiki.kubuntu.org/RaringRingtail/Alpha2/Kubuntu):

> The desktop image installer cannot unlock existing encrypted (LUKS) volumes. If you need to make use of existing encrypted volumes during partitioning, then use the "Try Ubuntu without installing" boot option to start a live session, open the encrypted volumes (for example, by clicking on their icons in the Unity launcher), enter your password when prompted to unlock them, close them again, and run ubiquity to start the installer. (1066480) 

refering to bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1066480](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1066480). Indeed, this technique works: by mounting my two encrypted partitions in Dolphin from the KDE live CD:


[LIST]
[*]one for /home on a HDD 
[*]another one for a Logical Volume Manager on a SSD containing /home/local (separated from /home to benefit from the speed of the SSD for scientific computing), /, /usr/local. 
[/LIST]

I was able to see them in the installer (run from the icon on the KDE desktop). Without mounting them before, only the various /dev/sda* and /dev/sdb* partitions are seen, not the encrypted volumes and LVM. However, the installer segfaults more or less rapidly when assigning paths to logical volumes. I found no easy workaround, so my next idea was to do the same by using a live distribution of Ubuntu instead of Kubuntu. Indeed the process is almost the same, and the installation works like a charm. However, at the reboot, I obtain an error: Linux does not find the logical volume for /. The solution was to use the technique indicated in the HOWTO located at [http://ubuntuforums.org/showthread.php?t=1205372](http://ubuntuforums.org/showthread.php?t=1205372), i.e. to use the “rescue mode” of the text installer to:


[LIST]
[*]make a suitable /etc/crypttab file 
[*]run update-initramfs as indicated in aforementioned HOWTO. 
[/LIST]

But I did not realize that at this time, and instead I had the idea to use the old good text installer shipped with Lubuntu, but unfortunately no more distributed with Ubuntu and Kubuntu. So I downloaded Lubuntu, put it on a USB key, installed it (the logical volumes and partitions are detected without any problem by this text installer; to do that it asks for the encryption passwords). After having updated /etc/crypttab and run update-initramfs, it booted perfectly. Now, to obtain a working KDE system, I had to do the two following things from the “rescue mode” of the installer:


[LIST]
[*]use "adduser" to add my user account. Indeed, for some reason only a guest account appeared after a reboot. 
[*]put this new user in the “sudo” group so as to be able to run root commands. 
[*]install the following packages
[LIST]
[*]kde-standard which is the “KDE Plasma Desktop and standard set of applications” (not kde-plasma-desktop, which is the “KDE Plasma Desktop and minimal set of applications”) 
[*]kde-workspace-randr for display management to appear in KDE system settings. 
[*]and possibly, if not installed by kde-standard (at the beginning, I had installed by error kde-plasma-desktop instead of kde-standard): muon, update-manager-kde, kontact, kmix, muon-installer, kmag. 
[/LIST]
   
[/LIST]

---

### Post by mk4umha on 2013-06-20
Anyone have issues with installing 12.04.2 and it not prompting to enter a username and password?

---

### Post by rom1v on 2013-09-18
Hi,

For reinstalling, I followed your reinstalling tuto (on Debian Wheezy).

The command:
```
update-initramfs -k all -c -v
```
says:
```
Available versions:  3.2.0-4-486
Execute: /usr/sbin/update-initramfs -c -k "3.2.0-4-486" -b /boot -v
Cannot create version 3.2.0-4-486: already exists
```

Therefore, I tried:
```
update-initramfs -k all -u -v
```
I "worked", but after a reboot, the system does not ask for my passphrase, and thus cannot boot.

Thank you for your help.

---

### Post by John Wiersba on 2013-09-18
Well, I've never seen that error before.  In any case, maybe these notes will help you recover.  These notes are meant for reinstalling an OS like Mint into an already-existing LUKS/LVM container.  You will need to know which partition has the LUKS/LVM container and your passphrase to unlock it.  In the notes below, that partition is referred to as sda5.  You can skip the parts about installing.

```

To install into already-created LVM containers within encrypted partition

Boot desktop CD, open terminal, and install missing packages as needed:

   # not needed in mint: sudo apt-get install cryptsetup lvm2
   # not needed in mint: sudo modprobe dm-crypt

Now set up the LVM and crypto partitions with the command line tools. If you
already have Ubuntu installed on a standard LVM-on-LUKS, this is as easy as:

   sudo cryptsetup luksOpen /dev/sda5 sda5_crypt

or whichever partition is the encrypted LVM PV. This should automatically
create the LVM LVs in /dev/mapper/.

   cd /dev/mapper
   ls -l

NOW DO THE INSTALL: Start ubiquity with manual partitioning, and use the
existing partitions; keep /home etc. as they are, and reformat the root
partition in the LVM. Do not reboot immediately; your system will not boot!
After installation, mount the newly installed target system:

   # sudo mount /dev/mapper/ubuntu*-root /mnt
   sudo mount /dev/mapper/vg1-lvroot2 /mnt
   sudo chroot /mnt mount /proc
   sudo mount --bind /dev /mnt/dev
   sudo chroot /mnt mount /boot

Create an appropriate crypttab:

   echo "sda5_crypt UUID=$(sudo blkid -s UUID -o value /dev/sda5) none luks" |
      sudo tee -a /mnt/etc/crypttab

# or alternatively on older systems:

   # OLD: echo "sda5_crypt UUID=$(sudo vol_id --uuid /dev/sda5) none luks" |
   #    sudo tee -a /mnt/etc/crypttab

Rebuild the ramdisk:

# This only applies to Ubuntu version < 11.04.  Install a few missing packages
# into the target system (this will also take care of updating the initramfs):

   # OLD: sudo chroot /mnt apt-get install cryptsetup lvm2 dmsetup

This only applies to Ubuntu version >= 11.04.  Run the following command to
rebuild the ramdisk:

   # The following line (update-initramfs) causes a warning:
   #  Warning: No support for locale: en_US.utf8
   #
   # This is caused by the locales being stored in (/mnt)/usr/lib/locale:
   #     C.UTF-8
   #     locale-archive
   #
   # This next command (--no-archive) will delete the archive and replace it
   # with the .utf8 files
   #
   #     sudo chroot /mnt locale-gen --purge --no-archive    # remove archive
   #
   # To get the archive back:
   #     sudo chroot /mnt locale-gen --purge                 # recover archives
   #
   # After rebooting, try:
   #     sudo dpkg-reconfigure locales
   #     sudo update-locale LANG=en_US.UTF-8
   # ??? sudo update-locale LANG=en_US.utf8     # I don't think this is right

   sudo chroot /mnt update-initramfs -u

Create a backup copy of the master boot record

   sudo chroot /mnt dd bs=512 count=1 if=/dev/sda of=/boot/mbr.bin

Create a backup copy of /boot

   cd /boot    # or /mnt/boot
   sudo tar cvzf /tmp_boot.tgz .
   sudo mv /tmp_boot.tgz ./boot.tgz

Unmount the target system:

   sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt

Reboot into your newly installed system.


```

---

### Post by jscordia on 2014-04-26
I have just installed (K)Ubuntu 14.04 through ubiquity, and using some of the tips you give in your Howto, John. I have made a small installation report at the following location

[http://julien-scordia.org/?p=119]("http://julien.scordia.free.fr/?p=119")

---

### Post by John Wiersba on 2014-04-28
Thanks for the report Julien!  It would be nice if these use-cases were better integrated with the installation process.  I'm sure it will get there someday...

---

