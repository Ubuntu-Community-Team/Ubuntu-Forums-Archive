---
title: "usb flash drive works in 12.04 but not in 13.10"
date: 2013-09-08
forum: Ubuntu Development Version
---

### Post by ortermagic on 2013-09-08
Hi! has anyone any knowhow to explain why a flashdrive (kingston usb) would mount in 12.04 but fail to mount in saucy salamander... This is the first fault i've found in 13.10 which I have been trialling for the past three or four months.
 I am very impressed with this distro and the usb anomality is the first problem I've had```
Disk /dev/sdf: 16.0 GB, 15971909632 bytes
100 heads, 36 sectors/track, 8665 cylinders, total 31195136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2416    31195135    15596360    c  W95 FAT32 (LBA)
ortermagic@ortermagic-Centurion-CPD-1303:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 18e3:9102 Fitipower Integrated Technology Inc Multi Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 040b:2013 Weltrend Semiconductor 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=#ff0000]Bus 001 Device 006: ID 0951:1643 Kingston Technology DataTraveler G3[/COLOR]
Bus 001 Device 002: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

I have highlighted the device in red as it appears in  lsusb.
It does not appear in gparted

---

### Post by carlwsnyder on 2013-09-08
Does it show up when you do an **fdisk -l** (the option is a lower case 'L')?  How is it formatted: NTFS, FAT32, ext4, or some other file system?

---

### Post by VMC on 2013-09-08
What kernel are you using that it fails in?

---

### Post by ortermagic on 2013-09-09
Hi, thanks for the response, the flash dongle does not show up using **fdisk -l**  I get the following...
> ortermagic@ortermagic-Centurion-CPD-1303:~$ fdisk -l
ortermagic@ortermagic-Centurion-CPD-1303:~$ 
 It is on /dev/sdb1 formatted to fat32.
The kernel is..3.10.0-6 generic
Hope that's a help

---

### Post by sudodus on 2013-09-09
You need root privileges for fdisk.

```
 sudo fdisk -lu
```

I have heard of temporary problems with some USB drives also in 13.04. It is probably a driver, that is not 100%. The problem is that the USB devices vary (both hardware and firmware), and it is hard to make drivers that cooperate well with all of them. With another version of the kernel you might be able to mount it.

---

### Post by ortermagic on 2013-09-09
Thanks sudodus, Didn't know that, well truth is I don't really know all that much about anything any more ;)
> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo fdisk -lu
[sudo] password for ortermagic: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     9766911     4882432   82  Linux swap / Solaris
/dev/sda2         9768958   976770446   483500744+   5  Extended
/dev/sda5         9768960   482631679   236431360   83  Linux
/dev/sda6       482633728   976770446   247068359+  83  Linux

Disk /dev/sdb: 16.0 GB, 15971909632 bytes
100 heads, 36 sectors/track, 8665 cylinders, total 31195136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

[COLOR=#ff0000]   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2416    31195135    15596360    c  W95 FAT32 (LBA)[/COLOR]
ortermagic@ortermagic-Centurion-CPD-1303:~$ 


This is the terminal output I got, does it give you a clue?

---

### Post by sudodus on 2013-09-09
The red text indicates that the system finds a FAT32 partition on the 16GB drive. I suppose it is your pendrive.

Can you mount it with the following command?

```
sudo mount [COLOR=#ff0000]/dev/sdb1[/COLOR] /mnt
```

Check with ```
df
```

---

### Post by ortermagic on 2013-09-09
sudodus, I followed your advice the device seems to have mounted, but I cannot find it in any of the usual places.
enclosed screen shot may be useful for someone with an educated eye

---

### Post by ortermagic on 2013-09-09
according to parted it is already mounted on /mnt

---

### Post by sudodus on 2013-09-09
You change directory in file browser to

***/mnt***

and you should find it.

If you unmount the partition with

```
sudo umount /mnt
```

unplug and replug the drive, maybe you can find it and mount it with the file browser. Depending on version it may appear in different places.

12.04:**[FONT=courier new] /media/'label'[/FONT]** (if there is a label)

13.10: [FONT=courier new]**/media/'username'/'label'**[/FONT]

If there are problems, you may need to add execute permissions for all for the /media/'username' directory.

```
sudo chmod ugo+x /media/'username'
```

where 'username' should be replaced with your current user name.

```
sudo chmod ugo+x /media/ortermagic
```

---

### Post by Bucky Ball on 2013-09-09
*Thread moved to **Ubuntu +1**.*

Please post all support requests for 13.10 in this sub-forum, please. It is not released yet and testing.

---

### Post by ortermagic on 2013-09-09
followed your instructions

> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo umount /mnt
[sudo] password for ortermagic: 
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo chmod ugo+x /media/ortermagic
ortermagic@ortermagic-Centurion-CPD-1303:~$ 



I got nothing I looked in media, it was empty :(

---

### Post by sudodus on 2013-09-09
Did you unplug and replug the pendrive?

---

### Post by ortermagic on 2013-09-09
Cheers Bucky, maybe I have stumbled on a bug by accident

---

### Post by ortermagic on 2013-09-09
Yes, I did that too

---

### Post by sudodus on 2013-09-09
OK, so you need to mount the pendrive manually with

```
sudo mount [COLOR=#ff0000]/dev/sdb1[/COLOR] /mnt
```

Please do that again, and try to verify that you can see and manage it with the file browser (at ***/mnt***). For example make a file and remove it, or copy some file to or from the pendrive.

---

### Post by ortermagic on 2013-09-09
i'm a bit lost at the moment

---

### Post by ortermagic on 2013-09-09
Did that here's the result
> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for ortermagic: 
ortermagic@ortermagic-Centurion-CPD-1303:~$ 



---

### Post by sudodus on 2013-09-09
If I understand correctly, you could mount the drive manually with the mount command (see post #8). That is what I suggest you do again. But it may help to reboot the computer, if things are mixed up right now.

If it will be mounted, it should be possible to see at /mnt

So try these commands

```
df
```

```
ls -l /mnt   # ell ess space minus ell space slash emm enn tee
```

Please post the output of those commands!

---

### Post by ortermagic on 2013-09-09
Sorry to be a bit opaque but I tried to copy into media but I do not seem to have the permissions necessary
the media folder is empty as is the mnt folder I am still unable to see the pendrive which works in 12.04 flawlessly
> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for ortermagic: 
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ 

(how do i access do I sudo? could you possibly write a command line prescription for me please... /mnt using the terminal?)

---

### Post by Bucky Ball on 2013-09-09
Sorry to barge in, but should there be a mount point created in /mnt for it, for example:
```

sudo mkdir /mnt/Pendrive
sudo mount /dev/sdb1 /mnt/Pendrive
```

Not sure where this command mounts it to:

```
sudo mount /dev/sdb1 /mnt
```

? Or am I missing something? I'm aware you are fairly expert, sudodus, so I probably am missing something.

---

### Post by ortermagic on 2013-09-09
There's some weird stuff going on here, odd bits and peices by various family members :eek: but if it makes sense to you :cool:


> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for ortermagic: 
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda6      243191836  8987108 221851312   4% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1981288       12   1981276   1% /dev
tmpfs             404856     1148    403708   1% /run
none                5120        0      5120   0% /run/lock
none             2024264      220   2024044   1% /run/shm
none              102400       56    102344   1% /run/user
/dev/sda5      232590304 41270172 179482180  19% /media/ortermagic/c6e29b9f-f1db-4fd3-b849-2173f4eb10b0
/dev/sdb1       15581128  7563728   8017400  49% /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ ls -l /mnt 
ortermagic@ortermagic-Centurion-CPD-1303:~$ 



---

### Post by ortermagic on 2013-09-09
Bucky Ball I just tried to mkdir in /mnt but the folder is still empty
yet the terminal tells me the pendrive is mounted, see below
> ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mkdir /mnt/Pendrive
[sudo] password for ortermagic: 
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt/Pendrive
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ 


this is getting weird

---

### Post by ortermagic on 2013-09-09
I have just logged in to 12.04 and I find that it would appear the pendrive has been working in that distro all along
It would appear that 12.04 is leeching into 13.10 so could it be that there is an overlap causing the 13.10 terminal to be seeing the files in 12.04,
heres the output from 12.04
> ortermagic@russet:~$ sudo fdisk -lu
[sudo] password for ortermagic: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     9766911     4882432   82  Linux swap / Solaris
/dev/sda2         9768958   976770446   483500744+   5  Extended
/dev/sda5         9768960   482631679   236431360   83  Linux
/dev/sda6       482633728   976770446   247068359+  83  Linux

Disk /dev/sdb: 16.0 GB, 15971909632 bytes
100 heads, 36 sectors/track, 8665 cylinders, total 31195136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2416    31195135    15596360    c  W95 FAT32 (LBA)
ortermagic@russet:~$ 

12.04 can still read the kingston and it works as it should

---

### Post by cariboo on 2013-09-09
Usb drives should mount automatically in /media/user_name/string

where user_name is your user name, and string is generated when the device is mounted, for example on my system sdc1 is mounted to /media/cariboo/DDF3-0260.

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.7G  2.4G  74% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.6M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  544K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   72G  135G  35% /home
/dev/sdc1       3.8G  186M  3.6G   5% /media/cariboo/DDF3-0260
```

I always use dmesg to check if a device is mounted, if nautilus doesn't open. The output should look something like this:

```
dmesg | tail -n15
[ 2406.329144] scsi 4:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[ 2406.329373] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 2406.333631] sd 4:0:0:0: [sdc] 7913471 512-byte logical blocks: (4.05 GB/3.77 GiB)
[ 2406.334641] sd 4:0:0:0: [sdc] Write Protect is off
[ 2406.334644] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 2406.335501] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2406.335504] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2406.339024] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2406.339030] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2406.343142]  sdc: sdc1
[ 2406.345895] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2406.345901] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2406.345905] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

