---
title: "&quot;one or more disks are failing&quot;"
date: 2009-11-21
forum: System76 Support
---

### Post by 982000971 on 2009-11-21
Upgraded to 9.10 today, and immediately upon reboot got this warning: "one or more disks are failing"

Checked it out with Palimpsest Disk Utility which points out "Reallocated Sector Count" and "Airflow Temperature". I can provide more details upon request, just not sure how to print these errors to a txt file.

Obviously this sounds bad. Is it? What are my options? (Details in signature.)

---

### Post by thomasaaron on 2009-11-23
How many bad sectors is it reporting?

Try running fsck from a live CD and see how many bad sectors it reports. Here are instructions for doing so...

> To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.




---

### Post by 982000971 on 2009-11-24
according to palimpsest

REALLOCATED SECTOR COUNT:
Assessment - Warning
Value - Normalized: 99, Worst: 99, Threshold: 36, Value: 59 Sectors

AIRFLOW TEMPERATURE:
Assessment - Failed in the past
Value - Normalized: 51, Worst: 34, Threshold: 45, Value: 120* F

...trying live cd now...

---

### Post by 982000971 on 2009-11-25
Okay so when I run gparted from live cd I get a popup that reads:

```
The kernal is unable to re-read the partition tables on the following devices: - /dev/sda

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access
```

Nonetheless, I see sda1, 2, and 5. So in terminal from live cd (this info is inexact; not verbatim):

```
fsck /dev/sda1: clean files xxxxxxxxxx/xxxxxxxxx blocks xxxxxxxxxxxx/xxxxxxxx (idk the #'s)

fsck /dev/sda2 fsck.ext2 No such file or directory whilte trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck /dev/sda5 fsck.swap: not found

```

...roughly said that...

---

### Post by thomasaaron on 2009-11-25
In Gparted form the Live CD, right click the swap partition and then select "Swapoff" from the resulting submenu.

---

### Post by 982000971 on 2009-11-25
Okay did "Swapoff". This removed the error about "The kernal is unable to re-read the partition tables etc" when starting Gparted. Still receive error message from Palimpsest on bootup (was I supposed to re-run fsck?)

---

### Post by thomasaaron on 2009-11-27
I'm unsure at this point of what to make of Palimpsest. I've got a lot of people reporting these results... enough that it's difficult to buy it.

Did fsck report any errors? If not, I'm inclined to discount Palimpsest for the time being.

---

### Post by whoop on 2009-11-27
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by thomasaaron on 2009-11-27
There ya go.

---

### Post by 982000971 on 2009-11-27
Hmmm, well thats a relief I suppose.

---

### Post by PeteBeech on 2010-06-23
I've just installed 10.04 on my Dell Mini 9 following a failed update to the OEM version of 8.04 and immediately got the same message and information that the 3.8GB SSD is "being used outside design parameters".  The message has not gone away after rebooting a couple of times.  

The machine had been back to Dell under waranty in February to investigate what Dell support thought was a hardware fault and no problems were found then, they just re-installed the OS and sent it back.

Peter

---

### Post by isantop on 2010-06-24
I think you have the wrong forum. This forum is specifically for people with System76 computers. We can't offer any official support for Dell. 

There is a Dell support forum in the Ubuntu Forums as well. Just click on the Ubuntu Forums title at the top of the page, then scroll down until you see the link for Ubuntu Dell support.

That said, this is probably a false positive. See [Here](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136). You can run fsck from a LiveCD or Live USB to better determine if you are having problems with your disk.

---

