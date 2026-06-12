---
title: "UEFI Installing - Tips"
date: 2013-05-21
forum: Tutorials
---

### Post by oldfred on 2013-05-21
[B]General UEFI install Info (not for Macs)
Newest Install Info:
[/B][https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
Support now on Discourse. If first time, you need to review Welcome first. 
Support in Categories, Support & Help and then in tags for specific topics.
[https://discourse.ubuntu.com/t/welcome-to-support-and-help/49951](https://discourse.ubuntu.com/t/welcome-to-support-and-help/49951)
For help post on Discourse

[COLOR=#ff0000][SIZE=4]Caution:
[/SIZE][/COLOR]**Do not turn legacy on**. Most work better if UEFI only setting used. Lenovo annouced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[URL="https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products"]https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products
[/URL]Note: Samsung may brick in UEFI mode. Better to use BIOS. [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557) (old but still valid)
Ubuntu 24.04.1 LTS is now available. Desktop & other versions & flavors here:
[https://ubuntu.com/download](https://ubuntu.com/download)
Note that 24.04 22.04, & 20.04 LTS are long term support versions. Flavors like Kubuntu only have 3 years of normal support.  See below on enablement stack versions.
Very new hardware may need the newest version to have updated kernel & drivers. And that may include the 9 month support versions released between the LTS versions.

Systems need UEFI updates for        or Meltdown/Spectre mitigation, both Windows & Linux kernel updated, but new variants regularly found, so regular updates needed. One exception: Do not update UEFI for x299 if Kaby-X Also June 2021 many Dell models need UEFI update. See below for more info.
If SSD, you may also need firmware updates

If re-installing Ubuntu  only use Something Else (links to examples below).
Do not use LVM nor full drive encryption if new user. It will erase your Windows and requires advanced knowledge. But many advanced users especially with servers use LVM.
Many brands/models have unique settings, see below.

[I]Backups are very important, see backup section below.
[/I]
UEFI is now a bit more complex than the old BIOS install as it includes both UEFI and BIOS as options. You must choose in UEFI and choose how you boot installs. Various settings in UEFI/BIOS may be required to enable correct boot mode. You do always want to boot in UEFI mode, but may not need nor want secure boot mode of UEFI.
Install instructions for dual booting in UEFI apply with any current version of Windows in UEFI mode & Ubuntu in UEFI mode. Very minor differences with newer Windows (same settings required) and Ubuntu versions.

[B]Major Sections below:
[/B]Summary UEFI install instructions
Ubuntu UEFI install ISO Download link
    Windows 10 or 8 pre-installed with UEFI & secure boot, Windows 10 upgrade from Windows 7 probably BIOS with MBR partitions. No UEFI system, but if newer hardware it may be UEFI. 
    Systems that only boot Windows from UEFI.
Boot-Repair Should only be required if issues, will not fix Windows. Great for Summary Report.
    Partitioning - gpt required for UEFI
    Boot but black screen/Video issues with nVidia or AMD, nomodeset

    [B]Additional Info
[/B]gpt partitioning
Two drive installs - both must be gpt partitioned
    Backup - Windows & efi partition
UltraBooks with Intel SRT(Seen as RAID) and dual video
efi Menu cleanup
Windows 8/10 repair links
    rEFInd Boot Manager may solve some issues
    Un-installing
Examples by brand - Some users have posted details of how they did it.
    Links to additional info & what UEFI is
Acronyms

Some good detail on UEFI & Windows settings needed - by tea for one
[https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324](https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324)

** Summary UEFI install instructions:**
1. Back up Windows, your data, and make a Windows repair/recovery flash drive.
2. Download and create Ubuntu 64 bit  installer, USB flash drive (new versions may not work with DVD).
3. Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
4. Turn off Windows fast startup & bitlocker in Windows.
5. In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot (may be called "other" vs. "Windows"), only some may need CSM mode on (older Dell), but still select UEFI. Usually best to have UEFI only as boot mode.
6. Some UEFI may need you to turn on or allow USB boot, especially if Secure boot is on.
7. Boot Ubuntu live installer in UEFI live mode, and verify your system works ok. How you boot installer UEFI or BIOS is how it installs. 
8. Install Ubuntu. links to screen shots below Only / (root) as ext4 & ESP required. But may want others. Only one ESP per drive and installer will auto find it, if existing.
new versions will install proprietary nVidia driver if Safe Boot option & choose to install third-party software options are checked. If UEFI Secure Boot on, user must provide UEFI secure boot key. 
    If nVidia or AMD video may need nomodeset boot parameter. Some brands also may need other boot parameters. 
Create backup procedure for your Ubuntu data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

**Ubuntu UEFI install ISO**
 Also link on install guide, from Windows or Ubuntu
        [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) 
Easy way to create UEFI only bootable flash drive, did not work on some older versions.
[https://ubuntuforums.org/showthread.php?t=2299040]("http://ubuntuforums.org/showthread.php?t=2299040")

**Windows 8 or 10, 11 pre-installed & secure boot**
Since vendors also have bugs in UEFI, they are also updating regularly. Best to update to latest UEFI/BIOS version. You may have to make UEFI/BIOS settings changes also. New SSD also may need firmware updates.
    You will need to use the 64 bit version of newest 22.04.x (best for very new hardware) and from the UEFI menu, boot the flash drive in UEFI mode. That way it will install in UEFI mode. Very new hardware needs latest version of Ubuntu and still may need ppa to update to even newer software/drivers not yet in distribution.
    
Systems need Windows fast start up (hibernation) and UEFI/BIOS fast boot or quick boot UEFI settings turned off. Vital for some systems. UEFI fast boot may prevent or make it difficult to get into UEFI menu. Some systems need password set to allow settings changes (Acer for one).
 [https://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html")
[https://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")
    
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot into Windows after shrink so it can run its repairs to its new size. Make sure Windows fast startup & bitlocker are off.
    Backup efi partition and Windows partition before Install of Ubuntu.
    
    Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen - Good first link to follow for UEFI install details:
    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
How To Install Ubuntu Linux Alongside Windows 8 or 10 (UEFI)
 [https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi) 
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/]("http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html")
        
Linux on UEFI:  Installation Guides with screen shots
[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)
    [URL="http://www.rodsbooks.com/linux-uefi/"]https://www.rodsbooks.com/linux-uefi/
[/URL][URL="https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview"]https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview
https://ubuntuhandbook.org/index.php/how-to-install-ubuntu/[/URL]
    Something Else or manual Install, essentially same for Windows 10 & Ubuntu 16.04.
    [https://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html]("http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html")
    More info on Windows:
 [https://www.tenforums.com/]("http://www.tenforums.com/") 
[https://www.eightforums.com/]("http://www.eightforums.com/")

It is possible to install Ubuntu on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). But best to use newest version to have latest software updates as UEFI fixes for newest hardware is more up to date in newer versions.
    24.04, 22.04 & 20.04 LTS Release Notes:
[https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890)
[https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668)
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)
 
Enablement stack update schedules, newer kernels in LTS versions for newer systems
 [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) 

    UEFI systems now have multiple ways to boot - UEFI w/Secure boot, UEFI (secure boot off) and BIOS/CSM. Some UEFI clearly have all 3 settings, others may default. Some are not clear that a Windows boot setting in UEFI means secure boot and you need to select "Other" for UEFI only or CSM- UEFI Compatibility Support Module (CSM), which emulates a BIOS mode. Also the mode you select to boot USB installer may not be the default you have set in UEFI/BIOS. Make sure all boot settings are UEFI.

**gpt(GUID)) partitioning**
        Required for UEFI, and for drives over 2TB.
    You can also use gparted but must change default partitioning first.
    Select gpt under device(menu at top), advanced over msdos(MBR) default partitioning before starting. Note: erases entire drive.
    Or use gdisk which is in repository, now standard in newer installs:
    GPT fdisk Tutorial -srs5694 in forums
    [https://ubuntuforums.org/showthread.php?t=1439794]("http://ubuntuforums.org/showthread.php?t=1439794")
    [https://www.rodsbooks.com/gdisk/]("http://www.rodsbooks.com/gdisk/")
            sudo apt-get install gdisk
    GPT Advantages (older but still valid) srs5694 post #2:
    [https://ubuntuforums.org/showthread.php?t=1457901]("http://ubuntuforums.org/showthread.php?t=1457901")
    [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
    [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

**Two Drive UEFI installs**, Internal, external or flash drive
    You must gpt partition in advance including ESP - efi system partition on second drive, then use Something Else to install.
[https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives](https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives)
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

Grub  default installs to first  drive's ESP, you can either copy files  from first drive to second drive's ESP, update entry in EFI and edit  fstab. Or change default entry while installing. Still have to edit  fstab after install so updates are to correct ESP.
Only applies to Ubiquity installer, new versions use Subituity installer. Lubuntu & 24.04 Kubuntu use Calamares installer.
       [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) See #23 & #26 

    
 Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[https://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147](https://askubuntu.com/questions/720827/using-ubiquity-for-the-full-disk-encrypted-install-to-disk-on-dev-sdb-instead-o/722147#722147)
[https://ubuntuforums.org/showthread.php?t=2305876]("http://ubuntuforums.org/showthread.php?t=2305876")
[https://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot]("http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot")
[https://ubuntuforums.org/showthread.php?t=2192378]("http://ubuntuforums.org/showthread.php?t=2192378")
  [https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
UEFI dual boot two drives - HP
    [https://ubuntuforums.org/showthread.php?t=2072950]("http://ubuntuforums.org/showthread.php?t=2072950")
    UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
    [https://ubuntuforums.org/showthread.php?t=2031836]("http://ubuntuforums.org/showthread.php?t=2031836")


**Two Drive installs or external drive** - See also examples below
You must partition in advance with ESP on second drive and then see this work around in post 23. Still may need to update fstab with correct UUID.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Often easier to unplug or in UEFI turn off Windows drive. Then do a standard UEFI install to Ubuntu drive.
Or remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

    Both drives must be gpt partitioned. Best to include ESP - efi system partition as first partition on every gpt drive, even if booting from Windows efi partition. And Ubuntu's grub only installs to ESP on first drive usually sda or nvme0n1.
    Once you are booting with UEFI, best to have all drives and larger external devices even larger flash as gpt partitioned with an efi partition first even if just for future use. May have to manually edit UUID of efi partition, but Boot-Repair updated for two drive installs.

And Ubuntu's UEFI  grub only installs to the ESP on sda, or not the external drive and not  to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I  manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then  copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I  then updated fstab to have correct UUID for ESP on external drive.

The version of grub in a full install is hard coded to find the rest of  grub in /EFI/ubuntu so both copies are required. There are ways to directly  install grub as bootx64.efi, but then you have to manually maintain  grub.cfg.
 Good advice on UEFI and two drive installs
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration) 
[https://askubuntu.com/questions/1130372/dual-booting-win-10-and-ubuntu-18-04-on-two-separate-physical-ssds](https://askubuntu.com/questions/1130372/dual-booting-win-10-and-ubuntu-18-04-on-two-separate-physical-ssds)

Details on full UEFI install to flash drive or any external drive.
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836)

[B]Partitioning
[/B]New user with only 50GB for Linux only needs / (root) as ext4. And ESP if UEFI. 
If more space then smaller / of 30 to 50GB & rest as /home. Or more advanced use data partition(s) for your data.
Ubuntu now uses a lot of snaps that take more space in /. 

    With UEFI, gpt partitioning is (almost) required. If multiple drives all bootable drives need to be gpt and best if data drives are also gpt in case later you want to make it bootable. With gpt there is no primary, extended, logical partitions as in MBR(msdos) nor the 4 primary partition limit.
    
You can only have one ESP/efi partition per drive (Ubuntu will share Windows ESP if dual booting on same drive) and with gparted you use the boot flag to assign it as the efi partition. No other partitions can have boot flag. Only if booting in BIOS mode with Ubuntu on gpt partitioned drive, you need a bios_grub partition.
    Windows will only boot in UEFI mode so you cannot install Windows to gpt drive unless booting with UEFI.
    I suggest 300-500MB efi partition - FAT32, 25 to30GB /(root) - ext4, and then either /home - ext4, or /mnt/data partition(s). But you cannot do data partitions as part of install. 
    If dual booting with Windows a shared NTFS data partition is also recommended.
    [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL] [https://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu]("http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu") 

**UEFI update **
[https://fwupd.org/](https://fwupd.org/)
UEFI/BIOS updates brand & model list, note  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
Dell required update  June 2021
[https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home)

**Backup** - Windows, data & efi partitions
    Backup windows before install - post by Mark Phelps
        [https://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710]("http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710")
        [https://www.macrium.com/reflectfree.asp]("http://www.macrium.com/reflectfree.asp")
    Another suggestion by srs5694
        [https://www.runtime.org/driveimage-xml.htm]("http://www.runtime.org/driveimage-xml.htm")
    Microsoft Windows 7,8 & 10 reinstall/refresh
        [https://support.microsoft.com/en-us/help/15088/windows-create-installation-media](https://support.microsoft.com/en-us/help/15088/windows-create-installation-media)
Ubuntu backup
       [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 
    [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)


Black Screen/ Video Modes
    This usually required with AMD or nVidia. Newest versions now work better. And will let you install nVidia driver as part of install.
    How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different
 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

[https://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")
    Newer systems may have this setting:
    Also turn off one Video mode or Intel settings in UEFI/BIOS like Intel NIC if USB flash not working.
    Some Laptops need this in place of quiet splash:
    acpi_osi=Linux acpi_backlight=vendor
    Some laptops just have backlight set way down, press f key to make it brighter

    Some new Intel may need above or this (usually not required with 16.04 or later):
        i915.i915_enable_rc6=1
    Or Force Intel Video mode as boot parameter in grub menu - change to your screen size
        video=1280x1024-24@60

Ubuntu has option to install proprietary drivers as part of install. If UEFI Secure Boot on, you then have to provide your own Secure Boot signing key for those drivers. Best to install nVidia drivers as part of install, but can be installed after either by command line or in system settings.

**UltraBooks** - Also see examples below Also see updated comment in post #5 below. Grub may correctly install now with 14.04 or later without much effort.

    Ubuntu now installs with Intel RST on, but when grub sees the RAID grub will not install. So you have to turn the SRT off or set UEFI/BIOS to AHCI and remove the RAID meta data from the drives. Some install Ubuntu to SSD, others install to hard drive and turn SRT back on and have had it work.
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 

    Some discussion of limits of new nVidia driver with some Optimus support
    [https://ubuntuforums.org/showthread.php?t=2142215]("http://ubuntuforums.org/showthread.php?t=2142215")
    Intel Smart Response Technology
    [https://www.intel.com/p/en_US/support...ts/chpsts/imsm]("http://www.intel.com/p/en_US/support...ts/chpsts/imsm")
    Some general info in post #3
    [https://ubuntuforums.org/showthread.php?t=2071242]("http://ubuntuforums.org/showthread.php?t=2071242")
    Uses larger SSD for both Intel SRT & Ubuntu
    [https://ubuntuforums.org/showthread.php?t=2129157&page=2]("http://ubuntuforums.org/showthread.php?t=2129157&page=2")
    Ubuntu on hard drive, re-enable SRT post #19 details
    [https://ubuntuforums.org/showthread.php?t=2129157]("http://ubuntuforums.org/showthread.php?t=2129157")
    If issues with RAID, disable the RAID (Change to AHCI unless RAID 0), it was using the Intel rapid management in UEFI and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
        sudo dmraid -E -r /dev/sda
        sudo dmraid -E -r /dev/sdb

Grub menu (# is comment)

    # You can add this line to grub configuration or turn off the execute bit on 30_os-prober
        gksudo gedit /etc/default/grub
            GRUB_DISABLE_OS_PROBER=true
    #or turn off executable bit
        sudo chmod a-x /etc/grub.d/30_os-prober
    # Then do:
        sudo update-grub
    
    # Edit descriptions used by Boot-Repair or remove entire boot stanza
        sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
        gksudo gedit /etc/grub.d/25_custom
    #Then do:
        sudo update-grub

**UEFI menu clean up, delete old entries** (UEFI saves entries in its NVRAM)
You first need to remove /EFI/ubuntu folder from efi(ESP) partition or else UEFI may add it back again. Best to fully backup efi partition before making any changes.
    If you cannot do change from UEFI menu, you can from command line with efibootmgr.
        
# from live USB flash booted in UEFI mode and use efibootmgr
sudo apt-get install efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're  deleting the right one, and then you use the combination of "-b ####"  (to specify the entry) and "-B" (to delete it). Examples #5 is delete:,  with Ubuntu you need sudo, others must be at root.
 efibootmgr -b XXXX -B 

Examples:
    [https://linux.die.net/man/8/efibootmgr]("http://linux.die.net/man/8/efibootmgr")
Really UEFI boot menu edits 
    [https://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu]("http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu")

    Remove Duplicate Firmware Objects in Windows BCD and NVRAM
    [https://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx")
 

**Boot Repair** -Also handles LVM, GPT, separate /boot and  UEFI dual boot, but not most Windows 80 or 10 issues (use your Windows  repair/recovery disk):
    [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    If issues, run Boot-Repair's summary report and post a new thread in Ubuntu forums.
    [https://ubuntuforums.org/newthread.php?do=newthread&f=326]("http://ubuntuforums.org/newthread.php?do=newthread&f=326")
    
     Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc, and installing grub-efi-amd64, if gpt partitioned.
     It can update system to secure boot if you boot in secure boot mode. But then the grub entry for Windows may not work.

    If unsure of which file is orginal Windows boot file - Windows UEFI install should  have backup of bootmgfw.efi here:
    C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

How to Create a Bootable UEFI USB Flash Drive for Installing Windows 10, Windows 8, or Windows 8.1
 [https://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html]("http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html") 

[https://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html]("http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html")

[B]Windows 8/10 UEFI Repairs
[/B] How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[https://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5]("http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5")
 Windows 10 repair disk
[https://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html]("http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html") 

[https://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader]("http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader")
    [URL="http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html"]https://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html
[/URL]Create Windows 8 Repair flash drive, must be FAT32 to boot in UEFI mode:
    [https://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html]("http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html")
    [https://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/]("http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/")

**rEFInd - Boot Manager**
    rEFInd is a boot manager with graphical boot choices. UEFI and grub are also boot managers, but UEFI is limited and grub only has menu. You will still need grub2 as it is Ubuntu's boot loader but may want rEFInd. rEFInd also solves some issues with UEFI that will not correctly dual boot.
    [https://www.rodsbooks.com/refind/]("http://www.rodsbooks.com/refind/")
    [https://wiki.archlinux.org/index.php/Boot_loaders#Using_rEFInd](https://wiki.archlinux.org/index.php/Boot_loaders#Using_rEFInd)
    [https://www.rodsbooks.com/refind/secureboot.html]("http://www.rodsbooks.com/refind/secureboot.html")
    Now has a ppa to make it easy to install:
    [https://www.rodsbooks.com/refind/getting.html]("http://www.rodsbooks.com/refind/getting.html")

**Examples** - some older, newer versions of Ubuntu should be easier as major updates to kernel, support software, video & UEFI drivers.
Dell often requires changing RAID to AHCI, may need UEFI update from Dell and SSD firmware update.
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN) 
Dell XPS 13 9360 
 [https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
 
        Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[https://ubuntuforums.org/showthread.php?t=2317643]("http://ubuntuforums.org/showthread.php?t=2317643") 
    
    Screenshots of secure boot settings Asrock, Asus, HP, Acer
    [https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

    Haswell Laptop - Toshiba P50
    [https://ubuntuforums.org/showthread.php?t=2163854]("http://ubuntuforums.org/showthread.php?t=2163854")
    acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win
    [https://ubuntuforums.org/showthread.php?t=2240043]("http://ubuntuforums.org/showthread.php?t=2240043")

All Acer require supervisor password  & enable "trust" on Ubuntu/grub efi files. Acer Trust Settings - details:
 [https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)

 [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
 [https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 

Many Asus seem to need pci=nomsi boot parameter
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[https://ubuntuforums.org/showthread.php?t=2303665]("http://ubuntuforums.org/showthread.php?t=2303665")
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3) 
    ASUS Zenbook Prime UX32VD
    [https://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1]("http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1")
    [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

    HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
        [URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]https://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079
[/URL] HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

        [https://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453]("http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453")
[https://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook]("http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook") 
    [https://ubuntuforums.org/showthread.php?t=2185869]("http://ubuntuforums.org/showthread.php?t=2185869")
    Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
        [https://ubuntuforums.org/showthread.php?t=2144853]("http://ubuntuforums.org/showthread.php?t=2144853")
   
   Lenovo T540 works but UEFI settings critical or it may brick
        [https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
        Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
        [https://ubuntuforums.org/showthread.php?t=2255746]("http://ubuntuforums.org/showthread.php?t=2255746") 
    Lenovo Ideapad Y500 LiveUSB Problem
    [https://ubuntuforums.org/showthread.php?t=2095063]("http://ubuntuforums.org/showthread.php?t=2095063")
   Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
        [https://ubuntuforums.org/showthread.php?t=2230919]("http://ubuntuforums.org/showthread.php?t=2230919")
    Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
        [https://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio]("http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio")
    [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
        [https://ubuntuforums.org/showthread.php?t=2247186]("http://ubuntuforums.org/showthread.php?t=2247186")
Phoenix SecureCore Tiano bios setup and secure boot is greyed out. You need to set a Supervisor Password in the Security tab
Samsung w/ Phoenix Tiano SecureCore
[https://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267]("http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267")

**Systems that only boot Windows from UEFI & using efibootmgr to manage UEFI entries.**
    Per UEFI standard you should be able to boot any entry in UEFI boot  menu. But some vendors have modified UEFI code to only boot the Windows  efi file. The UEFI looks for the Windows file name and only boots it.  (Note for Acer, it requires "trust" settings in UEFI)
    Installing Grub for UEFI secure boot is only possible if you have  booted your system using EFI with the 64bit version with secure boot on.  A few systems will only boot with UEFI and secure boot on or with CSM  (BIOS) if secure boot is off. Best to test system to see which modes it  boots in. In secure boot mode it will only show/allow systems that have  secure boot. You may have to change UEFI settings or set password to  allow other devices to boot.

    Backup entire efi partition before making changes.
    
    A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot
 
 In Boot-Repair "Use the standard EFI file" Should do the same as these  manual instrutions by copying shimx64.efi to /EFI/Boot/bootx64.efi for  fallback or hard drive  boot from UEFI menu.

     Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and  name it bootx64.efi  Then boot harddrive entry in UEFI menu.[https://www.tenforums.com/]("http://www.tenforums.com/")
     Older rename of Windows efi file not recommended anymore. (old versions of Boot-Repair did rename the Windows efi file)
    
    From live installer booted in UEFI mode, mount the efi partition on  hard drive, lines with # are comments only: Mount ESP - efi system  partition. check which partition is FAT32 with boot flag. Often sda1 or  sda2 but varies. 
# if your ESP is not sda1 change this to correct partition
        sudo mount /dev/sda1 /mnt
    only if /EFI/Boot not already existing, run the mkdir command,
        sudo mkdir /mnt/EFI/Boot
        sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
    # If new folder created, the bootx64.efi will not exist, skip backup command
    sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
    # make grub be hard drive boot entry in UEFI. Then boot hard drive entry in UEFI menu.
    sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
# You may need new hard drive entry (uses default  of sda1 for ESP):
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
# if not sda1 you must specify drive [COLOR=#ff0000]X[/COLOR] with -d and partition [COLOR=#ff0000]Y [/COLOR]with  - p , see also man efibootmgr
 sudo efibootmgr -c -g -d [COLOR=#ff0000]/dev/sdX[/COLOR] -p[COLOR=#ff0000] Y[/COLOR] -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 

 # confirm entries:
sudo efibootmgr -v

More examples of users who manually moved efi files
[https://ubuntuforums.org/showthread.php?t=2101840]("http://ubuntuforums.org/showthread.php?t=2101840")
[https://ubuntuforums.org/showthread.php?t=2219452]("http://ubuntuforums.org/showthread.php?t=2219452")
[https://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109]("http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109")

    B: Edit Windows BCD to make Ubuntu default (chg'd from grubx64 in case Secure Boot on)
        bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
    [https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)
    UEFI NVRAM boot entries are cached in the BCD store
    BCD has 1:1 mappings for some UEFI global variables
    Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

    C:  Use efibootmgr, if only Ubuntu install, not dual boot, install  to make Windows UEFI description boot grub or shim file (Assumes default  of sda1 for ESP, see links for added parameters for different drive or  partitions) examples are with efibootmgr's default of sda1 for ESP,  additional parameters required if not sda1:
         sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
       If you have Windows to restore Windows boot entry:
         sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

    D: Some install rEFInd which seems to be another workaround and has nice boot icons.
        See section below on rEFInd

    Other work arounds for UEFI that only boots Windows. 
    [https://ubuntuforums.org/showthread.php?t=2234019]("http://ubuntuforums.org/showthread.php?t=2234019")

Restore or create new Ubuntu UEFI boot entry:
sdX is drive, Y is efi partition , if sda2 for example
sudo efibootmgr -c -L ubuntu -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sda -p 1
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

 
**Links to more Info**
    Background and details of what UEFI is.
    [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
    Matthew Garrett's Blog
    [https://mjg59.dreamwidth.org/]("http://mjg59.dreamwidth.org/")
    Details on Ubuntu's shim with 12.10
    [https://falstaff.agner.ch/2012/12/12/secure-boot-implementation-of-ubuntu-12-10-quantal-quetzal/]("http://falstaff.agner.ch/2012/12/12/secure-boot-implementation-of-ubuntu-12-10-quantal-quetzal/")
    They land alongside their unsigned variants in /boot with the file suffix &#8220;.efi.signed&#8221;.

 **Video**  Older versions still similar UEFI install process
     Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
    [https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

    Acer Windows 8 Video on getting into UEFI
        [https://www.youtube.com/watch?v=QGiG1oljjZI]("http://www.youtube.com/watch?v=QGiG1oljjZI")
        Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
        [https://www.youtube.com/watch?v=wNCSbTyUzoM]("http://www.youtube.com/watch?v=wNCSbTyUzoM")
        Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
        [https://www.youtube.com/watch?v=dRMIvY7BiL4]("http://www.youtube.com/watch?v=dRMIvY7BiL4")

Somewhat simple explanation of UEFI:
[https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
 
Acronyms:
UEFI [URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface
[/URL]MOK - Machine Owner Key (MOK) [https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)
ESP/efi -  Efi System Partition for UEFI boot on gpt drive:  [https://en.wikipedia.org/wiki/EFI_System_partition]("http://en.wikipedia.org/wiki/EFI_System_partition")
bios_grub - For BIOS boot on gpt drive: [https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)     
BIOS - Basic Input/Output System [https://en.wikipedia.org/wiki/BIOS]("http://en.wikipedia.org/wiki/BIOS") # must be inside first 2TB of drive
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Some vendors in 2020 are announcing CSM will be eliminated. Systems will be UEFI Class 3 (no CSM).
 Secure Boot - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [https://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
MBR(msdos) [https://en.wikipedia.org/wiki/Master_boot_record]("http://en.wikipedia.org/wiki/Master_boot_record")
SSD [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
RAID [https://en.wikipedia.org/wiki/RAID]("http://en.wikipedia.org/wiki/RAID")
LVM Logical Volume Management [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
    LVM not recommended for newer users, but used with full drive encryption which erases entire hard drive.
Ubuntu [https://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29")
[https://www.ubuntu.com/about/about-ubuntu]("http://www.ubuntu.com/about/about-ubuntu")
Windows BCD - Boot Configuration Data [https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options)
Common Linux terms:
[URL="https://askubuntu.com/questions/691277/ubuntu-glossary-dictionary-of-commonly-used-terms"]https://askubuntu.com/questions/691277/ubuntu-glossary-dictionary-of-commonly-used-terms
[/URL][https://uefi.org/specifications/](https://uefi.org/specifications/)

---

### Post by spryte on 2013-05-25
I thought this should be meantioned somewhere like here, by the "Boot-Repair will convert a BIOS install to UEFI" bit, or on [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode) .

Main Point:
While trying to Convert Ubuntu into EFI mode, If there is a bios_grub flagged partition, it needs to be removed before running boot-repair.

Background:
I was installing and trying various Ubuntu + Mint flavours on my new Samsung 3 series laptop, in dual-boot with Win8. Somewhere along the line I picked up a small (1mb) grub_bios flagged partition, as at least one of the installations happened in legacy mode.

SecureBoot was always disabled. UEFI only, CSM, and legacy were changed as neccessary to get my various Install Media to boot.

Although EFI was detected by boot-repair, grub persisted in looking in this grub_bios partition and not the EFI partition after running boot-repair (with various options including a purge of grub). I confirmed that the grub on the EFI partition was good by "SET"ting it from the grub_rescue prompt and booting the pc to both win8 + linux thereafter.

I eventually fixed my problems by;
- booting a "live" disk in EFI mode.
- deleting the bios_grub flagged partion with gparted.
- running boot-repair again.

This was far easier than most of the googled "help" which was mostly about installing and configuring some other EFI bootmanager manually.  As a linux newbie, I wasn't prepared to put the time into learning all that. I was just going to delete linux partitions and re-install (after ensuring the DVD booted in EFI mode), when I noticed the extra partition.


P.S. Thanks a lot for the consolidated info in your post, it was very helpful.

---

### Post by TheBrewmaster on 2013-06-01
One thing that threw me, when setting up my newly-bought UEFI system for dual-botting Ubuntu (13.04, Raring) is when you use boot repair, it lets you know that you need to go into your UEFI setup (I guess you can't call it BIOS, if you have UEFI) and mark the correct .efi file as trusted, if you have secure boot enabled (My Win8 woudn't boot unless Secure Boot was enabled).  
It makes sense, now that I think about it after the fact, but in order to enable the UEFI setup to mark anything as trusted (and do a few other things), you have to have a password set in the UEFI Setup; on my Acer laptop (InsydeH2O firmware) it was the "Supervisor" password. there's nothing stopping you (with my system, yours may vary) from unsetting the password after you've made your changes and saved them, though I decided to leave it.
Also, unless you need to set it, if the hard disk password setting says "Frozen", you can ignore it.  The hard disk password can only be set/reset if you did a cold boot.  I assume that's probably true for all dydtems, though they may call it something else on other UEFI formware.  

It was pretty frustrating that while I know the "help" within the UEFI firmware is limited, it couldn't have at least given a clue that some settings had to be changed (set a Supervisor password, in this case) in order for other settings to be available to even be selected.  I wasn't able to find a mention of anything about the UEFI setup on Acer's official site, but I got a clue when someone on their Acer User's site happened to mention that he had to set the password in order to get to the additional settings.  

Again, in retrospect, given the purpose of SecureBoot, this actually makes sense, where you have to have changing settings that would get around SecureBoot password-protected by default.  But at 11:30 at night when I had finally gotten to that point in my Ubuntu install, it didn't occur to me to try setting a password to see if that enabled changing any of the settings associated with SecureBoot.

---

### Post by nik6 on 2014-03-14
Here is my info on how to set up Toshiba p-50 dual boot in EFI mode with NIK working properly:


Bios is set to secure boot enabled and nik on.
Latest 13.10 as of today boots OK when secure boot is enabled and fails to boot when it off on this Toshiba P-50 laptop. BIOS has been updated with latest firmware but I think it did not make any difference.
Boot USB stick with ubuntu 13.10 into live boot and at terminal start 'gparted'.

Do not touch any partition except for the one where windows 8 is installed. It is partition #4 from disk start, ntfs resize it down to around 250 gigs
Next after on empty space create Data partition NTFS for around 500 gigs for data storage. It will be partition #5 from disk start.
Next after on empty space create primary partition around 190 gigs ext4 type for Ubuntu install. It will be partition #6 from disk start.
Use the rest of empty space for linux swap partition.

Now reboot into windows 8 - it should be ok on resized partition and it should see 500 gigs Data partition from windows explorer.
Reboot with orange usb stick with ubuntu 13.10 and choose install into ext4 and swap partitions that you done previously.
Choose to install boot loader into linux dedicated partiton. 
Linux will not boot after install as grub is not installed yet. Boot with usb stick again , mount EFI partition with 'disks' and back up all content.
In case boot config goes wrong you can just delete everything on EFI partition and put backed up files and folders back.
After that run
sudo add-apt-repository -y ppa:yannubuntu/boot-repair && sudo apt-get update
Press Enter, then type the following command:
sudo apt-get install -y boot-repair && boot-repair

choose 'recommended repair' and disregard it's whining about 'you should disable secure boot' as it will install.
The problem with grub2 installed on toshiba p50 that it will ask you for F12 key for 6 seconds then it will try to boot from network if nik is enabled for couple of 
minutes first with version 6 then with version 4 network boot even when network boot is on the last position in BIOS. It just disregards bios settings and you can
disable nik in bios to fix that. That is the huge problem of toshiba p-50 and to fix that permanently mount EFI partition with linux 'disks', 
( bios set to EFI boot, NIK enabled, secure boot enabled )
run 
'sudo nautilus' 
to be able to edit it. EFI parttion was mounted on /boot/efi
go to /boot/efi/EFI/Boot/ and rename bootx64.efi to bootx64-GRUB.efi
now copy 
/boot/efi/EFI/ubuntu/shimx64.efi and paste it as
/boot/efi/EFI/Boot/bootx64.efi


Reboot and enjoy. GRUB will load instantly now without trying network boot and windows and ununtu will boot without any problem.

---

### Post by Sciezyna on 2014-04-07
Thank you. This, again, is one of those clear and simple things one needs to do to have eg. Kubuntu 13.10 installed and running on modern hardware - especially one with ATI graphics card installed. :-)

What I did in the end I just installed Kubuntu 13.10 fresh, and instead of trying to boot it from the disk I shoved Boot Repair and repaired the grub mess. It worked nicely.

---

### Post by sam-c on 2014-06-20
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
This was very Helpfull!
Thanks
Uncle Sam

---

### Post by jon-zendatta on 2014-06-28
Recently purchased Acer E1-510, pre-installed with Windows 8. Bios (v 2.02) was unable to read USB iso Ubuntu 14.04 from UEFI.
I downloaded Bios (v 2.07) and changed it to bootable via Unetbootin. Installed/updated Bios, which then gave UEFI/Legacy option. Then installed Ubuntu via Bios Legacy option.:KS

---

### Post by ventrical on 2014-08-06
> **sam-c said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
This was very Helpfull!
Thanks
Uncle Sam


 Checked this out in the USC 14.04.1 Not there. So .. in a way .. not trusted?? Does'nt that defeat the whole security concept of UEFI?

---

### Post by Gordonbp531 on 2014-08-18
> 
 UltraBooks[/B] - Also see examples below

  Ubuntu now installs with Intel SRT on, but when grub sees the RAID grub will not install. So you have to turn the SRT off or set UEFI/BIOS to AHCI and remove the RAID meta data from the drives. Some install Ubuntu to SSD, others install to hard drive and turn SRT back on and have had it work.



That's not actually correct in all cases. Grub will install perfectly OK without disabling RAID. You need to install Grub on the EFI partition. Works perfectly OK with my Lenovo U410 Ultrabook.

---

### Post by oldfred on 2015-01-03
Needs a bit of updating. While Boot-Repair is useful especially for its summary report or understanding what issues there are, it is not now essential in most cases.

Main issue still is many vendors creating systems that require Windows in the UEFI entry.
 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

And many of the work arounds for systems that only boot Windows:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by caezsar on 2015-01-28
You can also use this guide <link snipped> in order to install Ubuntu Server Edition on machines with UEFI, GPT disk with LVM custom partition layout.

---

### Post by kansasnoob on 2015-02-21
Thanks for the efi menu cleanup instructions for grub. I'm learning a tiny bit at a time. Right now I've used "Something else" to replace an existing OS that broke due to a failed upgrade via live DVD:

[http://ubuntuforums.org/showthread.php?t=2266195](http://ubuntuforums.org/showthread.php?t=2266195)

I suspect what happened there was that the upgrade somehow failed to recognize the /EFI/boot partition.

Regardless I've now gone from Win 8.1 + Trusty to Win 8.1 + broken upgrade to Win 8.1 + Precise.

I'm beginning with Precise this time so I can try Precise -> Trusty, Trusty -> Utopic, and Utopic -> Vivid upgrades via live DVD to see what I can blow up :guitar:

---

