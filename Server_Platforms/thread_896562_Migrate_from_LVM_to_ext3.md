---
title: "Migrate from LVM to ext3"
date: 2008-08-21
forum: Server Platforms
---

### Post by ager01 on 2008-08-21
I need to migrate my existing Dapper server's LVM HDD to RAID with ext3. I successfully compiled RAID card drivers, created and mounted the root partition and copied everything from my old LVM drive. After compiling new vmlinuz, initrd and editing grub to point to /dev/sda5 instead of LVM, GRUB starts loading the kernel, but I get stuck at the message "Waiting to mount root filesystem". My guess is that something is still trying to use LVM instead of my ext3 partition. Any suggestions?

---

### Post by windependence on 2008-08-21
Usually, with a real hardware RAID card, you don't need drivers because the logical drive is created at the BIOS level before the machine boots. Did you set up your RAID array and logical drive?

-Tim

---

### Post by ager01 on 2008-08-21
> **windependence said:**
> Usually, with a real hardware RAID card, you don't need drivers because the logical drive is created at the BIOS level before the machine boots. Did you set up your RAID array and logical drive?

-Tim

Drivers are not an issue here. My RAID is perfectly viewable when I boot from the original LVM HDD. Moreover, the GRUB attempts to boot from RAID and goes through stage1.  The problem starts when I get to stage 2, and get stuck in "Waiting to mount root filesystem"

---

### Post by windependence on 2008-08-21
I'm wondering if it can't find the root file system. LVM also marks the system as LVM and the marker may still be present. How did you copy the files from your LVM volume?

-Tim

---

### Post by ager01 on 2008-08-21
> **windependence said:**
> I'm wondering if it can't find the root file system. LVM also marks the system as LVM and the marker may still be present. How did you copy the files from your LVM volume?

-Tim

I cp'd all dirs except for /proc and /sys. I was wondering how I could check for presence of LVM marker and change it to ext3

---

### Post by windependence on 2008-08-21
Can you post your dmesg?

-Tim

---

### Post by ager01 on 2008-08-21
Nothing is written to dmesg when I try to boot from my RAID card. I get stuck after the following message appears on the screen:
Uncompressing, OK Booting the kernel

---

### Post by ager01 on 2008-08-25
Any ideas?

---

### Post by sciurus on 2008-08-31
Post the grub configuration file.

---

### Post by windependence on 2008-08-31
Make sure you have the right boot drive selected in your bios also. It may still be set for the old drive instead of the RAID array logical volume.

-Tim

---

