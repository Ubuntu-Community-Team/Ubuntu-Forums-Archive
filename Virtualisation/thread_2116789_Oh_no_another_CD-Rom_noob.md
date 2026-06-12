---
title: "Oh no another CD-Rom noob"
date: 2013-02-16
forum: Virtualisation
---

### Post by DaMadHatter on 2013-02-16
Hi their,

Finally made the transition over from Windows, everything has been great on this copy of Linux Ubuntu 12.04LTS x64, So far im loving it and everything has been working perfectly. I am a very advanced windows user, but a complete nub when it comes too Linux. That being said I do have a fairly good understanding of the differences.

I recently decided too try VMware products with the intention of installing Windows 7 x64, that being said I was capable or creating a Windows XP VMware install that was flawless.

However when I tried my hand at the Win7 install my cd-rom stopped being recognized, (IE - It continued too fall back too the PXE intel 1000e network install, on a fully bootable and tested DVD.) Further investigation prompted me to do some googleing and I came up with the following.

```
polly@tweaks-PC:~$ dmesg | grep cd
[    0.606553] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.606554] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.606555] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.606556] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.606558] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.606650] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.606651] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.606653] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.606655] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.606657] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    1.471369] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.471387] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.471398] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.471437] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.471444] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.471466] ehci_hcd 0000:00:12.2: debug port 1
[    1.471483] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    1.480047] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.480224] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.480236] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.480270] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.480277] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.480295] ehci_hcd 0000:00:13.2: debug port 1
[    1.480313] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    1.492033] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.492212] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.492230] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.492243] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.492279] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.492299] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.552194] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.552206] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.552245] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.552258] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.612190] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.612201] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.612239] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.612259] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    1.672190] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.672202] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.672240] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.672253] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    1.732185] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.732197] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.732236] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.732250] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe9fa000
[    1.792272] uhci_hcd: USB Universal Host Controller Interface driver
[    1.994345] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.994348] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.056033] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[    2.508036] usb 4-1: new low-speed USB device number 2 using ohci_hcd
[   36.200035] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[  605.292062] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[ 3637.566089] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3677.616300] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3717.666475] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3757.716694] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3797.750956] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3837.801106] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3877.851258] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3917.901505] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3957.951738] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 3998.001888] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4038.052160] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4078.102359] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4118.152540] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4158.202753] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4198.252957] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4238.303167] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4278.353356] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4318.403557] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4358.453787] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4398.503981] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4438.554197] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4478.604407] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4518.654604] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4558.704834] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4598.755022] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4638.805269] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4678.855417] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4718.905669] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4758.955850] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4799.232099] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4839.282272] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4879.332501] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[ 4919.382680] [UFW BLOCK] IN=eth0 OUT= MAC=01 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 

```So I guess my question boils down to is ufw blocking my cd-rom in some way? As I have not configured ufw in any way other then too enable it, I dont see how.

And why would I be seeing multi-cast addressing coming from my gateway? (IE - 192.168.1.254) In relation too a CD-Rom Query in the terminal?

Yes I do have ufw enabled as well as the gfuw installed. I do have plans to get into the IPtables, as I do have some experience with this, just havent had the time at present.

Anyone that has any idea's about this care to venture a guess? or some troubleshooting techniques? 

Thank You In Advance!!

Just a quick FYI - Disk Utility is showing the exact model of Drive ( Lite-On DVDRW LH-20A1S), Port 3 of SATA Host Adapter, Device: /dev/sr0 - Connection SCSI after testing several other CD's and DVD's I can verify the drive is reading some disks but not all, seems too be somewhat intermittent.

---

### Post by Bashing-om on 2013-02-16
DaMadHatter; Hi ! welcome to the forum.

I don't recon linux recognizes the cd drive as the identifier "cd" ; try "sr1".
Off the top of my head I do not recall the command to see how the drives are identified.
```
ls -l /dev/sr1
``` will verify if "sr1'.

As to why VM/Windows does not recognize the drive, I have no knowledge and unable to advise.

[INDENT]not much help, but happyness in ubuntu to ya
[/INDENT]

---

### Post by DaMadHatter on 2013-02-16
Thanks for your reply Bashing-om,

I did give this a shot here is the output -

```
ls: cannot access /dev/sr1: No such file or directory
```I tried again with : /dev/sr0 and it successfully returned it.

 I think this is an issue mainly too do with VMware player and DVD's as some googeling has turned up similar results. Seems to be working in Ubuntu just fails after the VMware is loaded.

I tried updating too latest versions but alas, no results. Perhaps I will try turning the disk into an ISO, see what the results are.

Thanks for your post.

Okay apparently I was wrong, after downloading k9copy /dev/sr0 cannot be open or access too create an ISO.

So I decided too try in the terminal the following:

dd if=/dev/cdrom0 of=isofile.iso

