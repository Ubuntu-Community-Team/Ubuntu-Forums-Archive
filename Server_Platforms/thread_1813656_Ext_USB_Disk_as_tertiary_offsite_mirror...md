---
title: "Ext USB Disk as tertiary offsite mirror.."
date: 2011-07-28
forum: Server Platforms
---

### Post by effgee on 2011-07-28
Looking for a few pointers here.

I am trying to automate the adding and removal of two external usb disks to my linux raid mirror (md) that I use for an offsite copy of my data.

This is what I currently do.

Server has 2 x 500 gb internal disks setup with linux raid 1. (md)

I connect 1 of the external usb disks, add it as a secondary mirror to the main array.

After it rebuilds, I remove it from the array and take it home.

I have two of these external drives so one of them is always offsite, and the other is either being rebuilt, or connected as a secondary mirror.

At the moment, this involves running commands manually. I cannot seem to figure out how to automatically add these disks from and to the array with a script. It seems that every time it rebuilds on the external disk, it gives it a new UUID.

I would like to set it up so:
1.A specific time of day the external disk is removed from the array.
2. If the other usb disk is connected, it is automatically added to the array and the rebuild starts.


Can someone assist?

---

### Post by Wayne_V on 2011-07-28
can you provide the commands you run now to add and remove drives from your md array?

---

### Post by effgee on 2011-07-28
Yeah, I'll have to look into it. 
Give me a little bit.
I've been doing it through webmin.

---

### Post by effgee on 2011-07-28
1. Fail the external usb to enable removal.

mdadm --fail /dev/md2 /dev/sdc2

2. Remove the drive/partition.

mdadm --remove /dev/md2 /dev/sdc2

3. Unplug external drive 1.

4. Plug in external drive 2

5. Add the drive/partition back to the array.

mdadm --add /dev/md2 /dev/sd??  <--- This is the problem. I always have to verify what device has been assigned to it. Sometimes /dev/sdc sometimes /dev/sdd..

How can I assure that the external drive always is detected as a specific device name?
  
6. Automatically starts the rebuild.

---

### Post by effgee on 2011-07-28
I think my solution needs some custom udev rules.
I'm looking into it. If you happen to know your stuff with udev rules, I would appreciate the help, otherwise I'll muck through the documentation. :)

> **Wayne_V said:**
> can you provide the commands you run now to add and remove drives from your md array?

---

### Post by effgee on 2011-07-28
Ok, don't need to rewrite any udev rules.

Found that ubuntu makes some udev symlinks to the device-id in 
/dev/disk/by-id/

Referenced this page: [http://reactivated.net/writing_udev_rules.html#example-usbhdd](http://reactivated.net/writing_udev_rules.html#example-usbhdd)

and mdadm can recreate the array based on those symlinks. Ok, now time to write the script.

---

### Post by Wayne_V on 2011-07-28
yes, that should work fine.  you can monitor /dev/disk/by-id for your know drives (by model-s/n) and then add/sync/remove it automatically.

---