---

### Post by ortermagic on 2013-09-09
Thanks for the input Cariboo did the dmesg got a huge output, i cut a snip out that was relevant to the pendrive
>   1.875774] usb 1-5: New USB device found, idVendor=0951, idProduct=1643
[    1.875777] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.875779] usb 1-5: Product: DataTraveler G3
[    1.875780] usb 1-5: Manufacturer: Kingston
[    1.875781] usb 1-5: SerialNumber: 001CC0EC3466AC20D71E4B9C
[    1.877597] usb-storage 1-5:1.0: USB Mass Storage device detected
[    1.877763] scsi8 : usb-stor 
but it dont mean a thing cos the pendrive is only readable on the 12.04 partition of my hd, I guess that's the problem, somehow there is cross transferance between the partitions I dont know enough about the archetecture to attempt a fix I will try to find out whether the kernels are screwing up.

can anyone tell me how to get the kernel info using the terminal

---

### Post by Mateusz Stachowski on 2013-09-09
If you are on 13.10 I would start with update to the kernel because the one that you have installed is old. Saucy had a couple releases of 3.11 kernels now and the newest is 3.11.0.5.6. I think that you might be dealing with a bug that caused [exceedingly long time]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934") to mount USB drives.

There was also a thread about it in Ubuntu +1 sub-forum which is marked as SOLVED:

[Current Kernel causes blkid USB error]("http://ubuntuforums.org/showthread.php?t=2164982")

---

### Post by sudodus on 2013-09-09
> **Bucky Ball said:**
> Sorry to barge in, but should there be a mount point created in /mnt for it, for example:
```

sudo mkdir /mnt/Pendrive
sudo mount /dev/sdb1 /mnt/Pendrive
```

Not sure where this command mounts it to:

```
sudo mount /dev/sdb1 /mnt
```

? Or am I missing something? I'm aware you are fairly expert, sudodus, so I probably am missing something.

*@ Bucky Ball & cariboo907*: For temporary use, I have mounted to /mnt hundreds of times. I think there is something wrong with the USB drivers at least in some kernel versions, that creates problems with some pendrives.There are other threads at the UF about it, for example this one [slow-mounting pendrive issue (unison related?)]("http://ubuntuforums.org/showthread.php?t=2169702") and this one [Ubuntu doesn't see usb SanDisk]("http://ubuntuforums.org/showthread.php?t=2170633")


*@ **ortermagic*: Mounting a drive to /mnt should make it available for reading and writing, at least as root. As a final attempt, I suggest that you try (when when the pendrive is mounted to /mnt)

```
sudo ls -l /
sudo ls -l /mnt
```

```
sudo touch /mnt/empty
sudo ls -l /mnt/empty

```
```
sudo echo "hello world" > /mnt/hello.txt
sudo cat /mnt/hello.txt
```

---

### Post by sudodus on 2013-09-09
> **Mateusz Stachowski said:**
> If you are on 13.10 I would start with update to the kernel because the one that you have installed is old. Saucy had a couple releases of 3.11 kernels now and the newest is 3.11.0.5.6. I think that you might be dealing with a bug that caused [exceedingly long time]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934") to mount USB drives.

There was also a thread about it in Ubuntu +1 sub-forum which is marked as SOLVED:

[Current Kernel causes blkid USB error]("http://ubuntuforums.org/showthread.php?t=2164982")

+1

---

### Post by ortermagic on 2013-09-09
That's funny cos I have been doing daily updates for the last two months...are the kernel updates separate, and why would the pendrive read from a different partition?

---

### Post by sudodus on 2013-09-09
A small fraction of all the updates are kernel updates. Probably you have a few kernels, that are ***available to select at the grub menu.*** You can also see files belonging to different kernels in /boot

```
 ls -l /boot
```

The difference between 12.04 and 13.10: They are systems with different kernels and drivers. That there are different partitions has no influence.

---

### Post by ortermagic on 2013-09-09
That does'nt explain why my 13.10 install writes the mount of my usb dongle to the adjacent 12.04 tho

---

### Post by sudodus on 2013-09-09
Sorry, but I don't understand what you mean by
> my 13.10 install writes the mount of my usb dongle to the adjacent 12.04

---

### Post by ortermagic on 2013-09-09
Sorry if I have not made myself clear, how else do I explain that the pendrive is *recognised as mounted in 13.10* when there is no file in media to support it, whereas on the working 12.10 the pendrive files are in media.
 I am using 3.10.0-6 generic on 13.10 and 3.2.something on the 12.04 these two distros share a 500gb hd half and half.
 So it seems to me that 13.10 is* looking over the partition* seeing the drive as mounted, already active, there.
 That's not very scientific I know, but I like to think i'm a bit intuitive.
Thanks everyone, I have learned something more, I've never really investigated the kernel till now that's another few cups of coffee for the future.;)

---

### Post by VMC on 2013-09-09
ortermagic,

