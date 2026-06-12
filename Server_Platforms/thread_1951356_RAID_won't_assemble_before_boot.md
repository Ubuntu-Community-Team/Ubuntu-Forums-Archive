---
title: "RAID won't assemble before boot"
date: 2012-04-02
forum: Server Platforms
---

### Post by zachlac on 2012-04-02
I have a Ubuntu Server 10.04 LTS system with software RAID and LVM, on a Dell PowerEdge r710.  When I try to boot, it fails to assemble all of the arrays, and thus fails to boot.
What is really vexing is that it boots fine off of a boot CD (SystemRescueCD, if it helps).
Some disk info:
* 4 disks (2 250G, 2 500G), with 3 partitions on the first set of disks and none on the second.
* /boot is on its own RAID1, which assembles correctly (/dev/md0)
* swap is on RAID1, which assembles correctly (/dev/md1)
* root (/) is on a RAID1, which fails to assemble (/dev/md2)

Since root fails to assemble, the LVM fails to initialize, and it drops to initramfs.  However, inside of initramfs, I can run "mdadm --assemble /dev/md2 /dev/sdc /dev/sdd" and it assembles fine.  At this point I boot normally.

Things I've tried:
1) Updating the kernel, including installing backports up to 3.0.
2) Adding rootdelay to grub

Neither of these worked.

Any suggestions?

---

### Post by rubylaser on 2012-04-02
What do you have in /etc/mdadm/mdadm.conf?
```
cat /etc/mdadm/mdadm.conf
```

And, what's the output of this once it's assembled?
```
cat /proc/mdstat
mdadm --detail --scan
```

If you have a properly formatted mdadm.conf file, you'll might just need to update your initramfs to get it working.
```
update-initramfs -u
```

---

### Post by zachlac on 2012-04-02
Thank you thank you thank you.  I've been struggling with this problem for over 6 months, in various forms.  It seems to have been a non-updated mdadm.conf.  I'll test it when I can get some server downtime tonight.

A follow-up question would be...why doesn't mdadm update this file when I create a new array?

Again, thank you.

---

### Post by rubylaser on 2012-04-02
> **zachlac said:**
> 
A follow-up question would be...why doesn't mdadm update this file when I create a new array?


No problem. It would have been created if you'd transferred your array to a new machine and just installed mdadm, or if you'd done a dpkg-reconfigure mdadm.  The best thing to do is when you make a change or create a new array to always update your mdadm.conf file.  This is how I generate mine.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST <system>" >> /etc/mdadm/mdadm.conf
echo "MAILADDR user@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

