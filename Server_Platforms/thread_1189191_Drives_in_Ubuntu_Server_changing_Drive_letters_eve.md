---
title: "Drives in Ubuntu Server changing Drive letters every boot"
date: 2009-06-16
forum: Server Platforms
---

### Post by pederjohn on 2009-06-16
Well now i'm having a problem again.

Seems everytime i boot the drive letters keep changing.

I have 6 drives in the server 2 are EXT3. 4 are NTFS.

Here is what it does:
Drive Letter : Size of Drive : Location of Drive : Filesystem : Connector type

First Round (New)
/dev/sdc : 120GB : On-Board (extra) : NTFS : IDE
/dev/sda : 200gb : PCI SataCard : NTFS : Sata
/dev/sdb : 1TB : PCI Sata Card : ext3: SATA
/dev/sdd : 80GB : On-Board : ext3 : IDE
/dev/sde : 80GB : On-Board : NTFS : IDE
/dev/sdf : 250GB : On-Board : NTFS : IDE

Second (Origignal)
/dev/sda : 200gb : PCI SataCard : NTFS : Sata
/dev/sdb : 1TB : PCI Sata Card : ext3: SATA
/dev/sdc : 120GB : On-Board (extra) : NTFS : IDE
/dev/sdd : 80GB : On-Board : ext3 : IDE
/dev/sde : 80GB : On-Board : NTFS : IDE
/dev/sdf : 250GB : On-Board : NTFS : IDE

And it switches at random between the two... and my drives don't load properly if they are different places... can anyone tell me why this happens?

Thanx
Peder

---

### Post by grantemsley on 2009-06-16
Some motherboard do this depending on what drives are connected, whether they are SATA or IDE, and sometimes depending on what order they spin up in.

The best thing to do is make sure you specify the drive by UUID in fstab.

---

### Post by twkcs on 2009-06-16
i have exactly the same problem, but i am still using ubuntu 8.04 on a 
older MSI Mainboard Socket 478 with 10 drives connected
4x internal IDE
4x on a PCI-IDE-card
2x SCSI (systemdrive is a old IBM DCAS 4,3gb from 1997)
every boot the drives get different names, so if you dont use UUID in your drives get mounted in the wrong folders
to prevent that i use UUID to mount them, so things like wrong paths never happen again.
"G" for UUID - its pretty simple

kcs

---

### Post by TwiceOver on 2009-06-16
I know it isn't mentioned, but is there any chance you have a usb disk of some kind hanging off the machine?  

I had this same problem when usb disks are attached.

---

### Post by ian dobson on 2009-06-16
Hi,

Maybe you could blacklist one of the controllers then "manually" modprobe it after the boot controller is loaded. Maybe in rc.local.

It's abit of a nasty hack but I've solved swapping hd controllers doing this.

Regards
Ian Dobson

---

### Post by pederjohn on 2009-06-16
okay... but i have no gui so i guess i have to type it in all?

I just wish the power would stop going out... this server works perfectly and it has for QUITE a while but all of a sudden its doing this

---

### Post by grantemsley on 2009-06-17
Connect via SSH from a system with a GUI (use putty if on windows) then you can copy and paste the UUIDs...they are a pain to have to type out, and even more of a pain to realize hours later that a typo is preventing your system from working.

---

### Post by cariboo on 2009-06-17
Use uuid instead of device label when mounting the drives in fstab. I have an MSI motherboard that does the same thing by using uuid you don't have to worry about device labels changing every time you reboot, to find the uuid of your hard drives, at the prompt type:

```
blkid
```

if running Jaunty you have to use sudo eg:

```
sudo blkid
[sudo] password for jim: 
/dev/sda1: UUID="20599368-31a7-4f01-8397-fd7e7126dd29" TYPE="ext4" 
/dev/sda2: UUID="7c109a7f-b7fd-402d-aec5-0ee7dd30d37a" TYPE="ext4" 
/dev/sda3: UUID="bc7912f5-a427-429d-98cd-7b97312c294d" TYPE="swap" 
/dev/sda4: UUID="7911a1c9-3c28-4a63-80c7-9cb6607b81eb" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap
```

---

