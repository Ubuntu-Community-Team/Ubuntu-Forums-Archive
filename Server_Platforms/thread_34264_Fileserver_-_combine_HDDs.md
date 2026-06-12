---
title: "Fileserver - combine HDDs"
date: 2005-05-14
forum: Server Platforms
---

### Post by YorHel on 2005-05-14
I'm trying to turn my old PII into a small fileserver for my LAN, and so far, it's a success. 
But I want put my HDDs in some sort of Array, so my 3 200gb hdds all have one mount-point, where I can store 600gb of data (3x200)

I have thought of setting up a software RAID 0, and found a good howto here: [http://www.linuxhomenetworking.com/linux-adv/raid.htm](http://www.linuxhomenetworking.com/linux-adv/raid.htm), there are a few problems though, when I set my HDDs in RAID 0, AFAIK, it isn't very easy to just add/remove a hdd to/from the array, and when one hdd crashes, all the data will be lost. 

So: is there a way to combine multiple HDDs into one 'virtual drive' (so I have one huge mount-point) and so I add/remove hdds, without losing all the data on the other hdds?
Performance isn't really that important, as long as it's faster than the network connection (100Mbit), and my 266Mhz pentium 2 can handle it.

Thanks in advance

---

### Post by Gandalf on 2005-05-14
[QUOTE=YorHel]I'm trying to turn my old PII into a small fileserver for my LAN, and so far, it's a success. 
But I want put my HDDs in some sort of Array, so my 3 200gb hdds all have one mount-point, where I can store 600gb of data (3x200)

I have thought of setting up a software RAID 0, and found a good howto here: [http://www.linuxhomenetworking.com/linux-adv/raid.htm](http://www.linuxhomenetworking.com/linux-adv/raid.htm), there are a few problems though, when I set my HDDs in RAID 0, AFAIK, it isn't very easy to just add/remove a hdd to/from the array, and when one hdd crashes, all the data will be lost. 

So: is there a way to combine multiple HDDs into one 'virtual drive' (so I have one huge mount-point) and so I add/remove hdds, without losing all the data on the other hdds?
Performance isn't really that important, as long as it's faster than the network connection (100Mbit), and my 266Mhz pentium 2 can handle it.

Thanks in advance[/QUOTE]
 No, i do not think so....
RAID 0 is the only option *i guess* and it's highly unrecommanded!

---

### Post by LordHunter317 on 2005-05-14
[QUOTE=Gandalf]No, i do not think so....
RAID 0 is the only option *i guess* and it's highly unrecommanded![/QUOTE]No, with three drives you have a bunch of options.

You could do software RAID-5, which would give you 400GB of space and allow you to tolerate one failure.   This is what I would do, personally.

Online capacity expansion is possible but is not really supported, so if you know you'll need more space, I'd buy the disks now.

There are other options, but I'm not going to go into them because this is really the best one.

---

### Post by Jarl Nicolson on 2005-05-15
I'd say your best option would be to use LVM.  This will allow you to add or remove hard drives as you want, and resize a filesystem on a logical volume (if using a filesystem which supports it).

However, like RAID 0, if one drive dies, you're basically out of luck.  I'm not quite sure what i'd do if redundancy was required.  Probably exactly what LordHunter317 suggested.

You might have to recompile your kernel, not sure what ubuntus default config is like (haven't really looked into it).  For the rest, you can read the HOWTO [here](http://www.tldp.org/HOWTO/LVM-HOWTO/).

---

### Post by LordHunter317 on 2005-05-15
[QUOTE=Jarl Nicolson]You might have to recompile your kernel, not sure what ubuntus default config is like (haven't really looked into it). For the rest, you can read the HOWTO [here]("http://www.tldp.org/HOWTO/LVM-HOWTO/").[/QUOTE]Nope.  Ubuntu's kernels come with LVM support.

---

### Post by YorHel on 2005-05-15
Thanks all for your replies, I think I'm going to create one huge LVM partition, with a reiserfs filesystem... and if by any chance a drive fails, it won't do much harm, it's not really important data (mostly backups, etc) :)

---

### Post by LordHunter317 on 2005-05-15
If you're going to do that, you might as well do RAID-0 and at least get some extra performance out of your highly likely to fail array.

Seriously, RAID-5 is a really good idea here.  Data stored on HDDs isn't backups.

---

