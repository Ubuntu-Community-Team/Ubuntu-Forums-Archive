---
title: "Old software raid, new motherboard"
date: 2007-04-02
forum: Server Platforms
---

### Post by AusIV4 on 2007-04-02
I have a software raid with about 400 GB worth of data on it. Without going into too much detail, I need to replace my motherboard with a very similar motherboard. Will it be possible to move my RAID to the new motherboard? If the device names change, how much trouble will I be in?

[EDIT]
For what it's worth, I'm actually using 2 raids, one is a RAID 1, the other a RAID 5.

---

### Post by kidders on 2007-04-02
Hi there,

The beauty of software RAID is that it's effectively platform-independent. All Linux (mdadm/etc, I presume) cares about is that it can access the block devices that make up your arrays ... they don't even have to be real hard disks. The best way to avoid naming problems is to be as non-specific as possible about exactly where an array's component devices are. For instance, try to use UUIDs where you can, or leave Linux to guess about your configuration, rather than actually *telling* it what's what.

Basically...

[LIST]
[*]You can move software RAID component partitions from motherboard to motherboard, or from disk to disk, without any problems.
[*]Remember that both RAID arrays and component devices tend to have UUIDs that you can often use in place of /dev paths.
[*]RAID components know the UUID of the specific array they are part of, so you don't need to worry about weird stuff happening, like devices getting assigned to the wrong array. (Provided of course you don't explicitly instruct Linux to do so!)
[*]If you *must* use them, remember that you can often write regular expression-ish /dev paths. For instance, my /etc/mdadm/mdadm.conf contains references to things like **/dev/hd[abc]1**, which lets me move array components around a little, without having to do any reconfiguration.
[/LIST]

If you're in doubt about anything, the best advice is to go slow, check everything (with liberal use of things like **cat /proc/mdstat** and **mdadm --detail**), and start with the RAID 1 array.

If you've never messed around with RAID like this, leaping into the unknown (with something that, quite often, is waaaay to big to back up) can be unpleasant. If you have more than one computer, may I suggest doing a practice run, by temporarily moving one of your arrays into another machine, so you can see what happens. I learned to use RAID by creating small test arrays, and messing around with them, just to see how easy it is to force systems to do something they shouldn't. If you have a few minutes, you should try ... it'd be very reassuring!

---

### Post by ktulu1115 on 2007-05-11
Not sure if you've done it yet or found another solution, but my recommendation for this type of situation is to use a LiveCD.  kidders provided good information but for an actual test-method:
[LIST]
[*]Move the array (disks) to the new motherboard
[*]Boot up the system with a LiveCD
[*]Install mdadm at a console prompt (sudo apt-get install mdadm)
[/LIST]
..and that should be it!  Off of my Feisty CD, mdadm installation automatically detected and assembled the arrays (all 3 of them!).  All I had to do was mount the devices to temporary directories to ensure I could read from them.  Hope that helps.

---

### Post by ihatethetv on 2008-07-10
whoa old thread, but just curious...can you force this behavior somehow?

I moved a three disk raid5 array that was working hunky-dory in another machine into this machine and it doesn't see it....

What should I do?

Thanks,
Glen

---

### Post by ktulu1115 on 2008-07-11
> **ihatethetv said:**
> whoa old thread, but just curious...can you force this behavior somehow?

I moved a three disk raid5 array that was working hunky-dory in another machine into this machine and it doesn't see it....

What should I do?

Thanks,
Glen

Try reassembling the array with mdadm.  As long as all 3 of your drives and the associated Linux raid partitions are detected, you should be able to assemble it just fine... worked for me when I moved my 4 drive array into a new system.

---

### Post by Victormd on 2008-07-11
what happens if it's a software raid though (bios controled), then changing the MB changes the bios and it might get funky...

---

### Post by ihatethetv on 2008-07-11
I suspect what you're talking about is "FakeRaid" which is like the silicon image and promise chips that do the calculations in software on the host (x86).  

Linux does support those, but migrating them is the big problem...that's the major disadvantage with them....that's my understanding at least.

-Glen

---

### Post by Victormd on 2008-07-11
You're right. Linux does support them and migrating is a big problem... it's even bigger when switching motherboards...

---