Do this. unplug the usb device, then monitor the output of syslog,```
tail -f /var/log/syslog
```
,  then plug the usb device back in.
Wait for either it got mount or 5 minutes. Then copy the results back here. 
[When you've copy&paste, then Ctrl+c will exit the tail.]

Example:
```
Sep  9 15:27:04 0823 kernel: [ 2251.907460] usb 2-8: **new full-speed USB device** number 5 using ohci-pciSep  9 15:27:04 0823 kernel: [ 2252.123545] usb 2-8: New USB device found, idVendor=0ea0, idProduct=6803
Sep  9 15:27:04 0823 kernel: [ 2252.123558] usb 2-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  9 15:27:04 0823 kernel: [ 2252.123566] usb 2-8: Product: Solid state disk
Sep  9 15:27:04 0823 kernel: [ 2252.123571] usb 2-8: Manufacturer: USB
Sep  9 15:27:04 0823 kernel: [ 2252.123577] usb 2-8: SerialNumber: 22D07D7386D8C6F
Sep  9 15:27:04 0823 kernel: [ 2252.126677] usb-storage 2-8:1.0: USB Mass Storage device detected
Sep  9 15:27:04 0823 kernel: [ 2252.126850] scsi8 : usb-storage 2-8:1.0
Sep  9 15:27:04 0823 mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-8"
Sep  9 15:27:04 0823 mtp-probe: bus: 2, device: 5 was not an MTP device
Sep  9 15:27:05 0823 kernel: [ 2253.133280] scsi 8:0:0:0: Direct-Access     OTi      Flash Disk       1.11 PQ: 0 ANSI: 2
Sep  9 15:27:05 0823 kernel: [ 2253.133990] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep  9 15:27:05 0823 kernel: [ 2253.144227] sd 8:0:0:0: [sdd] 516096 512-byte logical blocks: (264 MB/252 MiB)
Sep  9 15:27:05 0823 kernel: [ 2253.151242] sd 8:0:0:0: [sdd] Write Protect is off
Sep  9 15:27:05 0823 kernel: [ 2253.151256] sd 8:0:0:0: [sdd] Mode Sense: 03 00 00 00
Sep  9 15:27:05 0823 kernel: [ 2253.158248] sd 8:0:0:0: [sdd] No Caching mode page present
Sep  9 15:27:05 0823 kernel: [ 2253.158263] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Sep  9 15:27:05 0823 kernel: [ 2253.198298] sd 8:0:0:0: [sdd] No Caching mode page present
Sep  9 15:27:05 0823 kernel: [ 2253.198316] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Sep  9 15:27:06 0823 kernel: [ 2253.208348]  sdd: sdd1
Sep  9 15:27:06 0823 kernel: [ 2253.246291] sd 8:0:0:0: [sdd] No Caching mode page present
Sep  9 15:27:06 0823 kernel: [ 2253.246301] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Sep  9 15:27:06 0823 kernel: [ 2253.246308] sd 8:0:0:0: [sdd] Attached SCSI removable disk
Sep  9 15:27:08 0823 kernel: [ 2255.207708] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
```

---

### Post by sudodus on 2013-09-09
Please try all these commands (in 13.10) in a row and note carefully what happens after each step, just to check if you can mount the pendrive manually and after that actually read and write file to and from it. After rebooting

Plug in the pendrive and wait for 10 seconds.

1. Try to mount the pendrive

```
sudo mount /dev/sdb1 /mnt
```

2. Check if mounted and how it is mounted. The pendrive should be mounted now.

```
df
```

```
cat /etc/mtab
```

3. If the pendrive is not mounted (not found by df), please wait for 5 minutes and try again

(go back to item 1. a couple of times before giving up.)

4. Try to list files and watch the permissions

```
sudo ls -l /
sudo ls -l /mnt
```

5. Try to create an empty file in the pendrive and check that it is there

```
sudo touch /mnt/empty
sudo ls -l /mnt/empty

```

6. Try to create a file and write contents to it, check that it is there, and that it's content can be read

```

sudo -s  # enter a superuser shell
echo "hello world" > /mnt/hello.txt
ls -l /mnt
cat /mnt/hello.txt
exit   # exit from the superuser shell (important to remember this command)

```

7. Check that the pendrive is mounted (after the writing tests)

```
df
```

8. Try to unmount the pendrive

```
sudo umount /mnt
```

9. Check if the pendrive is mounted (after trying to unmount the pendrive). It should *not* be mounted now.

```
df
```

10. Check again if the files are there (at ***/mnt***)

```
sudo ls -l /mnt
```

If the pendrive was mounted there, when you wrote to*** /mnt***, the files should be in the pendrive, and should not be seen at ***/mnt*** after unmounting. But they should be seen again after mounting the pendrive (in 12.04 or 13.10 or another computer).

---

### Post by ortermagic on 2013-09-09
there you go man
 > ortermagic@ortermagic-Centurion-CPD-1303:~$ tail -f /var/log/syslog
Sep 10 00:29:24 ortermagic-Centurion-CPD-1303 dbus[634]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Sep 10 00:29:24 ortermagic-Centurion-CPD-1303 dbus[634]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Sep 10 00:29:28 ortermagic-Centurion-CPD-1303 dbus[634]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Sep 10 00:29:28 ortermagic-Centurion-CPD-1303 udisksd[2144]: udisks daemon version 2.1.0 starting
Sep 10 00:29:28 ortermagic-Centurion-CPD-1303 dbus[634]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep 10 00:29:28 ortermagic-Centurion-CPD-1303 udisksd[2144]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep 10 00:31:00 ortermagic-Centurion-CPD-1303 whoopsie[1053]: online
Sep 10 00:31:52  whoopsie[1053]: last message repeated 3 times
Sep 10 00:32:48  whoopsie[1053]: last message repeated 2 times
Sep 10 00:32:48 ortermagic-Centurion-CPD-1303 kernel: [  648.690889] usb 1-5: USB disconnect, device number 3
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.096043] usb 1-5: new high-speed USB device number 4 using ehci-pci
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.230623] usb 1-5: New USB device found, idVendor=0951, idProduct=1643
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.230636] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.230643] usb 1-5: Product: DataTraveler G3
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.230648] usb 1-5: Manufacturer: Kingston
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.230653] usb 1-5: SerialNumber: 001CC0EC3466AC20D71E4B9C
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.231685] usb-storage 1-5:1.0: USB Mass Storage device detected
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 kernel: [  688.231790] scsi10 : usb-storage 1-5:1.0
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-5"
Sep 10 00:33:27 ortermagic-Centurion-CPD-1303 mtp-probe: bus: 1, device: 4 was not an MTP device
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.067157] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler G3  1.00 PQ: 0 ANSI: 4
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.067785] sd 10:0:0:0: Attached scsi generic sg2 type 0
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.070345] sd 10:0:0:0: [sdb] 31195136 512-byte logical blocks: (15.9 GB/14.8 GiB)
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.072599] sd 10:0:0:0: [sdb] Write Protect is off
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.072612] sd 10:0:0:0: [sdb] Mode Sense: 2f 00 00 00
Sep 10 00:33:29 ortermagic-Centurion-CPD-1303 kernel: [  690.075799] sd 10:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA



---

### Post by ortermagic on 2013-09-09
thats a reply to VLC I will now run sudodu's  precription,
hang on!

---

### Post by ortermagic on 2013-09-09
sudodus I have followed your prescription as follows..

