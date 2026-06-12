---
title: "GParted takes forever..."
date: 2009-12-19
forum: The Cafe
---

### Post by Yes on 2009-12-19
I needed to add some space to my Windows partition to install something.  So I pop in my GParted live CD, and start it up.  It's been going for about 5 hours, and it's predicting it'll take another 6 hours.  

Gahhhhh this is annoying.

Sorry for ranting lol

---

### Post by gletob on 2009-12-19
Partitioning take A LOT of copying.  So when you have to copy tens to hundreds of GiB around multiple times, the time to complete can add up greatly.  Trust me it's not Gparted's fault.

---

### Post by lisati on 2009-12-19
You are not alone in your frustration. I experienced a rather long and boring wait of several hours freeing up space on my current laptop before installing Ubuntu.

---

### Post by earthpigg on 2009-12-19
the more full any particular partition/drive is, the longer it will take.

sounds like you have an ntfs partition nearly full.

---

### Post by Yes on 2009-12-19
Lol I know it's not not GParted's fault.  It's a ext3 partition that's got about 43 GB full of the 70 GB.

It finally got to 70 GB of 70 GB and I thought it was done, and then I checked what it was doing - the "readonly" check.  The actual copying started and it went up to 5 hours left ><

---

### Post by Xbehave on 2009-12-20
> Partitioning take A LOT of copying. So when you have to copy tens to hundreds of GiB around multiple times, the time to complete can add up greatly. Trust me it's not Gparted's fault.
It sounds like it's doing a dumb move,so it really it's ext and gparted's fault. 

[LIST]
[*]The fsck/readonly check for ext3 will be slooow [ext3 is to blame, if you have a big partition it's worth going with reiserfs or btrfs for the fast fsck alone]
[*]Resizing an fs is always dumb, you shrink it (fairly quick if your not on ext) then you move it (starting at the back you move it bitwise, so if you move a 40GB partition 1GB backwards thats 80GB of r/w instead of 2) [All filesystems are to blame]
[*]gParted could do something clever for a well know FS like ext3, it could move the needed files to the back of the disk and then forge the superblocks but it doesn't [gParted is to blame]
[/LIST]

BTW old copies of gParted are even slower than they have to be what version is the disk using? if it older than v3.9 it **might** be worth stopping and starting it with a the latest version because apparently there was a bug in 3.8 that slowed everything down

---

### Post by earthpigg on 2009-12-20
> Resizing an fs is always dumb

yeah, i don't. if you are at the point where you ***must*** resize due to space issues, it is almost always quicker to back everything important up, delete all partitions, create new ones, reinstall the OS, and restore from backup.

may sound silly, but it's true.

---

### Post by Xbehave on 2009-12-20
> **earthpigg said:**
> yeah, i don't. if you are at the point where you ***must*** resize due to space issues, it is almost always quicker to back everything important up, delete all partitions, create new ones, reinstall the OS, and restore from backup.

may sound silly, but it's true.
Really? I've done that for convenience, but even over a decent lan and using rsync i only got ~10MB/s, whereas disc access is surely higher than that?

---

### Post by earthpigg on 2009-12-20
> **Xbehave said:**
> Really? I've done that for convenience, but even over a decent lan and using rsync i only got ~10MB/s, whereas disc access is surely higher than that?

walk 10 meters to the other side of the LAN. move hard drive from point b to point a, put in computer a.

yes, this requires walking... but will probably save ***time***, if that is the primary concern.

if not, then gparted till the cows come home i suppose.

---

### Post by HappyFeet on 2009-12-20
It's important to defrag windows before resizing. It will take A LOT less time. Better yet, is to use a certain app on Hirens Boot CD. Only takes a few minutes to resize. Use the right tool for the right job. ;)

---

### Post by donniezazen on 2009-12-20
I tried Partition Magic 8.0 and in comparison to Gparted its superfast.

---

### Post by NoaHall on 2009-12-20
Get a new hard drive? Problem solved.

---

### Post by The Real Dave on 2009-12-20
> **earthpigg said:**
> yeah, i don't. if you are at the point where you ***must*** resize due to space issues, it is almost always quicker to back everything important up, delete all partitions, create new ones, reinstall the OS, and restore from backup.

may sound silly, but it's true.

Not for me :) Something always goes wrong. 

That said, I'm gonna have to copy 150Gb of Data at about 7Mb/s over my LAN so I can change a vfat partition to NTFS. Maybe your right...... :)

---

### Post by Yes on 2009-12-20
Lol oh dear, I woke up this morning and it's still going.  It's moving smaller partitions now though so it should go faster.  Hopefully it'll be done by the time I'm done shoveling.

I'm afraid to cancel it after I've already started cause I'm worried it would screw something up (like my data).  Is that a legitamate worry?

---

### Post by markp1989 on 2009-12-20
> **Yes said:**
> Lol oh dear, I woke up this morning and it's still going.  It's moving smaller partitions now though so it should go faster.  Hopefully it'll be done by the time I'm done shoveling.

I'm afraid to cancel it after I've already started cause I'm worried it would screw something up (like my data).  Is that a legitamate worry?

its recomended not to cancel after the read-only test has completed, because if you do it can  cause data loss.

really any partiton editing can cause problems, so its best to back up first, but if u had a backup drive you woulldnt need to shuffle partitions about lol

---

### Post by The Real Dave on 2009-12-20
> **markp1989 said:**
> its recomended not to cancel after the read-only test has completed, because if you do it can  cause data loss.

really any partiton editing can cause problems, so its best to back up first, but if u had a backup drive you woulldnt need to shuffle partitions about lol

+1 just don't do it. I tried it out in a VM, and it resulted in alot of data loss. That said, I recovered it with testdisk, but just be patient :)

---

### Post by Yes on 2009-12-20
Yeah that's what I thought.  I do have a backup, but I didn't want to go though the trouble of reinstalling Arch.  At least this way I can play some playstation while I wait :)

---

### Post by Yes on 2009-12-20
Wooooo after more than 11 hours it's finally done.  It turns out I've been using 3.4, I'm gona burn a new copy of it...

---

