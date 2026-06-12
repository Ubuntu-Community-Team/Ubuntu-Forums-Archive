---
title: "Upgrade from Ubuntu 14.04.6 LTS to 18.04"
date: 2019-08-05
forum: Server Platforms
---

### Post by gerald17006 on 2019-08-05
Dear All,
I have a server which is:
[B]
Distributor ID: Ubuntu
Description: Ubuntu 14.04.6 LTS
Release: 14.04
Codename: trusty[/B]

and i want to upgrade to 18.04 LTS but i am receiving this error:

[B]calculating the changes

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.[/B]
**Restoring original system state**

Please how can i find this issue?

---

### Post by Impavidus on 2019-08-05
Have you installed any "unofficial software packages not provided by Ubuntu"? If so, remove those first.

Furthermore, you're dealing with an [EOL upgrade](https://help.ubuntu.com/community/EOLUpgrades). That means that your system is already dead, which makes things a bit harder. Best to upgrade before it reaches end of life.

Upgrading will bring you to 16.04. To get to 18.04, you need to upgrade twice. It's usually better to do a fresh install, but I don't know your system.

---

### Post by cruzer001 on 2019-08-05
It can be done, IMO a fresh install is better.

---

### Post by rsteinmetz70112 on 2019-08-07
I  think you need to be more specific about what you did to get the error you got.

Basically to upgrade an EOL system like 14.04. you need to make sure you have the correct repositories available, update the system, upgrade the system then do-release-upgrade. That will get you to 16.04. If there are any issues fix them before going forward. Once you have 16.04 up and running you should then be able to update the system, upgrade the system and do-release-upgrade. These upgrades a not foolproof and you can run into problems.

If you don't understand this general description please post specific questions and we can try to help.

---

### Post by gerald17006 on 2019-08-09
Dear all,
During the EOL Upgrade i ran into boot loading issue:

[B]run-init: /sbin/init: No such file or directory
Target filesystem doesn't have requested /sbin/init.
run-init: /sbin/init: No such file or directory
run-init: /etc/init: Permission denied
run-init: /bin/init: No such file or directory
/bin/sh: 0: Can't open splash
Kernel panic — not syncing: Attempted to kill init! exitcode=0x00007f00
etc. (last two lines mentioned for SEO purposes)[/B]

Using the Ubuntu live, i was able to load the raid drives **mdadm /dev/md0 --assemble /dev/sda2 /dev/sdb2 **and then mount the drives **mount /dev/md0 /mnt **and then **sudo apt-get -o Dir=/mnt update **(this exposed the errors and they were fixed for example appStream). Please i want to know how can install the 'init' to the server again so that it could boot normally. Kindly note that the boot file of the server is mount in **/mnt**

---