```
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for ortermagic: 
ortermagic@ortermagic-Centurion-CPD-1303:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda6      243191836 8928344 221910076   4% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1981288       4   1981284   1% /dev
tmpfs             404856    1160    403696   1% /run
none                5120       0      5120   0% /run/lock
none             2024264     152   2024112   1% /run/shm
none              102400      36    102364   1% /run/user
/dev/sdb1       15581128 7563736   8017392  49% /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ cat /etc/mtab
/dev/sda6 / ext2 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=ortermagic 0 0
/dev/sdb1 /mnt vfat rw 0 0
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo ls -l /
total 136
drwxr-xr-x   2 root root  4096 Sep  7 10:58 bin
drwxr-xr-x   3 root root  4096 Sep  7 10:59 boot
drwxr-xr-x   2 root root  4096 Jul 17 19:13 cdrom
drwxr-xr-x  17 root root  4460 Sep 10 00:37 dev
drwxr-xr-x 146 root root  8192 Sep 10 00:43 etc
drwxr-xr-x   3 root root  4096 Jul 17 19:13 home
lrwxrwxrwx   1 root root    32 Jul 28 02:52 initrd.img -> boot/initrd.img-3.10.0-6-generic
lrwxrwxrwx   1 root root    33 Jul 28 02:51 initrd.img.old -> /boot/initrd.img-3.10.0-6-generic
drwxr-xr-x  26 root root  4096 Sep  8 19:58 lib
drwxr-xr-x   2 root root  4096 Aug  2 09:05 lib32
drwxr-xr-x   2 root root  4096 Aug  2 09:05 lib64
drwxr-xr-x   2 root root 49152 Jul 17 19:10 lost+found
drwxr-xr-x  11 root root  4096 Sep  8 16:46 media
drwxr-xr-x  19 root root 16384 Jan  1  1970 mnt
drwxr-xr-x   2 root root  4096 Jul 17 08:31 opt
dr-xr-xr-x 206 root root     0 Sep 10 00:21 proc
drwx------   7 root root  4096 Aug 18 18:36 root
drwxr-xr-x  24 root root   760 Sep 10 00:29 run
drwxr-xr-x   2 root root  8192 Sep  7 10:57 sbin
drwxr-xr-x   2 root root  4096 Jul 17 08:31 srv
dr-xr-xr-x  13 root root     0 Sep 10 00:22 sys
drwxrwxrwt   7 root root  4096 Sep 10 00:44 tmp
drwxr-xr-x  12 root root  4096 Jul 17 19:30 usr
drwxr-xr-x  13 root root  4096 Jul 17 08:38 var
lrwxrwxrwx   1 root root    29 Jul 28 02:52 vmlinuz -> boot/vmlinuz-3.10.0-6-generic
lrwxrwxrwx   1 root root    29 Jul 28 02:51 vmlinuz.old -> boot/vmlinuz-3.10.0-6-generic
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo ls -l /mnt
total 1919400
-rwxr-xr-x  1 root root   3247976 Dec  2  2012 Adam Ant_s, New Single _Cool Zombie_ [Official Preview Trail.mp4
-rwxr-xr-x  1 root root 106660241 Jul  9  2012 amd-driver-installer-12-6-x86.x86_64.run
-rwxr-xr-x  1 root root      1050 Oct  6  2012 amd-driver-installer-12-9-x86.x86_64.run
-rwxr-xr-x  1 root root     87451 Jul 16 18:43 andy-murray-dog-medal.jpg
-rwxr-xr-x  1 root root    178166 Jul 16 18:38 andy murray.jpg
-rwxr-xr-x  1 root root     67687 Jul 16 18:54 Andy-Murray.jpg
-rwxr-xr-x  1 root root    155772 Jul 16 16:31 Andy-Murray-of-Great-Britain-holds-trophy-2038035.jpg
-rwxr-xr-x  1 root root     21618 Jun 19 19:38 arch.odt
-rwxr-xr-x  1 root root  50650432 Dec 27  2012 army of two.wav
-rwxr-xr-x  1 root root  47729248 Dec 27  2012 beneath your beautiful.wav
-rwxr-xr-x  1 root root    323184 Nov 30  2012 Bike Riding.pptx
-rwxr-xr-x  1 root root   1368151 Jan 21  2013 bikes.PPTX.odp
-rwxr-xr-x  1 root root     53777 Jul  4 12:40 bio adam.odt
-rwxr-xr-x  1 root root  53648743 Oct 18  2012 blender-2.64a-linux-glibc27-x86_64.tar.bz2
drwxr-xr-x  2 root root      8192 Nov 15  2012 canada pics
-rwxr-xr-x  1 root root      5579 Nov 29  2012 carl andrej.odt
-rwxr-xr-x  1 root root     30360 Jun 20 12:29 citylit.odt
drwxr-xr-x  4 root root      8192 Jul 17  2012 claires
drwxr-xr-x  2 root root      8192 May 18  2012 claires animation starts
drwxr-xr-x 14 root root      8192 Sep  8 18:28 claires blender tuts 1
-rwxr-xr-x  1 root root    563332 Jun 29  2012 claires.zip
drwxr-xr-x  3 root root      8192 Feb 26  2011 Conky-lua
-rwxr-xr-x  1 root root  36404368 Dec 27  2012 dear darling.wav
-rwxr-xr-x  1 root root  39144448 Dec 27  2012 dont wake me up.wav
-rwxr-xr-x  1 root root    462667 Feb  7  2009 DSC00110.JPG
-rwxr-xr-x  1 root root    145842 Feb  7  2009 DSC00117.JPG
-rwxr-xr-x  1 root root    546600 Feb  7  2009 DSC00118.JPG
-rwxr-xr-x  1 root root    125683 Feb 24  2009 DSC00145.JPG
-rwxr-xr-x  1 root root     25088 Nov 22  2012 dutch.doc
drwxr-xr-x  2 root root      8192 Apr  2 13:58 ed sheeran
-rwxr-xr-x  1 root root  15784567 Sep  3 13:17 Ellie Goulding - Burn - YouTube.mp4
-rwxr-xr-x  1 root root    122791 Jun  9 16:50 enterprise.odt
drwxr-xr-x  3 root root     32768 Sep 26  2012 Family Slides
-rwxr-xr-x  1 root root   5045891 Jun  9 18:41 farthers day gift.odp
-rwxr-xr-x  1 root root   5045891 Jun  9 18:41 farthers day gift.pptx
-rwxr-xr-x  1 root root  35524720 Dec 27  2012 hall of fame.wav
-rwxr-xr-x  1 root root  34741504 Dec 27  2012 hand on heart.wav
-rwxr-xr-x  1 root root   3586089 Dec 13  2012 heart skips a beat.mpeg
-rwxr-xr-x  1 root root  32916352 Dec 27  2012 hey your beautiful.wav
-rwxr-xr-x  1 root root     17652 Jan 17  2013 hmv.odt
-rwxr-xr-x  1 root root     42118 Feb 28  2013 hooligans.odt
-rwxr-xr-x  1 root root     17531 Feb 14  2013 horse2 (copy).PPTX.odt
-rwxr-xr-x  1 root root    142851 Feb 14  2013 horse2.odt
-rwxr-xr-x  1 root root   1353753 Feb 10  2013 horsemeat2 (copy).PPTX.odp
-rwxr-xr-x  1 root root   1367509 Feb 10  2013 horsemeat2.odp
-rwxr-xr-x  1 root root     13793 May 12 11:33 IMG00346-20130511-2252.jpg
-rwxr-xr-x  1 root root     48654 Jun 14 20:02 IMG00364-20130614-1834.jpg
-rwxr-xr-x  1 root root   8835565 Jun 14 21:02 international night 2013 jocelin.3GP
drwxr-xr-x  2 root root      8192 Jul 31 16:00 james blunt
-rwxr-xr-x  1 root root  17926198 Sep  3 13:21 Lawson - Brokenhearted ft. B.O.B. - YouTube.mp4
-rwxr-xr-x  1 root root  13514775 Sep  3 13:19 Lawson - Juliet - YouTube.mp4
-rwxr-xr-x  1 root root  16122967 Sep  3 13:19 Lawson - Learn To Love Again - YouTube.mp4
-rwxr-xr-x  1 root root  13796004 Sep  3 13:20 Lawson - Standing In The Dark - YouTube.mp4
-rwxr-xr-x  1 root root  15178789 Sep  3 13:20 Lawson - When She Was Mine - YouTube.mp4
drwxr-xr-x  2 root root      8192 May 21  2012 LearningUnit01VideoTutorials
-rwxr-xr-x  1 root root  35103712 Dec 27  2012 live while were young.wav
drwxr-xr-x  2 root root      8192 Jun 10  2012 more advanced blender videos
-rwxr-xr-x  1 root root  17917185 Dec 30  2012 Mumford _ Sons - Little Lion Man.mp4
drwxr-xr-x  3 root root      8192 Dec  5  2012 New folder
-rwxr-xr-x  1 root root  14298142 Aug 23  2012 Noel Gallagher emotional Where did it all go wrong_ w_ lyric.mp4
-rwxr-xr-x  1 root root  32810512 Dec 27  2012 one of these days.wav
-rwxr-xr-x  1 root root    787236 Dec  3  2012 Organic of Life pres.pptx
drwxr-xr-x  2 root root      8192 Sep  9 15:32 Pendrive
-rwxr-xr-x  1 root root     18033 Jan 30  2009 Picture(101).jpg
-rwxr-xr-x  1 root root      9537 Oct  3  2009 Picture(140).jpg
-rwxr-xr-x  1 root root      8540 Jan 31  2009 Picture(144).jpg
-rwxr-xr-x  1 root root     12626 Jan 31  2009 Picture(157).jpg
-rwxr-xr-x  1 root root      8450 Feb  9  2009 Picture(20).jpg
-rwxr-xr-x  1 root root     10852 Oct  3  2009 Picture(23).jpg
-rwxr-xr-x  1 root root      7459 Oct  3  2009 Picture(50).jpg
-rwxr-xr-x  1 root root      6704 Oct  3  2009 Picture(51).jpg
-rwxr-xr-x  1 root root      9992 Oct  3  2009 Picture(95).jpg
drwxr-xr-x  2 root root      8192 Nov 28  2012 presentation project 2
-rwxr-xr-x  1 root root  14338197 Aug  4  2012 Queen - _Don_t Stop Me Now_.mp4
-rwxr-xr-x  1 root root     14799 Nov 15  2012 radio DJ.odt
-rwxr-xr-x  1 root root    624379 Dec  4  2012 ride 1.odp
-rwxr-xr-x  1 root root    623558 Dec  7  2012 ride 1.pptx
drwxr-xr-x  6 root root      8192 Nov 12  2012 saved website
-rwxr-xr-x  1 root root  39184432 Dec 27  2012 say nothing.wav
-rwxr-xr-x  1 root root     34525 Nov 29  2012 shark.odt
-rwxr-xr-x  1 root root 474409284 Sep  3 13:31 Sonic Adventure 2 Versus _ Episode 1 - YouTube.webm
-rwxr-xr-x  1 root root 293060242 Sep  3 13:47 Sonic Adventure 2 Versus _ Episode 2 - YouTube.flv
-rwxr-xr-x  1 root root      6296 Nov 22  2012 target.odt
-rwxr-xr-x  1 root root     18245 Nov 15  2012 tdj.odt
-rwxr-xr-x  1 root root  24201866 Sep  3 13:25 Tenacious D - Tribute - YouTube.mp4
-rwxr-xr-x  1 root root    180457 Feb 11  2013 tesco (copy).PPTX.odt
-rwxr-xr-x  1 root root    164031 Feb 11  2013 tesco.odt
-rwxr-xr-x  1 root root   8618793 Aug  9  2012 The party - The Young Ones - BBC comedy.mp4
-rwxr-xr-x  1 root root     22281 Jan 23  2013 the turtle and the apple.odt
-rwxr-xr-x  1 root root  18591282 Sep  3 13:22 The Wanted - Walks Like Rihanna - YouTube.mp4
-rwxr-xr-x  1 root root  40727344 Dec 25  2012 Track 13.wav
-rwxr-xr-x  1 root root  43589728 Dec 25  2012 Track 19.wav
-rwxr-xr-x  1 root root  38878672 Dec 25  2012 Track 1.wav
-rwxr-xr-x  1 root root  37072336 Dec 25  2012 Track 20.wav
-rwxr-xr-x  1 root root  35195440 Dec 25  2012 Track 2.wav
-rwxr-xr-x  1 root root  37643872 Dec 25  2012 Track 3.wav
-rwxr-xr-x  1 root root  32737600 Dec 27  2012 troublemaker ma.wav
-rwxr-xr-x  1 root root  32937520 Dec 25  2012 try.wav
-rwxr-xr-x  1 root root  40757920 Dec 27  2012 turn arownd.wav
-rwxr-xr-x  1 root root     21445 Nov 26  2012 Untitled par.odt
-rwxr-xr-x  1 root root  43686160 Dec 25  2012 vanity.wav
-rwxr-xr-x  1 root root   5100363 Sep 12  2012 VID 00054-20120906-2100.3GP
-rwxr-xr-x  1 root root  38683456 Dec 27  2012 whatchtower.wav
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo touch /mnt/empty
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo ls -l /mnt/empty
-rwxr-xr-x 1 root root 0 Sep 10 00:45 /mnt/empty
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo -s  # enter a superuser shell
root@ortermagic-Centurion-CPD-1303:~# echo "hello world" > /mnt/hello.txt
root@ortermagic-Centurion-CPD-1303:~# ls -l /mnt
total 1919408
-rwxr-xr-x  1 root root   3247976 Dec  2  2012 Adam Ant_s, New Single _Cool Zombie_ [Official Preview Trail.mp4
-rwxr-xr-x  1 root root 106660241 Jul  9  2012 amd-driver-installer-12-6-x86.x86_64.run
-rwxr-xr-x  1 root root      1050 Oct  6  2012 amd-driver-installer-12-9-x86.x86_64.run
-rwxr-xr-x  1 root root     87451 Jul 16 18:43 andy-murray-dog-medal.jpg
-rwxr-xr-x  1 root root    178166 Jul 16 18:38 andy murray.jpg
-rwxr-xr-x  1 root root     67687 Jul 16 18:54 Andy-Murray.jpg
-rwxr-xr-x  1 root root    155772 Jul 16 16:31 Andy-Murray-of-Great-Britain-holds-trophy-2038035.jpg
-rwxr-xr-x  1 root root     21618 Jun 19 19:38 arch.odt
-rwxr-xr-x  1 root root  50650432 Dec 27  2012 army of two.wav
-rwxr-xr-x  1 root root  47729248 Dec 27  2012 beneath your beautiful.wav
-rwxr-xr-x  1 root root    323184 Nov 30  2012 Bike Riding.pptx
-rwxr-xr-x  1 root root   1368151 Jan 21  2013 bikes.PPTX.odp
-rwxr-xr-x  1 root root     53777 Jul  4 12:40 bio adam.odt
-rwxr-xr-x  1 root root  53648743 Oct 18  2012 blender-2.64a-linux-glibc27-x86_64.tar.bz2
drwxr-xr-x  2 root root      8192 Nov 15  2012 canada pics
-rwxr-xr-x  1 root root      5579 Nov 29  2012 carl andrej.odt
-rwxr-xr-x  1 root root     30360 Jun 20 12:29 citylit.odt
drwxr-xr-x  4 root root      8192 Jul 17  2012 claires
drwxr-xr-x  2 root root      8192 May 18  2012 claires animation starts
drwxr-xr-x 14 root root      8192 Sep  8 18:28 claires blender tuts 1
-rwxr-xr-x  1 root root    563332 Jun 29  2012 claires.zip
drwxr-xr-x  3 root root      8192 Feb 26  2011 Conky-lua
-rwxr-xr-x  1 root root  36404368 Dec 27  2012 dear darling.wav
-rwxr-xr-x  1 root root  39144448 Dec 27  2012 dont wake me up.wav
-rwxr-xr-x  1 root root    462667 Feb  7  2009 DSC00110.JPG
-rwxr-xr-x  1 root root    145842 Feb  7  2009 DSC00117.JPG
-rwxr-xr-x  1 root root    546600 Feb  7  2009 DSC00118.JPG
-rwxr-xr-x  1 root root    125683 Feb 24  2009 DSC00145.JPG
-rwxr-xr-x  1 root root     25088 Nov 22  2012 dutch.doc
drwxr-xr-x  2 root root      8192 Apr  2 13:58 ed sheeran
-rwxr-xr-x  1 root root  15784567 Sep  3 13:17 Ellie Goulding - Burn - YouTube.mp4
-rwxr-xr-x  1 root root         0 Sep 10 00:45 empty
-rwxr-xr-x  1 root root    122791 Jun  9 16:50 enterprise.odt
drwxr-xr-x  3 root root     32768 Sep 26  2012 Family Slides
-rwxr-xr-x  1 root root   5045891 Jun  9 18:41 farthers day gift.odp
-rwxr-xr-x  1 root root   5045891 Jun  9 18:41 farthers day gift.pptx
-rwxr-xr-x  1 root root  35524720 Dec 27  2012 hall of fame.wav
-rwxr-xr-x  1 root root  34741504 Dec 27  2012 hand on heart.wav
-rwxr-xr-x  1 root root   3586089 Dec 13  2012 heart skips a beat.mpeg
-rwxr-xr-x  1 root root        12 Sep 10 00:46 hello.txt
-rwxr-xr-x  1 root root  32916352 Dec 27  2012 hey your beautiful.wav
-rwxr-xr-x  1 root root     17652 Jan 17  2013 hmv.odt
-rwxr-xr-x  1 root root     42118 Feb 28  2013 hooligans.odt
-rwxr-xr-x  1 root root     17531 Feb 14  2013 horse2 (copy).PPTX.odt
-rwxr-xr-x  1 root root    142851 Feb 14  2013 horse2.odt
-rwxr-xr-x  1 root root   1353753 Feb 10  2013 horsemeat2 (copy).PPTX.odp
-rwxr-xr-x  1 root root   1367509 Feb 10  2013 horsemeat2.odp
-rwxr-xr-x  1 root root     13793 May 12 11:33 IMG00346-20130511-2252.jpg
-rwxr-xr-x  1 root root     48654 Jun 14 20:02 IMG00364-20130614-1834.jpg
-rwxr-xr-x  1 root root   8835565 Jun 14 21:02 international night 2013 jocelin.3GP
drwxr-xr-x  2 root root      8192 Jul 31 16:00 james blunt
-rwxr-xr-x  1 root root  17926198 Sep  3 13:21 Lawson - Brokenhearted ft. B.O.B. - YouTube.mp4
-rwxr-xr-x  1 root root  13514775 Sep  3 13:19 Lawson - Juliet - YouTube.mp4
-rwxr-xr-x  1 root root  16122967 Sep  3 13:19 Lawson - Learn To Love Again - YouTube.mp4
-rwxr-xr-x  1 root root  13796004 Sep  3 13:20 Lawson - Standing In The Dark - YouTube.mp4
-rwxr-xr-x  1 root root  15178789 Sep  3 13:20 Lawson - When She Was Mine - YouTube.mp4
drwxr-xr-x  2 root root      8192 May 21  2012 LearningUnit01VideoTutorials
-rwxr-xr-x  1 root root  35103712 Dec 27  2012 live while were young.wav
drwxr-xr-x  2 root root      8192 Jun 10  2012 more advanced blender videos
-rwxr-xr-x  1 root root  17917185 Dec 30  2012 Mumford _ Sons - Little Lion Man.mp4
drwxr-xr-x  3 root root      8192 Dec  5  2012 New folder
-rwxr-xr-x  1 root root  14298142 Aug 23  2012 Noel Gallagher emotional Where did it all go wrong_ w_ lyric.mp4
-rwxr-xr-x  1 root root  32810512 Dec 27  2012 one of these days.wav
-rwxr-xr-x  1 root root    787236 Dec  3  2012 Organic of Life pres.pptx
drwxr-xr-x  2 root root      8192 Sep  9 15:32 Pendrive
-rwxr-xr-x  1 root root     18033 Jan 30  2009 Picture(101).jpg
-rwxr-xr-x  1 root root      9537 Oct  3  2009 Picture(140).jpg
-rwxr-xr-x  1 root root      8540 Jan 31  2009 Picture(144).jpg
-rwxr-xr-x  1 root root     12626 Jan 31  2009 Picture(157).jpg
-rwxr-xr-x  1 root root      8450 Feb  9  2009 Picture(20).jpg
-rwxr-xr-x  1 root root     10852 Oct  3  2009 Picture(23).jpg
-rwxr-xr-x  1 root root      7459 Oct  3  2009 Picture(50).jpg
-rwxr-xr-x  1 root root      6704 Oct  3  2009 Picture(51).jpg
-rwxr-xr-x  1 root root      9992 Oct  3  2009 Picture(95).jpg
drwxr-xr-x  2 root root      8192 Nov 28  2012 presentation project 2
-rwxr-xr-x  1 root root  14338197 Aug  4  2012 Queen - _Don_t Stop Me Now_.mp4
-rwxr-xr-x  1 root root     14799 Nov 15  2012 radio DJ.odt
-rwxr-xr-x  1 root root    624379 Dec  4  2012 ride 1.odp
-rwxr-xr-x  1 root root    623558 Dec  7  2012 ride 1.pptx
drwxr-xr-x  6 root root      8192 Nov 12  2012 saved website
-rwxr-xr-x  1 root root  39184432 Dec 27  2012 say nothing.wav
-rwxr-xr-x  1 root root     34525 Nov 29  2012 shark.odt
-rwxr-xr-x  1 root root 474409284 Sep  3 13:31 Sonic Adventure 2 Versus _ Episode 1 - YouTube.webm
-rwxr-xr-x  1 root root 293060242 Sep  3 13:47 Sonic Adventure 2 Versus _ Episode 2 - YouTube.flv
-rwxr-xr-x  1 root root      6296 Nov 22  2012 target.odt
-rwxr-xr-x  1 root root     18245 Nov 15  2012 tdj.odt
-rwxr-xr-x  1 root root  24201866 Sep  3 13:25 Tenacious D - Tribute - YouTube.mp4
-rwxr-xr-x  1 root root    180457 Feb 11  2013 tesco (copy).PPTX.odt
-rwxr-xr-x  1 root root    164031 Feb 11  2013 tesco.odt
-rwxr-xr-x  1 root root   8618793 Aug  9  2012 The party - The Young Ones - BBC comedy.mp4
-rwxr-xr-x  1 root root     22281 Jan 23  2013 the turtle and the apple.odt
-rwxr-xr-x  1 root root  18591282 Sep  3 13:22 The Wanted - Walks Like Rihanna - YouTube.mp4
-rwxr-xr-x  1 root root  40727344 Dec 25  2012 Track 13.wav
-rwxr-xr-x  1 root root  43589728 Dec 25  2012 Track 19.wav
-rwxr-xr-x  1 root root  38878672 Dec 25  2012 Track 1.wav
-rwxr-xr-x  1 root root  37072336 Dec 25  2012 Track 20.wav
-rwxr-xr-x  1 root root  35195440 Dec 25  2012 Track 2.wav
-rwxr-xr-x  1 root root  37643872 Dec 25  2012 Track 3.wav
-rwxr-xr-x  1 root root  32737600 Dec 27  2012 troublemaker ma.wav
-rwxr-xr-x  1 root root  32937520 Dec 25  2012 try.wav
-rwxr-xr-x  1 root root  40757920 Dec 27  2012 turn arownd.wav
-rwxr-xr-x  1 root root     21445 Nov 26  2012 Untitled par.odt
-rwxr-xr-x  1 root root  43686160 Dec 25  2012 vanity.wav
-rwxr-xr-x  1 root root   5100363 Sep 12  2012 VID 00054-20120906-2100.3GP
-rwxr-xr-x  1 root root  38683456 Dec 27  2012 whatchtower.wav
root@ortermagic-Centurion-CPD-1303:~# cat /mnt/hello.txt
hello world
root@ortermagic-Centurion-CPD-1303:~# exit   # exit from the superuser shell (important to remember this command)df
exit
ortermagic@ortermagic-Centurion-CPD-1303:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda6      243191836 8928196 221910224   4% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1981288       4   1981284   1% /dev
tmpfs             404856    1152    403704   1% /run
none                5120       0      5120   0% /run/lock
none             2024264     152   2024112   1% /run/shm
none              102400      32    102368   1% /run/user
/dev/sdb1       15581128 7563744   8017384  49% /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo umount /mnt
ortermagic@ortermagic-Centurion-CPD-1303:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda6      243191836 8928224 221910196   4% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1981288       4   1981284   1% /dev
tmpfs             404856    1152    403704   1% /run
none                5120       0      5120   0% /run/lock
none             2024264     152   2024112   1% /run/shm
none              102400      32    102368   1% /run/user
ortermagic@ortermagic-Centurion-CPD-1303:~$ sudo ls -l /mnt
total 0
ortermagic@ortermagic-Centurion-CPD-1303:~$ 


```