Which failed and returned - dd: opening `/dev/cdrom0': No such file or directory

So I decided too try what Disk Utility is telling me the drive path is:

dd if=/dev/sr0 of=isofile.iso
The Drive spun up ever so slowly and stayed active for several mins before completing, and creating isofile.iso.

Can anyone tell me how I might go about changing the drive from being at /dev/sr0 to /dev/cdrom0 ?

---

### Post by HereInOz on 2013-02-16
Have you tried VirtualBox as a VM manager?  I have been using it for some years with no difficulty.

The only thing you need to do after installation is to add your user to the vboxusers group, and then install your guest OS.

---

### Post by Bashing-om on 2013-02-16
DaMadHatter;

In ubuntu there is the mechanism termed "symbolic link" that maps the device name "cdrom0" to the identifier "sr0" (in your case, my cd rom is "sr1"). I have been castigating myself since my last post that I do not recall how to see this relationship.
Another way to identify the device name is while a disk is inserted into the cdrom run the terminal command 
```
mount
``` will list all mount points inclusive of the cd drive.

Got one !
```
ls -l /dev/disk/by-id/
```To view the physical device identifiers; drives and partitions appear twice, the first time as ata and the second time as scsi.

But that does not address why the Virtual Hardware (driver ?) does not see the device .
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by DaMadHatter on 2013-02-16
HereInOz;

Thank you for your post, I will have a look at VM Manager see if it helps, could always use it for system related performance and future related problems.

Bashing-om:

Thanks again for your reply, after successfully creating the ISO through the terminal I was able too successfully install my guestOS, oddly enough after the instillation I was surprised too see that under My Computer the disk was not only visible again, I could explore all the content on the disk. 

Even though strangely enough I still cannot see the disk in Ubuntu, im going too try what you advised and will post back the results.

Thanks again!!

---

### Post by DaMadHatter on 2013-02-16
Bashing-om:

Here are the results of the commands run from terminal.

```
polly@tweaks-PC:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/polly/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=polly)
gvfs-fuse-daemon on /home/tweak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tweak)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)

```and:
```
polly@tweaks-PC:~$ ls -1 /dev/disk/by-id/
ata-LITE-ON_DVDRW_LH-20A1S
ata-ST1000DM003-9YN162_S1D0XB6L
ata-ST1000DM003-9YN162_S1D0XB6L-part1
ata-ST1000DM003-9YN162_S1D0XB6L-part2
ata-ST1000DM003-9YN162_S1D0XB6L-part5
dm-name-cryptswap1
dm-uuid-CRYPT-PLAIN-cryptswap1_unformatted
scsi-SATA_ST1000DM003-9YN_S1D0XB6L
scsi-SATA_ST1000DM003-9YN_S1D0XB6L-part1
scsi-SATA_ST1000DM003-9YN_S1D0XB6L-part2
scsi-SATA_ST1000DM003-9YN_S1D0XB6L-part5
wwn-0x5000c5004aa425d4
wwn-0x5000c5004aa425d4-part1
wwn-0x5000c5004aa425d4-part2
wwn-0x5000c5004aa425d4-part5

```

I do see the drive listing by ID, but not in the mount command, still a little unclear as too why however. I will keep working at this, as the disk utility is showing /dev/sr0, little surprised it didnt show here.

---

### Post by Bashing-om on 2013-02-16
DaMadHatter;
Do not know what I can say. Here is my totally different output with the same commands:
```
sysop1@1204-a:~$ mount
/dev/sdc1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,noexec,nosuid)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/sysop1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sysop1)
/dev/sr1 on /media/Ubuntu 12.04.1 LTS amd64 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


sysop1@1204-a:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 Feb 16 20:21 ata-HL-DT-STDVD-RAM_GH22NP20 -> ../../sr1
lrwxrwxrwx 1 root root  9 Feb 16 11:21 ata-TOSHIBA_DVD-ROM_SD-M1502_7100207541 -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1463479 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1463479-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1463479-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1463479-part5 -> ../../sdc5
lrwxrwxrwx 1 root root  9 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1745533 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW1745533-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Feb 16 11:21 ata-WDC_WD5000ABYS-01TNA0_WD-WCAPW4886797-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1463479 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1463479-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1463479-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1463479-part5 -> ../../sdc5
lrwxrwxrwx 1 root root  9 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1745533 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW1745533-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Feb 16 11:21 scsi-SATA_WDC_WD5000ABYS-_WD-WCAPW4886797-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Feb 16 11:21 wwn-0x50014ee2559795df -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee2559795df-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 16 11:21 wwn-0x50014ee255d84d23 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee255d84d23-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Feb 16 11:21 wwn-0x50014ee2aaecf760 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee2aaecf760-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee2aaecf760-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Feb 16 11:21 wwn-0x50014ee2aaecf760-part5 -> ../../sdc5
sysop1@1204-a:~$ 

```Hopefully a guru of linux will see this thread and explain to us.

---

### Post by DaMadHatter on 2013-02-17
Much appreciate your feed back here Bashing-om, thanks for your assistance thus far. :)

Much appreciation.

---

### Post by DaMadHatter on 2013-02-17
After some further diagnostics and troubleshooting, I have found what appears to be the root of the problem, the drive itself is experiencing Hardware Related problems. :sad:

Looks like its time for a new one.
Thanks too all who posted much appreciate your support.

---

### Post by Bucky Ball on 2013-02-17
*Thread moved to **Virtualisation**.*


(PS: Hi HereInOz. I am in Adelaide, too. ;))

---

### Post by Bashing-om on 2013-02-17
DaMadHatter;
It's a pain to replace and image a drive, but is good the fault is isolated and fixable !


[INDENT]best to ya, enjoy ubuntu
[/INDENT]

---

