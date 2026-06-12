---
title: "Power outage while installing 12.04 beta"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dandylion on 2012-04-11
Was just in the process of upgrading from 11.10 to 12.04, and because the upgrade was taking so long, I decided to go run some errands. When I came back I realized that there indeed was a power outage, ruining my upgrade. I now cannot boot from the usb I was using to upgrade, nor get into the os. I have countless amounts of data on my harddrive that I cannot live without. Being somewhat of a noob to ubuntu, I would appreciate any and all suggestions. thanks in advance :)

---

### Post by Mark Phelps on 2012-04-11
Another Precise thread.  Please move to the Precise Development forum.  thanks

---

### Post by critin on 2012-04-11
The flash was probably corrupted through the outage.  You'll need to create another live iso to boot and check the hdd to see if your personal files are still there and recoverable.

---

### Post by oldfred on 2012-04-11
Moved to Precise sub forum.

Sometimes a total power down/cold boot will allow locked up system to boot with CD or USB. critin could also be correct, but usually writes that are only partially done are what cause the major corruption.

You should image hard drive and see if then from CD or USB you can mount it and recover data. Always best to have good backup before any system change.

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by cariboo on 2012-04-11
As critin suggest, recreating the usb drive, then chrooting your installation will probably allow you to fix the upgrade. To chroot your linux partition, boot from a Live CD/USB drive, it doesn't even have to be Precise, as long as it's the same architecture, i386 or AMD64, next open a terminal and type the following commands:

```
sudo mount /dev/sdX /mnt
```

where /dev/sdX is your Ubuntu / partition, next:

```
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```

Next at the prompt type:

```
sudo apt-get -f install
```

This should download and install any broken packages, then:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

This is a prime example of why you need to do a backup of all your important data before attempting to upgrade to a newer version.

Good luck.

---

### Post by dandylion on 2012-04-12
Thank you for the replies! After trying to install the broken packages, I am prompted 

E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/) , are you root?


Now I have been using sudo this whole time... I dont understand the problem...?

---

### Post by xyzzyman on 2012-04-12
[https://lists.ubuntu.com/archives/ubuntu-users/2011-June/246473.html](https://lists.ubuntu.com/archives/ubuntu-users/2011-June/246473.html)

Sounds like dpkg itself is messed up. The steps in that article should fix it.

---