I'm not sure what it all means, I will get back to it tomorrow thanks.

---

### Post by sudodus on 2013-09-09
> **ortermagic said:**
> sudodus I have followed your prescription as follows..



I'm not sure what it all means, I will get back to it tomorrow thanks.

Please use code tags instead of quote tags (mark the text and click the **#** icon above this editing window instead)

```
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo mount /dev/sdb1 /mnt*[/COLOR]
[COLOR=#000000]*[sudo] password for ortermagic: *[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*df*[/COLOR]
[COLOR=#000000]*Filesystem 1K-blocks Used Available Use% Mounted on*[/COLOR]
[COLOR=#000000]*/dev/sda6 243191836 8928344 221910076 4% /*[/COLOR]
[COLOR=#000000]*none 4 0 4 0% /sys/fs/cgroup*[/COLOR]
[COLOR=#000000]*udev 1981288 4 1981284 1% /dev*[/COLOR]
[COLOR=#000000]*tmpfs 404856 1160 403696 1% /run*[/COLOR]
[COLOR=#000000]*none 5120 0 5120 0% /run/lock*[/COLOR]
[COLOR=#000000]*none 2024264 152 2024112 1% /run/shm*[/COLOR]
[COLOR=#000000]*none 102400 36 102364 1% /run/user*[/COLOR]
[COLOR=#ff0000]*/dev/sdb1 15581128 7563736 8017392 49% /mnt                  # the pendrive is mounted :-)*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*cat /etc/mtab*[/COLOR]
[COLOR=#000000]*/dev/sda6 / ext2 rw,errors=remount-ro 0 0*[/COLOR]
[COLOR=#000000]*proc /proc proc rw,noexec,nosuid,nodev 0 0*[/COLOR]
[COLOR=#000000]*sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0*[/COLOR]
[COLOR=#000000]*none /sys/fs/cgroup tmpfs rw 0 0*[/COLOR]
[COLOR=#000000]*none /sys/fs/fuse/connections fusectl rw 0 0*[/COLOR]
[COLOR=#000000]*none /sys/kernel/debug debugfs rw 0 0*[/COLOR]
[COLOR=#000000]*none /sys/kernel/security securityfs rw 0 0*[/COLOR]
[COLOR=#000000]*udev /dev devtmpfs rw,mode=0755 0 0*[/COLOR]
[COLOR=#000000]*devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0*[/COLOR]
[COLOR=#000000]*tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0*[/COLOR]
[COLOR=#000000]*none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0*[/COLOR]
[COLOR=#000000]*none /run/shm tmpfs rw,nosuid,nodev 0 0*[/COLOR]
[COLOR=#000000]*none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0*[/COLOR]
[COLOR=#000000]*systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0*[/COLOR]
[COLOR=#000000]*gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=ortermagic 0 0*[/COLOR]
[COLOR=#ff0000]*/dev/sdb1 /mnt vfat rw 0 0*[/COLOR]                                             [COLOR=#FF0000]*# confirmed, the pendrive is mounted and it has a fat file system with read and write permissions*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo ls -l /*[/COLOR]
[COLOR=#000000]*total 136*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 4096 Sep 7 10:58 bin*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 4096 Sep 7 10:59 boot*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 4096 Jul 17 19:13 cdrom*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 17 root root 4460 Sep 10 00:37 dev*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 146 root root 8192 Sep 10 00:43 etc*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 4096 Jul 17 19:13 home*[/COLOR]
[COLOR=#000000]*lrwxrwxrwx 1 root root 32 Jul 28 02:52 initrd.img -> boot/initrd.img-3.10.0-6-generic*[/COLOR]
[COLOR=#000000]*lrwxrwxrwx 1 root root 33 Jul 28 02:51 initrd.img.old -> /boot/initrd.img-3.10.0-6-generic*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 26 root root 4096 Sep 8 19:58 lib*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 4096 Aug 2 09:05 lib32*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 4096 Aug 2 09:05 lib64*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 49152 Jul 17 19:10 lost+found*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 11 root root 4096 Sep 8 16:46 media*[/COLOR]
[COLOR=#ff0000]*drwxr-xr-x 19 root root 16384 Jan 1 1970 mnt                 # checking the permissions of /mnt*
[/COLOR][COLOR=#000000]*drwxr-xr-x 2 root root 4096 Jul 17 08:31 opt*[/COLOR]
[COLOR=#000000]*dr-xr-xr-x 206 root root 0 Sep 10 00:21 proc*[/COLOR]
[COLOR=#000000]*drwx------ 7 root root 4096 Aug 18 18:36 root*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 24 root root 760 Sep 10 00:29 run*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Sep 7 10:57 sbin*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 4096 Jul 17 08:31 srv*[/COLOR]
[COLOR=#000000]*dr-xr-xr-x 13 root root 0 Sep 10 00:22 sys*[/COLOR]
[COLOR=#000000]*drwxrwxrwt 7 root root 4096 Sep 10 00:44 tmp*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 12 root root 4096 Jul 17 19:30 usr*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 13 root root 4096 Jul 17 08:38 var*[/COLOR]
[COLOR=#000000]*lrwxrwxrwx 1 root root 29 Jul 28 02:52 vmlinuz -> boot/vmlinuz-3.10.0-6-generic*[/COLOR]
[COLOR=#000000]*lrwxrwxrwx 1 root root 29 Jul 28 02:51 vmlinuz.old -> boot/vmlinuz-3.10.0-6-generic*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo ls -l /mnt*[/COLOR]
[COLOR=#ff0000]*total 1919400                   # here we go, there are a lot of files, that you can read in the pendrive*
[/COLOR][COLOR=#000000]*-rwxr-xr-x 1 root root 3247976 Dec 2 2012 Adam Ant_s, New Single _Cool Zombie_ [Official Preview Trail.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 106660241 Jul 9 2012 amd-driver-installer-12-6-x86.x86_64.run*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1050 Oct 6 2012 amd-driver-installer-12-9-x86.x86_64.run*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 87451 Jul 16 18:43 andy-murray-dog-medal.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 178166 Jul 16 18:38 andy murray.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 67687 Jul 16 18:54 Andy-Murray.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 155772 Jul 16 16:31 Andy-Murray-of-Great-Britain-holds-trophy-2038035.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 21618 Jun 19 19:38 arch.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 50650432 Dec 27 2012 army of two.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 47729248 Dec 27 2012 beneath your beautiful.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 323184 Nov 30 2012 Bike Riding.pptx*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1368151 Jan 21 2013 bikes.PPTX.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 53777 Jul 4 12:40 bio adam.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 53648743 Oct 18 2012 blender-2.64a-linux-glibc27-x86_64.tar.bz2*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Nov 15 2012 canada pics*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5579 Nov 29 2012 carl andrej.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 30360 Jun 20 12:29 citylit.odt*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 4 root root 8192 Jul 17 2012 claires*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 May 18 2012 claires animation starts*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 14 root root 8192 Sep 8 18:28 claires blender tuts 1*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 563332 Jun 29 2012 claires.zip*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 8192 Feb 26 2011 Conky-lua*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 36404368 Dec 27 2012 dear darling.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 39144448 Dec 27 2012 dont wake me up.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 462667 Feb 7 2009 DSC00110.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 145842 Feb 7 2009 DSC00117.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 546600 Feb 7 2009 DSC00118.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 125683 Feb 24 2009 DSC00145.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 25088 Nov 22 2012 dutch.doc*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Apr 2 13:58 ed sheeran*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 15784567 Sep 3 13:17 Ellie Goulding - Burn - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 122791 Jun 9 16:50 enterprise.odt*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 32768 Sep 26 2012 Family Slides*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5045891 Jun 9 18:41 farthers day gift.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5045891 Jun 9 18:41 farthers day gift.pptx*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35524720 Dec 27 2012 hall of fame.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 34741504 Dec 27 2012 hand on heart.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 3586089 Dec 13 2012 heart skips a beat.mpeg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32916352 Dec 27 2012 hey your beautiful.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17652 Jan 17 2013 hmv.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 42118 Feb 28 2013 hooligans.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17531 Feb 14 2013 horse2 (copy).PPTX.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 142851 Feb 14 2013 horse2.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1353753 Feb 10 2013 horsemeat2 (copy).PPTX.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1367509 Feb 10 2013 horsemeat2.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13793 May 12 11:33 IMG00346-20130511-2252.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 48654 Jun 14 20:02 IMG00364-20130614-1834.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8835565 Jun 14 21:02 international night 2013 jocelin.3GP*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Jul 31 16:00 james blunt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17926198 Sep 3 13:21 Lawson - Brokenhearted ft. B.O.B. - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13514775 Sep 3 13:19 Lawson - Juliet - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 16122967 Sep 3 13:19 Lawson - Learn To Love Again - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13796004 Sep 3 13:20 Lawson - Standing In The Dark - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 15178789 Sep 3 13:20 Lawson - When She Was Mine - YouTube.mp4*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 May 21 2012 LearningUnit01VideoTutorials*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35103712 Dec 27 2012 live while were young.wav*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Jun 10 2012 more advanced blender videos*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17917185 Dec 30 2012 Mumford _ Sons - Little Lion Man.mp4*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 8192 Dec 5 2012 New folder*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14298142 Aug 23 2012 Noel Gallagher emotional Where did it all go wrong_ w_ lyric.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32810512 Dec 27 2012 one of these days.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 787236 Dec 3 2012 Organic of Life pres.pptx*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Sep 9 15:32 Pendrive*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18033 Jan 30 2009 Picture(101).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 9537 Oct 3 2009 Picture(140).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8540 Jan 31 2009 Picture(144).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 12626 Jan 31 2009 Picture(157).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8450 Feb 9 2009 Picture(20).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 10852 Oct 3 2009 Picture(23).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 7459 Oct 3 2009 Picture(50).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 6704 Oct 3 2009 Picture(51).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 9992 Oct 3 2009 Picture(95).jpg*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Nov 28 2012 presentation project 2*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14338197 Aug 4 2012 Queen - _Don_t Stop Me Now_.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14799 Nov 15 2012 radio DJ.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 624379 Dec 4 2012 ride 1.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 623558 Dec 7 2012 ride 1.pptx*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 6 root root 8192 Nov 12 2012 saved website*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 39184432 Dec 27 2012 say nothing.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 34525 Nov 29 2012 shark.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 474409284 Sep 3 13:31 Sonic Adventure 2 Versus _ Episode 1 - YouTube.webm*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 293060242 Sep 3 13:47 Sonic Adventure 2 Versus _ Episode 2 - YouTube.flv*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 6296 Nov 22 2012 target.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18245 Nov 15 2012 tdj.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 24201866 Sep 3 13:25 Tenacious D - Tribute - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 180457 Feb 11 2013 tesco (copy).PPTX.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 164031 Feb 11 2013 tesco.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8618793 Aug 9 2012 The party - The Young Ones - BBC comedy.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 22281 Jan 23 2013 the turtle and the apple.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18591282 Sep 3 13:22 The Wanted - Walks Like Rihanna - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 40727344 Dec 25 2012 Track 13.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 43589728 Dec 25 2012 Track 19.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 38878672 Dec 25 2012 Track 1.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 37072336 Dec 25 2012 Track 20.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35195440 Dec 25 2012 Track 2.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 37643872 Dec 25 2012 Track 3.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32737600 Dec 27 2012 troublemaker ma.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32937520 Dec 25 2012 try.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 40757920 Dec 27 2012 turn arownd.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 21445 Nov 26 2012 Untitled par.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 43686160 Dec 25 2012 vanity.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5100363 Sep 12 2012 VID 00054-20120906-2100.3GP*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 38683456 Dec 27 2012 whatchtower.wav*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo touch /mnt/empty*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo ls -l /mnt/empty*[/COLOR]
[COLOR=#ff0000]*-rwxr-xr-x 1 root root 0 Sep 10 00:45 /mnt/empty                                      # yes, it is there :-)*
[/COLOR][COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo -s # enter a superuser shell*[/COLOR]
[COLOR=#000000]*root@ortermagic-Centurion-CPD-1303:~# *[/COLOR][COLOR=#0000cd]*echo "hello world" > /mnt/hello.txt*[/COLOR]
[COLOR=#000000]*root@ortermagic-Centurion-CPD-1303:~#*[/COLOR][COLOR=#0000cd]* ls -l /mnt*[/COLOR]
[COLOR=#000000]*total 1919408*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 3247976 Dec 2 2012 Adam Ant_s, New Single _Cool Zombie_ [Official Preview Trail.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 106660241 Jul 9 2012 amd-driver-installer-12-6-x86.x86_64.run*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1050 Oct 6 2012 amd-driver-installer-12-9-x86.x86_64.run*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 87451 Jul 16 18:43 andy-murray-dog-medal.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 178166 Jul 16 18:38 andy murray.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 67687 Jul 16 18:54 Andy-Murray.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 155772 Jul 16 16:31 Andy-Murray-of-Great-Britain-holds-trophy-2038035.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 21618 Jun 19 19:38 arch.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 50650432 Dec 27 2012 army of two.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 47729248 Dec 27 2012 beneath your beautiful.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 323184 Nov 30 2012 Bike Riding.pptx*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1368151 Jan 21 2013 bikes.PPTX.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 53777 Jul 4 12:40 bio adam.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 53648743 Oct 18 2012 blender-2.64a-linux-glibc27-x86_64.tar.bz2*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Nov 15 2012 canada pics*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5579 Nov 29 2012 carl andrej.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 30360 Jun 20 12:29 citylit.odt*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 4 root root 8192 Jul 17 2012 claires*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 May 18 2012 claires animation starts*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 14 root root 8192 Sep 8 18:28 claires blender tuts 1*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 563332 Jun 29 2012 claires.zip*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 8192 Feb 26 2011 Conky-lua*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 36404368 Dec 27 2012 dear darling.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 39144448 Dec 27 2012 dont wake me up.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 462667 Feb 7 2009 DSC00110.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 145842 Feb 7 2009 DSC00117.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 546600 Feb 7 2009 DSC00118.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 125683 Feb 24 2009 DSC00145.JPG*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 25088 Nov 22 2012 dutch.doc*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Apr 2 13:58 ed sheeran*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 15784567 Sep 3 13:17 Ellie Goulding - Burn - YouTube.mp4*[/COLOR]
[COLOR=#ff0000]*-rwxr-xr-x 1 root root 0 Sep 10 00:45 empty                                                        # yes it is there among your 'real' files*
[/COLOR][COLOR=#000000]*-rwxr-xr-x 1 root root 122791 Jun 9 16:50 enterprise.odt*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 32768 Sep 26 2012 Family Slides*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5045891 Jun 9 18:41 farthers day gift.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5045891 Jun 9 18:41 farthers day gift.pptx*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35524720 Dec 27 2012 hall of fame.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 34741504 Dec 27 2012 hand on heart.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 3586089 Dec 13 2012 heart skips a beat.mpeg*[/COLOR]
[COLOR=#ff0000]*-rwxr-xr-x 1 root root 12 Sep 10 00:46 hello.txt*[/COLOR][COLOR=#FF0000]*                                                        # yes it is there among your 'real' files*[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#000000]*-rwxr-xr-x 1 root root 32916352 Dec 27 2012 hey your beautiful.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17652 Jan 17 2013 hmv.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 42118 Feb 28 2013 hooligans.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17531 Feb 14 2013 horse2 (copy).PPTX.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 142851 Feb 14 2013 horse2.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1353753 Feb 10 2013 horsemeat2 (copy).PPTX.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 1367509 Feb 10 2013 horsemeat2.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13793 May 12 11:33 IMG00346-20130511-2252.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 48654 Jun 14 20:02 IMG00364-20130614-1834.jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8835565 Jun 14 21:02 international night 2013 jocelin.3GP*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Jul 31 16:00 james blunt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17926198 Sep 3 13:21 Lawson - Brokenhearted ft. B.O.B. - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13514775 Sep 3 13:19 Lawson - Juliet - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 16122967 Sep 3 13:19 Lawson - Learn To Love Again - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 13796004 Sep 3 13:20 Lawson - Standing In The Dark - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 15178789 Sep 3 13:20 Lawson - When She Was Mine - YouTube.mp4*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 May 21 2012 LearningUnit01VideoTutorials*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35103712 Dec 27 2012 live while were young.wav*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Jun 10 2012 more advanced blender videos*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 17917185 Dec 30 2012 Mumford _ Sons - Little Lion Man.mp4*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 3 root root 8192 Dec 5 2012 New folder*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14298142 Aug 23 2012 Noel Gallagher emotional Where did it all go wrong_ w_ lyric.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32810512 Dec 27 2012 one of these days.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 787236 Dec 3 2012 Organic of Life pres.pptx*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Sep 9 15:32 Pendrive*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18033 Jan 30 2009 Picture(101).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 9537 Oct 3 2009 Picture(140).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8540 Jan 31 2009 Picture(144).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 12626 Jan 31 2009 Picture(157).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8450 Feb 9 2009 Picture(20).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 10852 Oct 3 2009 Picture(23).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 7459 Oct 3 2009 Picture(50).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 6704 Oct 3 2009 Picture(51).jpg*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 9992 Oct 3 2009 Picture(95).jpg*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 2 root root 8192 Nov 28 2012 presentation project 2*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14338197 Aug 4 2012 Queen - _Don_t Stop Me Now_.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 14799 Nov 15 2012 radio DJ.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 624379 Dec 4 2012 ride 1.odp*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 623558 Dec 7 2012 ride 1.pptx*[/COLOR]
[COLOR=#000000]*drwxr-xr-x 6 root root 8192 Nov 12 2012 saved website*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 39184432 Dec 27 2012 say nothing.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 34525 Nov 29 2012 shark.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 474409284 Sep 3 13:31 Sonic Adventure 2 Versus _ Episode 1 - YouTube.webm*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 293060242 Sep 3 13:47 Sonic Adventure 2 Versus _ Episode 2 - YouTube.flv*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 6296 Nov 22 2012 target.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18245 Nov 15 2012 tdj.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 24201866 Sep 3 13:25 Tenacious D - Tribute - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 180457 Feb 11 2013 tesco (copy).PPTX.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 164031 Feb 11 2013 tesco.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 8618793 Aug 9 2012 The party - The Young Ones - BBC comedy.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 22281 Jan 23 2013 the turtle and the apple.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 18591282 Sep 3 13:22 The Wanted - Walks Like Rihanna - YouTube.mp4*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 40727344 Dec 25 2012 Track 13.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 43589728 Dec 25 2012 Track 19.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 38878672 Dec 25 2012 Track 1.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 37072336 Dec 25 2012 Track 20.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 35195440 Dec 25 2012 Track 2.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 37643872 Dec 25 2012 Track 3.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32737600 Dec 27 2012 troublemaker ma.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 32937520 Dec 25 2012 try.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 40757920 Dec 27 2012 turn arownd.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 21445 Nov 26 2012 Untitled par.odt*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 43686160 Dec 25 2012 vanity.wav*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 5100363 Sep 12 2012 VID 00054-20120906-2100.3GP*[/COLOR]
[COLOR=#000000]*-rwxr-xr-x 1 root root 38683456 Dec 27 2012 whatchtower.wav*[/COLOR]
[COLOR=#000000]*root@ortermagic-Centurion-CPD-1303:~# *[/COLOR][COLOR=#0000cd]*cat /mnt/hello.txt*[/COLOR]
[COLOR=#ff0000]*hello world*[/COLOR][COLOR=#FF0000]*                                                                                                     # yes it is there and you can read its content :-)*[/COLOR]
[COLOR=#000000]*root@ortermagic-Centurion-CPD-1303:~# *[/COLOR][COLOR=#0000cd]*exit*[/COLOR][COLOR=#000000]* # exit from the superuser shell (important to remember this command)df*[/COLOR]
[COLOR=#000000]*exit*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*df*[/COLOR]
[COLOR=#000000]*Filesystem 1K-blocks Used Available Use% Mounted on*[/COLOR]
[COLOR=#000000]*/dev/sda6 243191836 8928196 221910224 4% /*[/COLOR]
[COLOR=#000000]*none 4 0 4 0% /sys/fs/cgroup*[/COLOR]
[COLOR=#000000]*udev 1981288 4 1981284 1% /dev*[/COLOR]
[COLOR=#000000]*tmpfs 404856 1152 403704 1% /run*[/COLOR]
[COLOR=#000000]*none 5120 0 5120 0% /run/lock*[/COLOR]
[COLOR=#000000]*none 2024264 152 2024112 1% /run/shm*[/COLOR]
[COLOR=#000000]*none 102400 32 102368 1% /run/user*[/COLOR]
[COLOR=#ff0000]*/dev/sdb1 15581128 7563744 8017384 49% /mnt                          # the pendrive is still mounted*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo umount /mnt*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*df*[/COLOR]
[COLOR=#000000]*Filesystem 1K-blocks Used Available Use% Mounted on*[/COLOR]
[COLOR=#000000]*/dev/sda6 243191836 8928224 221910196 4% /*[/COLOR]
[COLOR=#000000]*none 4 0 4 0% /sys/fs/cgroup*[/COLOR]
[COLOR=#000000]*udev 1981288 4 1981284 1% /dev*[/COLOR]
[COLOR=#000000]*tmpfs 404856 1152 403704 1% /run*[/COLOR]
[COLOR=#000000]*none 5120 0 5120 0% /run/lock*[/COLOR]
[COLOR=#000000]*none 2024264 152 2024112 1% /run/shm*[/COLOR]
[COLOR=#000000][I]none 102400 32 102368 1% /run/user
[/I][/COLOR][COLOR=#FF0000]*                                                        # the pendrive is no longer mounted (this is correct after unmounting)*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR][COLOR=#0000cd]*sudo ls -l /mnt*[/COLOR]
[COLOR=#ff0000]*total 0                                               # nothing is found *[/COLOR][COLOR=#FF0000]*(this is correct after unmounting)*[/COLOR]
[COLOR=#000000]*ortermagic@ortermagic-Centurion-CPD-1303:~$ *[/COLOR]
```

You ***[COLOR=#008000]can[/COLOR]*** mount and read/write from/to the pendrive this way. Do you want to find a way to do it also without using sudo (superuser privileges)?

---

### Post by ortermagic on 2013-09-10
Thank you ```
is this how you implement code tags
``` just checking

---

### Post by ortermagic on 2013-09-10
Oh my,eureka!
 I did not click the advanced button.
advanced applied to me? *sheepishgrin*. 
Now i have a range of editing options that I was'nt aware of.
Great.

---

### Post by ortermagic on 2013-09-10
> You ***[COLOR=#008000]can[/COLOR]*** mount and read/write  from/to the pendrive this way. Do you want to find a way to do it also  without using sudo (superuser privileges)?

Not really sudodus, as i am learning to use the terminal. 
If there is another way that you know of I would be interested in trying.
I still have the pen-drive problem.
It is only showing up on the terminal, and the media file is empty.

---

### Post by sudodus on 2013-09-10
Yes, the ***/media*** directory is empty, because the pendrive is mounted to another directory, ***/mnt***. Look at the /mnt directory with the file browser (instead of the /media directory).

You can run the file browser as superuser, but it is not recommended, because it is too easy to destroy a lot. Instead, when you feel more experienced, you can 

- create a directory and change its permissions (for mounting the pendrive) 
- create a label on the pendrive (for easy identification)
- and try until you can mount the pendrive with the file browser (instead of using ***sudo mount*** ...)

---

### Post by ortermagic on 2013-09-12
Dear sudodus thank you for your efforts to help me, I am posting to confess that I made a stupid error.
> Yes, the ***/media*** directory is empty, because the pendrive is mounted to another directory, ***/mnt***. Look at the /mnt directory with the file browser (instead of the /media directory).

When I was looking into the file system for the file I was mistakenly looking in the media directory of my 12.10 install.
I realise now that when I open up 13.10 there are two sets of directories one with 240 apx gb, and another called computer, I was looking in the 240gb partition when I should have been looking in the one labeled computer. Hopefully I will be able to resolve the issue over the next few days using your advice with clearer eyesight.

---

### Post by sudodus on 2013-09-12
Good luck :-)

And when you are happy with a solution, please mark the thread as SOLVED according to this link
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ortermagic on 2013-09-12
Thank you, I found the clicky now.

---

