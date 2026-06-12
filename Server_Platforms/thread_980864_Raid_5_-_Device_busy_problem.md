---
title: "Raid 5 - Device busy problem"
date: 2008-11-13
forum: Server Platforms
---

### Post by obg123 on 2008-11-13
I know this is a common problem, as I've seen similar posts. I have yet to find a solution that works for me. :(

mdadm --stop will NOT do the trick. lsof says nothing about my disks or md0. /proc/mdstat reports all personalities, no unused devises, and nothing else.

I want 5 disks + 1 spare in my array. All disks are partitioned (one full parition) and typed FD.

```
mdadm -Cv /dev/md0 --assume-clean --force -l5 -n5 -x1 -c128 /dev/sd{a,b,c,d,e,f}1
```
gives
```
mdadm: layout defaults to left-symmetric
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: Cannot open /dev/sdf1: Device or resource busy
mdadm: create aborted
```

Why isn't sda1 in there? I did have an old IDE disk (the others are SATAII) that got the name sda, and I wrote a raidtab file (as specified in the SW Raid HOWTO) before I realized it wasn't needed. Now the IDE disk is called sdg. Perhaps something was done by the kernel before I removed that file? Or maybe somthing was done by the BIOS as I was experimenting with my fake raid. (But in that case, all disks would be equally busy, right?) I also tried to create the array with sdb1-sdg1 before I realized that the IDE disk had changed places. - This might be the real problem, now that I think about it.

In any case, how do I see what's keeping my devices busy, and primarily, how do I stop it? The only step I can think of right now is running the command from a boot CD shell. I can't do that from remote though, and right now I am rather remote...

Please, I really need som help with this.

I am using Ubuntu Alternative x86_64 8.10.

---

### Post by fjgaude on 2008-11-13
Make sure none of the drives are mounted... then using mdadm zero the superblocks of each drive:

sudo mdadm --zero-superblock /dev/sd[nn]

Then try to create once again.

---

### Post by obg123 on 2008-11-13
```
root@kakmonstret:~# mdadm --zero-superblock /dev/sda1
mdadm: Unrecognised md component device - /dev/sda1
root@kakmonstret:~# mdadm --zero-superblock /dev/sdb1
mdadm: Couldn't open /dev/sdb1 for write - not zeroing
root@kakmonstret:~# mdadm --zero-superblock /dev/sdc1
mdadm: Couldn't open /dev/sdc1 for write - not zeroing
root@kakmonstret:~# mdadm --zero-superblock /dev/sdd1
mdadm: Couldn't open /dev/sdd1 for write - not zeroing
root@kakmonstret:~# mdadm --zero-superblock /dev/sde1
mdadm: Couldn't open /dev/sde1 for write - not zeroing
root@kakmonstret:~# mdadm --zero-superblock /dev/sdf1
mdadm: Couldn't open /dev/sdf1 for write - not zeroing

```

Once again, sda1 is different from the rest.

Create still gives the same result. ](*,)

And no, none of these drives are mounted anywhere.

---

### Post by fjgaude on 2008-11-13
Well, something is using them even if not mounted. The only think I can suggest at this point is to see what happens if you use a LiveCD. From there you can install **mdadm** and then try doing the things you wish with the drives.

---

### Post by obg123 on 2008-11-14
Hmm, yes... The "liveCD", do you mean the regular desktop installation CD? I currently have only the alternative and the server CDs, but I kind of remember such a feature from the previous versions.

---

### Post by fjgaude on 2008-11-14
LiveCD, any will do that permits you to do stuff, commands, and add **mdadm** to it.

Also, what did you do with these drives before trying to create the array?

---

### Post by obg123 on 2008-11-17
Ok, now I have entered the shell from "Rescue mode" on the Server installation CD. Here I can issue all my mdadm commands. Last thing I tried was to --zero-superblock all disks and then creating the array (just like I did above).

From the same shell I added ReiserFS. In this process I lost sda and my spare set in.  I waited until the array was rebuilt. Then I could mount it - no problem.

However, after reboot to the regular prompt. Nothing worked again. All I could figure out was that my failed sda was now put as spare... This doesn't seem like a great choice.

Any ideas? Any more input required? I could post dmesg output or parts of /var/log/messages if anyone thinks that it would help.

:(

---

### Post by fjgaude on 2008-11-17
After you created the array did you make a filesystem on it?

If you did, did you mount the array while using the LiveCD?

What does

```
sudo mdadm -D /dev/md0
```

show?

---

### Post by obg123 on 2008-11-18
Hey!!! Now it works!

It was my bios still messing with my disks even though I had switched from Raid mode to AHCI. I had to go back to Raid mode and really remove all disks from any kind or Raid association. Then I had to switch to AHCI again (which obviously not completely switches raid off).

The extremely strange thing here is why there is a difference...

When I boot from a live CD (on my extarnal DVD unit connected via USB), the BIOS does not scan for raid sectors on my disks, and therefore does not start anything funny. This means I can to whatever I want during this session.

However, when I boot up my installed system, which resides on a memory stick - also connected via USB - it interferes like crazy! This happens even if I boot up in single user mode.

So, anyone, please explain this to me. :confused:

---

### Post by Robstarusa on 2008-11-18
> **obg123 said:**
> Hey!!! Now it works!

It was my bios still messing with my disks even though I had switched from Raid mode to AHCI. I had to go back to Raid mode and really remove all disks from any kind or Raid association. Then I had to switch to AHCI again (which obviously not completely switches raid off).

The extremely strange thing here is why there is a difference...

When I boot from a live CD (on my extarnal DVD unit connected via USB), the BIOS does not scan for raid sectors on my disks, and therefore does not start anything funny. This means I can to whatever I want during this session.

However, when I boot up my installed system, which resides on a memory stick - also connected via USB - it interferes like crazy! This happens even if I boot up in single user mode.

So, anyone, please explain this to me. :confused:

When you got "device busy" was there anything in /dev/mapper ?

It's possible dmsetup assigned those to a fakeraid device or something.

man dmsetup for more info.

---

### Post by fjgaude on 2008-11-18
The whole thing likely has to do with USB drives, vs IDE, ACHI, and how the BIOS sets up to use drives in a raid array.

What you are doing is somewhat out of the mainstream and likely not tested too well by Linux developers.

You might try putting his line in your fstab file and see if that fixes anything:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

It has done much good for a few folks.

---