### Post by gerald17006 on 2019-08-10
[COLOR=#1A1A1B]After rebooting the server old updates kicked in (It was administered by someone else back then) and now at boot system says:
run-init: /sbin/init: No such file or directory
Target filesystem doesn't have requested /sbin/init
run-init: /sbin/init: No such file or directory
run-init: /etc/init: Permission denied
run-init: /bin/init: No such file or directory
[     "number"] random: nonblocking pool is initialized
/bin/sh: 0: can't access tty; job control turned off


Anyone had faced this problem before? What I didn't try already to boot it, nothing worked for me.

The System is Ubuntu 14.04 server

[/COLOR]

---

### Post by oldfred on 2019-08-10
Moved to Server sub-forum.

But issue really is that 14.04 has reached End of Life - EOL as of April 2019.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You need to make sure your server backup is current & install a new LTS version, probably 18.04 LTS.

---

### Post by LHammonds on 2019-08-11
That seems really messed up.  Did the file system run out of space?  Odd that it says things are missing and permission denied.  If not space-related, I would wonder if it was malicious.

No matter what, your best bet might be to restore from backup.

Telling it to boot using a prior kernel might get you part way there but the missing items and lack of permission makes me think it is not just an update issue.

LHammonds

---

### Post by gerald17006 on 2019-08-11
Der all,
Please find attached view of my boot up screen.

---

### Post by LHammonds on 2019-08-11
@gerald17006, do you have a backup of this server or its data?

---

### Post by gerald17006 on 2019-08-11
LHammonds,
Not i don't!! Why? We can't recover this error?

---

### Post by LHammonds on 2019-08-11
> **gerald17006 said:**
> LHammonds,
Not i don't!! Why? We can't recover this error?
Why?  There are a hundred reasons why you backup your servers/data.  You are experiencing a good reason for one right now.  You need to ask yourself, if the machine gets destroyed (or encrypted by a virus), are you OK losing it?  If not, you NEED to back it up.

"I" cannot recover your system for you.  I can help with issues I have experienced 1st hand or read about but I typically do NOT have boot issues so my experience toolbox is a bit small in that department and will have to defer to others helping you.

I am not saying "you do not have a backup so I am not going help you," I was just confirming what options you have available to you.  You confirmed that restoring from backup is not an option....one that I could have helped you with.

I think there is a bigger issue here than just "fix the boot problem" but fixing the boot problem should be the 1st thing to try and resolve (unless the data is very valuable...if that's the case, I would pull the drive and put it in another system and manually backup the files to avoid potentially messing them up trying to fix the system)

You said it is Ubuntu 14.04 so I would use the latest version on a DVDROM ([14.04.6](http://releases.ubuntu.com/14.04/)).  Once I boot up with the DVD, I would then see if I could repair the boot process.  But I would 1st check to see if /boot ran out of space which means you would have to deal with that before you could do a normal "fix the boot process"

LHammonds

---

### Post by gerald17006 on 2019-08-12
LHammonds,
Well i have an automatic backup system for an application running on this server. So that should be safe. Also, using the ubuntu live CD i can use that to mount the raids in the server and do total back up of those drives and there is enough space on this server too

---

### Post by gerald17006 on 2019-08-13
```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 Data partition (Linux)
/dev/sda2             1,050,624 5,844,017,151 5,842,966,528 RAID partition (Linux)
/dev/sda3         5,844,017,152 5,860,532,223    16,515,072 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sdb2             1,050,624 5,844,017,151 5,842,966,528 RAID partition (Linux)
/dev/sdb3         5,844,017,152 5,860,532,223    16,515,072 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     7,884,799     7,882,752   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6915-E944                              vfat       
/dev/sda2        a8cc761f-39df-0012-4c74-4801697faea9   linux_raid_member sl-mohs-mhero:3
/dev/sda3        73d7025f-25ab-dfd5-e04e-9eb5b71936e5   linux_raid_member SL-MOHS-MHERO:2
/dev/sdb1        F087-4F65                              vfat       
/dev/sdb2        a8cc761f-39df-0012-4c74-4801697faea9   linux_raid_member sl-mohs-mhero:3
/dev/sdb3        5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278   swap       
/dev/sdc1        F870-826A                              vfat       BOOT-REPAIR
/dev/zram0       78c2fbba-1006-46c2-9eca-740febba85c3   swap       
/dev/zram1       fe81f77e-39ff-4593-a16a-0f9b41ff1f32   swap       
/dev/zram2       0063b610-1fdc-466a-a02f-2c6601838300   swap       
/dev/zram3       1cf6970b-f8ef-43a6-8f90-48f629dffd77   swap       
/dev/zram4       9193d281-e1c6-4bdf-a501-344b80583e4f   swap       
/dev/zram5       922ea5e0-31c7-4b19-b65d-b3e4f1756c03   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8 -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-hp_DVD_D_DU8D6SH_427528902734 -> ../../sr0
lrwxrwxrwx 1 root root  9 Aug 13 13:28 usb-General_UDisk-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Aug 13 13:28 usb-General_UDisk-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Aug 13 13:28 wwn-0x5000c5003fdc5cd0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 wwn-0x5000c5004002ae27 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 5932c520-400a-4a57-8680-e9ff0cb9ea3a root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

========================== sdb1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid d5d466a7-8625-4c8a-b73b-6069ff2e16ad root mduuid/a8cc761f39df00124c744801697faea9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


ADDITIONAL INFORMATION :
=================== log of boot-repair 20190813_1327 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4

BLKID BEFORE RAID ACTIVATION:
/dev/sda1: UUID="6915-E944" TYPE="vfat" PARTUUID="8aa4fad2-c3db-4fbf-bbd4-5f22924a3487"
/dev/sdb1: UUID="F087-4F65" TYPE="vfat" PARTUUID="0ec3fa97-00d1-4d6d-8cc3-ed1681895feb"
/dev/sdb2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="6626eb44-ffce-2290-b7b7-2f0433f4bb80" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="fd501a24-c63e-4ed5-b9a2-95a85c315850"
/dev/sdc1: LABEL="BOOT-REPAIR" UUID="F870-826A" TYPE="vfat" PARTUUID="00ee0113-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="e0a667e0-1416-089a-5985-9df1addb9d36" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="59ae35dd-6bf7-4124-845a-d0cb18b10288"
/dev/sda3: UUID="73d7025f-25ab-dfd5-e04e-9eb5b71936e5" UUID_SUB="36a46f37-3f3b-feae-9823-0100fee852c2" LABEL="SL-MOHS-MHERO:2" TYPE="linux_raid_member" PARTLABEL="notswap" PARTUUID="6b9614ee-2152-4101-807d-a2224ef22440"
/dev/sdb3: UUID="5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278" TYPE="swap" PARTLABEL="swap2" PARTUUID="377142b2-c820-421b-86d3-ac1463c63898"
/dev/zram0: UUID="78c2fbba-1006-46c2-9eca-740febba85c3" TYPE="swap"
/dev/zram1: UUID="fe81f77e-39ff-4593-a16a-0f9b41ff1f32" TYPE="swap"
/dev/zram2: UUID="0063b610-1fdc-466a-a02f-2c6601838300" TYPE="swap"
/dev/zram3: UUID="1cf6970b-f8ef-43a6-8f90-48f629dffd77" TYPE="swap"
/dev/zram4: UUID="9193d281-e1c6-4bdf-a501-344b80583e4f" TYPE="swap"
/dev/zram5: UUID="922ea5e0-31c7-4b19-b65d-b3e4f1756c03" TYPE="swap"
dmraid packages needed

** (zenity:3618): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
ping: google.com: Temporary failure in name resolution
Please connect internet. Then close this window.

** (zenity:3626): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
ping: google.com: Temporary failure in name resolution
Could not install dmraid
No internet connection detected. Please connect internet. Then try again.

** (zenity:3636): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y mdadm --no-install-recommends)

** (zenity:3951): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
dmraid packages needed

** (zenity:4249): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
E: The repository 'http://archive.ubuntu.com/ubuntu artful Release' no longer has a Release file.
E: The repository 'http://security.ubuntu.com/ubuntu artful-security Release' does not have a Release file.
E: The repository 'http://archive.ubuntu.com/ubuntu artful-updates Release' does not have a Release file.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
dmraid -si -c: no raid disks
No DMRAID disk.
Warning: no DMRAID nor MD_ARRAY.

** (zenity:4585): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sda1: UUID="6915-E944" TYPE="vfat" PARTUUID="8aa4fad2-c3db-4fbf-bbd4-5f22924a3487"
/dev/sdb1: UUID="F087-4F65" TYPE="vfat" PARTUUID="0ec3fa97-00d1-4d6d-8cc3-ed1681895feb"
/dev/sdb2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="6626eb44-ffce-2290-b7b7-2f0433f4bb80" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="fd501a24-c63e-4ed5-b9a2-95a85c315850"
/dev/sdc1: LABEL="BOOT-REPAIR" UUID="F870-826A" TYPE="vfat" PARTUUID="00ee0113-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="e0a667e0-1416-089a-5985-9df1addb9d36" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="59ae35dd-6bf7-4124-845a-d0cb18b10288"
/dev/sda3: UUID="73d7025f-25ab-dfd5-e04e-9eb5b71936e5" UUID_SUB="36a46f37-3f3b-feae-9823-0100fee852c2" LABEL="SL-MOHS-MHERO:2" TYPE="linux_raid_member" PARTLABEL="notswap" PARTUUID="6b9614ee-2152-4101-807d-a2224ef22440"
/dev/sdb3: UUID="5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278" TYPE="swap" PARTLABEL="swap2" PARTUUID="377142b2-c820-421b-86d3-ac1463c63898"
/dev/zram0: UUID="78c2fbba-1006-46c2-9eca-740febba85c3" TYPE="swap"
/dev/zram1: UUID="fe81f77e-39ff-4593-a16a-0f9b41ff1f32" TYPE="swap"
/dev/zram2: UUID="0063b610-1fdc-466a-a02f-2c6601838300" TYPE="swap"
/dev/zram3: UUID="1cf6970b-f8ef-43a6-8f90-48f629dffd77" TYPE="swap"
/dev/zram4: UUID="9193d281-e1c6-4bdf-a501-344b80583e4f" TYPE="swap"
/dev/zram5: UUID="922ea5e0-31c7-4b19-b65d-b3e4f1756c03" TYPE="swap"

/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 0012,000C,0000,0002,0001,0003,0004,0005,0006,0007,0008,000D,000E,000B,000A,0009
Boot0000  Embedded UEFI Shell    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)
Boot0001  Diagnose Error    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(0849279d-40d5-53ea-e764-2496766f9844)
Boot0002  System Utilities    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(1fd631e5-44e0-2f91-10ab-f88f3568ef30)
Boot0003  Intelligent Provisioning    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(4a433501-ddaa-490b-96b2-04f42d8669b8)
Boot0004  Boot Menu    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(d3fd6286-43c5-bb8d-0793-07b70aa9de36)
Boot0005  Network Boot    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(ee8b26b0-37e9-11e1-b86c-0800200c9a66)
Boot0006  Embedded Diagnostics    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(b57fe6f1-4f49-d46e-4bba-0a8add34d2f3)
Boot0007  View Integrated Management Log    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(93c92423-d1c6-4286-be67-b76b6671047e)
Boot0008* Generic USB Boot    UsbClass(ffff,ffff,255,255)
Boot0009* Front USB 2 : General UDisk     PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(4,0)N.....YM....R,Y.
Boot000A* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv6)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,1)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot000B* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv4)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,1)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)N.....YM....R,Y.
Boot000C* Embedded SATA Port 9 CD/DVD ROM : hp DVD D DU8D6SH     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,0,0)N.....YM....R,Y.
Boot000D* Embedded SATA Port 1 HDD : MB3000GBKAC     PciRoot(0x0)/Pci(0x11,0x4)/Sata(0,0,0)N.....YM....R,Y.
Boot000E* Embedded SATA Port 2 HDD : MB3000GBKAC     PciRoot(0x0)/Pci(0x11,0x4)/Sata(1,0,0)N.....YM....R,Y.
Boot000F  Trigger ready-to-boot event    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(4affaab0-1376-44b4-9c6e-e92388751bc6)
Boot0010* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv4)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)N.....YM....R,Y.
Boot0011* Windows Boot Manager    HD(2,GPT,da56defb-c7a9-4960-a030-354e88278d33,0x96800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...C................
Boot0012* ubuntu    HD(1,GPT,0ec3fa97-00d1-4d6d-8cc3-ed1681895feb,0x800,0x100000)/File(EFIubuntushimx64.efi)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sdb1.

sda    : GPT,    no-BIOS_boot,    has-maybe-EFI,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes
sdb    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:512:gpt:ATA MB3000GBKAC:;
1:1049kB:538MB:537MB:fat32::;
2:538MB:2992GB:2992GB:ext4::raid;
3:2992GB:3001GB:8456MB:linux-swap(v1):notswap:;

BYT;
/dev/sdb:3001GB:scsi:512:512:gpt:ATA MB3000GBKAC:;
1:1049kB:538MB:537MB:fat32::boot, esp;
2:538MB:2992GB:2992GB:ext4::raid;
3:2992GB:3001GB:8456MB:linux-swap(v1):swap2:;

BYT;
/dev/sdc:4037MB:scsi:512:512:msdos:General UDisk:;
1:1049kB:4037MB:4036MB:fat32::boot, lba;

BYT;
/dev/zram5:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram3:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram1:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram4:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram2:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram0:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE              SIZE LABEL
loop0 loop squashfs          629.3M
sda   disk                     2.7T
sda1  part vfat                512M
sda2  part linux_raid_member   2.7T sl-mohs-mhero:3
sda3  part linux_raid_member   7.9G SL-MOHS-MHERO:2
sdb   disk                     2.7T
sdb1  part vfat                512M
sdb2  part linux_raid_member   2.7T sl-mohs-mhero:3
sdb3  part swap                7.9G
sdc   disk                     3.8G
sdc1  part vfat                3.8G BOOT-REPAIR
sr0   rom                     1024M
zram0 disk                   654.3M
zram1 disk                   654.3M
zram2 disk                   654.3M
zram3 disk                   654.3M
zram4 disk                   654.3M
zram5 disk                   654.3M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda3     1  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb2     1  0  0
sdb3     1  0  0         [SWAP]
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sr0      1  0  1 running
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]
zram2    0  0  0         [SWAP]
zram3    0  0  0         [SWAP]
zram4    0  0  0         [SWAP]
zram5    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3993004k,nr_inodes=998251,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804040k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14032)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=804036k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hpilo hugepages hwrng i2c-0 i2c-1 i2c-2 initctl input ipmi0 kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 ptp1 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb3 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 44 e9 15 69 4e  4f 20 4e 41 4d 45 20 20  |..)D..iNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 65 4f 87 f0 4e  4f 20 4e 41 4d 45 20 20  |..)eO..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     786M  9.4M  776M   2% /run
/dev/sdc1      vfat      3.8G  708M  3.1G  19% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   3.9G   79M  3.8G   3% /
tmpfs          tmpfs     3.9G     0  3.9G   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  4.0K  3.9G   1% /tmp
tmpfs          tmpfs     786M  4.0K  786M   1% /run/user/999
/dev/sda1      vfat      511M  3.4M  508M   1% /mnt/boot-sav/sda1
/dev/sdb1      vfat      511M  3.2M  508M   1% /mnt/boot-sav/sdb1

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8FAA242E-12EC-4B33-9A0C-FE198415F01E

Device          Start        End    Sectors  Size Type
/dev/sda1        2048    1050623    1048576  512M Linux filesystem
/dev/sda2     1050624 5844017151 5842966528  2.7T Linux RAID
/dev/sda3  5844017152 5860532223   16515072  7.9G Linux swap


Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C2DCBE76-39D5-4E20-B958-7DB17A0B56B9

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048    1050623    1048576  512M EFI System
/dev/sdb2     1050624 5844017151 5842966528  2.7T Linux RAID
/dev/sdb3  5844017152 5860532223   16515072  7.9G Linux swap




Disk /dev/sdc: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00ee0113

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7884799 7882752  3.8G  c W95 FAT32 (LBA)


Disk /dev/zram0: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram4: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram5: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


No OS or WinEFI system

** (zenity:8260): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
No OS or WinEFI system


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by gerald17006 on 2019-08-13
LHammonds,

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 Data partition (Linux)
/dev/sda2             1,050,624 5,844,017,151 5,842,966,528 RAID partition (Linux)
/dev/sda3         5,844,017,152 5,860,532,223    16,515,072 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sdb2             1,050,624 5,844,017,151 5,842,966,528 RAID partition (Linux)
/dev/sdb3         5,844,017,152 5,860,532,223    16,515,072 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048     7,884,799     7,882,752   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6915-E944                              vfat       
/dev/sda2        a8cc761f-39df-0012-4c74-4801697faea9   linux_raid_member sl-mohs-mhero:3
/dev/sda3        73d7025f-25ab-dfd5-e04e-9eb5b71936e5   linux_raid_member SL-MOHS-MHERO:2
/dev/sdb1        F087-4F65                              vfat       
/dev/sdb2        a8cc761f-39df-0012-4c74-4801697faea9   linux_raid_member sl-mohs-mhero:3
/dev/sdb3        5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278   swap       
/dev/sdc1        F870-826A                              vfat       BOOT-REPAIR
/dev/zram0       78c2fbba-1006-46c2-9eca-740febba85c3   swap       
/dev/zram1       fe81f77e-39ff-4593-a16a-0f9b41ff1f32   swap       
/dev/zram2       0063b610-1fdc-466a-a02f-2c6601838300   swap       
/dev/zram3       1cf6970b-f8ef-43a6-8f90-48f629dffd77   swap       
/dev/zram4       9193d281-e1c6-4bdf-a501-344b80583e4f   swap       
/dev/zram5       922ea5e0-31c7-4b19-b65d-b3e4f1756c03   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8 -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291VAT8-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 ata-MB3000GBKAC_Z291ZGYS-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 ata-hp_DVD_D_DU8D6SH_427528902734 -> ../../sr0
lrwxrwxrwx 1 root root  9 Aug 13 13:28 usb-General_UDisk-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Aug 13 13:28 usb-General_UDisk-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Aug 13 13:28 wwn-0x5000c5003fdc5cd0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5003fdc5cd0-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Aug 13 13:28 wwn-0x5000c5004002ae27 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 13 13:28 wwn-0x5000c5004002ae27-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 5932c520-400a-4a57-8680-e9ff0cb9ea3a root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

========================== sdb1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid d5d466a7-8625-4c8a-b73b-6069ff2e16ad root mduuid/a8cc761f39df00124c744801697faea9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


ADDITIONAL INFORMATION :
=================== log of boot-repair 20190813_1327 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4

BLKID BEFORE RAID ACTIVATION:
/dev/sda1: UUID="6915-E944" TYPE="vfat" PARTUUID="8aa4fad2-c3db-4fbf-bbd4-5f22924a3487"
/dev/sdb1: UUID="F087-4F65" TYPE="vfat" PARTUUID="0ec3fa97-00d1-4d6d-8cc3-ed1681895feb"
/dev/sdb2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="6626eb44-ffce-2290-b7b7-2f0433f4bb80" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="fd501a24-c63e-4ed5-b9a2-95a85c315850"
/dev/sdc1: LABEL="BOOT-REPAIR" UUID="F870-826A" TYPE="vfat" PARTUUID="00ee0113-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="e0a667e0-1416-089a-5985-9df1addb9d36" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="59ae35dd-6bf7-4124-845a-d0cb18b10288"
/dev/sda3: UUID="73d7025f-25ab-dfd5-e04e-9eb5b71936e5" UUID_SUB="36a46f37-3f3b-feae-9823-0100fee852c2" LABEL="SL-MOHS-MHERO:2" TYPE="linux_raid_member" PARTLABEL="notswap" PARTUUID="6b9614ee-2152-4101-807d-a2224ef22440"
/dev/sdb3: UUID="5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278" TYPE="swap" PARTLABEL="swap2" PARTUUID="377142b2-c820-421b-86d3-ac1463c63898"
/dev/zram0: UUID="78c2fbba-1006-46c2-9eca-740febba85c3" TYPE="swap"
/dev/zram1: UUID="fe81f77e-39ff-4593-a16a-0f9b41ff1f32" TYPE="swap"
/dev/zram2: UUID="0063b610-1fdc-466a-a02f-2c6601838300" TYPE="swap"
/dev/zram3: UUID="1cf6970b-f8ef-43a6-8f90-48f629dffd77" TYPE="swap"
/dev/zram4: UUID="9193d281-e1c6-4bdf-a501-344b80583e4f" TYPE="swap"
/dev/zram5: UUID="922ea5e0-31c7-4b19-b65d-b3e4f1756c03" TYPE="swap"
dmraid packages needed

** (zenity:3618): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
ping: google.com: Temporary failure in name resolution
Please connect internet. Then close this window.

** (zenity:3626): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
ping: google.com: Temporary failure in name resolution
Could not install dmraid
No internet connection detected. Please connect internet. Then try again.

** (zenity:3636): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y mdadm --no-install-recommends)

** (zenity:3951): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
dmraid packages needed

** (zenity:4249): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
E: The repository 'http://archive.ubuntu.com/ubuntu artful Release' no longer has a Release file.
E: The repository 'http://security.ubuntu.com/ubuntu artful-security Release' does not have a Release file.
E: The repository 'http://archive.ubuntu.com/ubuntu artful-updates Release' does not have a Release file.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
dmraid -si -c: no raid disks
No DMRAID disk.
Warning: no DMRAID nor MD_ARRAY.

** (zenity:4585): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sda1: UUID="6915-E944" TYPE="vfat" PARTUUID="8aa4fad2-c3db-4fbf-bbd4-5f22924a3487"
/dev/sdb1: UUID="F087-4F65" TYPE="vfat" PARTUUID="0ec3fa97-00d1-4d6d-8cc3-ed1681895feb"
/dev/sdb2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="6626eb44-ffce-2290-b7b7-2f0433f4bb80" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="fd501a24-c63e-4ed5-b9a2-95a85c315850"
/dev/sdc1: LABEL="BOOT-REPAIR" UUID="F870-826A" TYPE="vfat" PARTUUID="00ee0113-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="a8cc761f-39df-0012-4c74-4801697faea9" UUID_SUB="e0a667e0-1416-089a-5985-9df1addb9d36" LABEL="sl-mohs-mhero:3" TYPE="linux_raid_member" PARTUUID="59ae35dd-6bf7-4124-845a-d0cb18b10288"
/dev/sda3: UUID="73d7025f-25ab-dfd5-e04e-9eb5b71936e5" UUID_SUB="36a46f37-3f3b-feae-9823-0100fee852c2" LABEL="SL-MOHS-MHERO:2" TYPE="linux_raid_member" PARTLABEL="notswap" PARTUUID="6b9614ee-2152-4101-807d-a2224ef22440"
/dev/sdb3: UUID="5ddb9fe0-15b3-456f-9d9a-4fc2a39e7278" TYPE="swap" PARTLABEL="swap2" PARTUUID="377142b2-c820-421b-86d3-ac1463c63898"
/dev/zram0: UUID="78c2fbba-1006-46c2-9eca-740febba85c3" TYPE="swap"
/dev/zram1: UUID="fe81f77e-39ff-4593-a16a-0f9b41ff1f32" TYPE="swap"
/dev/zram2: UUID="0063b610-1fdc-466a-a02f-2c6601838300" TYPE="swap"
/dev/zram3: UUID="1cf6970b-f8ef-43a6-8f90-48f629dffd77" TYPE="swap"
/dev/zram4: UUID="9193d281-e1c6-4bdf-a501-344b80583e4f" TYPE="swap"
/dev/zram5: UUID="922ea5e0-31c7-4b19-b65d-b3e4f1756c03" TYPE="swap"

/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 0012,000C,0000,0002,0001,0003,0004,0005,0006,0007,0008,000D,000E,000B,000A,0009
Boot0000  Embedded UEFI Shell    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)
Boot0001  Diagnose Error    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(0849279d-40d5-53ea-e764-2496766f9844)
Boot0002  System Utilities    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(1fd631e5-44e0-2f91-10ab-f88f3568ef30)
Boot0003  Intelligent Provisioning    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(4a433501-ddaa-490b-96b2-04f42d8669b8)
Boot0004  Boot Menu    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(d3fd6286-43c5-bb8d-0793-07b70aa9de36)
Boot0005  Network Boot    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(ee8b26b0-37e9-11e1-b86c-0800200c9a66)
Boot0006  Embedded Diagnostics    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(b57fe6f1-4f49-d46e-4bba-0a8add34d2f3)
Boot0007  View Integrated Management Log    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(93c92423-d1c6-4286-be67-b76b6671047e)
Boot0008* Generic USB Boot    UsbClass(ffff,ffff,255,255)
Boot0009* Front USB 2 : General UDisk     PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(4,0)N.....YM....R,Y.
Boot000A* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv6)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,1)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot000B* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv4)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,1)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)N.....YM....R,Y.
Boot000C* Embedded SATA Port 9 CD/DVD ROM : hp DVD D DU8D6SH     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,0,0)N.....YM....R,Y.
Boot000D* Embedded SATA Port 1 HDD : MB3000GBKAC     PciRoot(0x0)/Pci(0x11,0x4)/Sata(0,0,0)N.....YM....R,Y.
Boot000E* Embedded SATA Port 2 HDD : MB3000GBKAC     PciRoot(0x0)/Pci(0x11,0x4)/Sata(1,0,0)N.....YM....R,Y.
Boot000F  Trigger ready-to-boot event    FvVol(cdbb7b35-6833-4ed6-9ab2-57d2acddf6f0)/FvFile(4affaab0-1376-44b4-9c6e-e92388751bc6)
Boot0010* Embedded LOM 1 Port 1 : HP Ethernet 1Gb 2-port 361i Adapter - NIC (PXE IPv4)     PciRoot(0x0)/Pci(0x2,0x3)/Pci(0x0,0x0)/MAC(5820b1032cf2,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)N.....YM....R,Y.
Boot0011* Windows Boot Manager    HD(2,GPT,da56defb-c7a9-4960-a030-354e88278d33,0x96800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...C................
Boot0012* ubuntu    HD(1,GPT,0ec3fa97-00d1-4d6d-8cc3-ed1681895feb,0x800,0x100000)/File(EFIubuntushimx64.efi)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sdb1.

sda    : GPT,    no-BIOS_boot,    has-maybe-EFI,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes
sdb    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:512:gpt:ATA MB3000GBKAC:;
1:1049kB:538MB:537MB:fat32::;
2:538MB:2992GB:2992GB:ext4::raid;
3:2992GB:3001GB:8456MB:linux-swap(v1):notswap:;

BYT;
/dev/sdb:3001GB:scsi:512:512:gpt:ATA MB3000GBKAC:;
1:1049kB:538MB:537MB:fat32::boot, esp;
2:538MB:2992GB:2992GB:ext4::raid;
3:2992GB:3001GB:8456MB:linux-swap(v1):swap2:;

BYT;
/dev/sdc:4037MB:scsi:512:512:msdos:General UDisk:;
1:1049kB:4037MB:4036MB:fat32::boot, lba;

BYT;
/dev/zram5:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram3:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram1:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram4:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram2:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

BYT;
/dev/zram0:686MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:686MB:686MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE              SIZE LABEL
loop0 loop squashfs          629.3M
sda   disk                     2.7T
sda1  part vfat                512M
sda2  part linux_raid_member   2.7T sl-mohs-mhero:3
sda3  part linux_raid_member   7.9G SL-MOHS-MHERO:2
sdb   disk                     2.7T
sdb1  part vfat                512M
sdb2  part linux_raid_member   2.7T sl-mohs-mhero:3
sdb3  part swap                7.9G
sdc   disk                     3.8G
sdc1  part vfat                3.8G BOOT-REPAIR
sr0   rom                     1024M
zram0 disk                   654.3M
zram1 disk                   654.3M
zram2 disk                   654.3M
zram3 disk                   654.3M
zram4 disk                   654.3M
zram5 disk                   654.3M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda3     1  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb2     1  0  0
sdb3     1  0  0         [SWAP]
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sr0      1  0  1 running
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]
zram2    0  0  0         [SWAP]
zram3    0  0  0         [SWAP]
zram4    0  0  0         [SWAP]
zram5    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3993004k,nr_inodes=998251,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804040k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14032)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=804036k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hpilo hugepages hwrng i2c-0 i2c-1 i2c-2 initctl input ipmi0 kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 ptp1 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb3 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 44 e9 15 69 4e  4f 20 4e 41 4d 45 20 20  |..)D..iNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 65 4f 87 f0 4e  4f 20 4e 41 4d 45 20 20  |..)eO..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     786M  9.4M  776M   2% /run
/dev/sdc1      vfat      3.8G  708M  3.1G  19% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   3.9G   79M  3.8G   3% /
tmpfs          tmpfs     3.9G     0  3.9G   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  4.0K  3.9G   1% /tmp
tmpfs          tmpfs     786M  4.0K  786M   1% /run/user/999
/dev/sda1      vfat      511M  3.4M  508M   1% /mnt/boot-sav/sda1
/dev/sdb1      vfat      511M  3.2M  508M   1% /mnt/boot-sav/sdb1

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8FAA242E-12EC-4B33-9A0C-FE198415F01E

Device          Start        End    Sectors  Size Type
/dev/sda1        2048    1050623    1048576  512M Linux filesystem
/dev/sda2     1050624 5844017151 5842966528  2.7T Linux RAID
/dev/sda3  5844017152 5860532223   16515072  7.9G Linux swap


Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C2DCBE76-39D5-4E20-B958-7DB17A0B56B9

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048    1050623    1048576  512M EFI System
/dev/sdb2     1050624 5844017151 5842966528  2.7T Linux RAID
/dev/sdb3  5844017152 5860532223   16515072  7.9G Linux swap




Disk /dev/sdc: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00ee0113

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7884799 7882752  3.8G  c W95 FAT32 (LBA)


Disk /dev/zram0: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram4: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram5: 654.3 MiB, 686112768 bytes, 167508 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


No OS or WinEFI system

** (zenity:8260): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
No OS or WinEFI system


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2019-08-13
Duplicate threads merged.

And with Boot-Repair only post link to summary report, not all the details.

---

