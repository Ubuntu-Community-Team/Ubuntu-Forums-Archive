---
title: "Upgrading my server"
date: 2009-11-15
forum: Server Platforms
---

### Post by Goobie81 on 2009-11-15
Hi All

I've been putting off upgrading / expanding my server for a long time but I finally am going to take the plunge.

I've got a running plan I just wanted to bounce off you guys to see if i've lost my mind yet :)

I have a server which has dozens of VMs on it (all sorts of Linux, SCO & BSD variants) which I use for my work

These are the specs:

Ubuntu 7.10 x86_64 with vmware server 1.06
md0 2x320 GB IDE (md raid 1 for OS & ISO store)
md1 4x1TB SATA (md raid 5 for data & vmware)

md0 is a PV for LVM and the everything is on LVs
md1 is encrypted with dm-crypt with an ext3 file system under that (no LVM)

I'm consdering breaking the md0 mirror and installing Karmic on one side and then adding another 1TB sata to md1. 

When i last considered doing this, resizing dm-crypt was still "experimental" and that just scared the bejesus outta me. I'm wondering what [if any] experiences people have had growing a dm-crypt device. 

The order would be (off the top of my head)
1. umount /dev/md1
2. e2fsk -f /dev/md1
3. *Add disk*
4. mdadm --add /dev/md1 /dev/sd*XX*
5. mdadm --grow /dev/md1 --raid-devices=5 (then watch some movies whilst panicing about grow operation)
6. cryptsetup resize *device*(Presumably)
7. resize2fs /dev/md1

Can anyone see any flaws in my plan? :)

---

### Post by aaronchall on 2009-11-15
if it's for work, there's the old adage, if it ain't broke, don't fix it.  So why are you fixing it?

---

### Post by Goobie81 on 2009-11-16
> **aaronchall said:**
> if it's for work, there's the old adage, if it ain't broke, don't fix it.  So why are you fixing it?

Sorry should have mentioned that - i am expanding the array because it's out of space and i want to upgrade because ive been tinkering with it over the last 2 or so years its a bit screwy. Also i want to take advantage of a more recent version of Ubuntu (Not that Ubuntu ages like Windows does! :))

Last time i formatted this Gibbon was the latest & greatest - i would prefer to either put Hardy or Karmic on it (hardy for the LTS factor).

---

### Post by aaronchall on 2009-11-16
I'm a total noob, but good luck getting a better quick response.  Here's a suggestion, that I think might be best for you:  Break the mirror, use the free space for the next 6 months, when 10.4 comes out, it will be a new LTS, and you'll have at least 5 more months to plan for the thing, and for the terabyte to get cheaper.  Who knows, by then maybe the world will end and you'll gain yourself an evening of worry free movie watching...

---

### Post by Goobie81 on 2009-11-16
> **aaronchall said:**
> I'm a total noob, but good luck getting a better quick response. Here's a suggestion, that I think might be best for you: Break the mirror, use the free space for the next 6 months, when 10.4 comes out, it will be a new LTS, and you'll have at least 5 more months to plan for the thing, and for the terabyte to get cheaper. Who knows, by then maybe the world will end and you'll gain yourself an evening of worry free movie watching...

Sound advice :) Although i'm not sure I can wait till April next year  :neutral: not to mention it'll be a fresh release!

LTS isn't crucial really, stability is probably the more important factor. Perhaps Hardy or Intrepid ?

---

### Post by aaronchall on 2009-11-16
> **Goobie81 said:**
> Sound advice :) Although i'm not sure I can wait till April next year  :neutral: not to mention it'll be a fresh release!

LTS isn't crucial really, stability is probably the more important factor. Perhaps Hardy or Intrepid ?

My thoughts on the 10.4 LTS were that it would provide the longest run stability, and given this is server you're dealing with, I can't imagine too much going wrong, especially if you give it a month or two to work out bugs, but...

I don't know, I'm now totally out of my depth, man, and I don't have experience with the older distributions, and I'm just getting started. Wait about a day or so, and bump the thread if no response...

---

### Post by Goobie81 on 2009-11-16
> **aaronchall said:**
> My thoughts on the 10.4 LTS were that it would provide the longest run stability, and given this is server you're dealing with, I can't imagine too much going wrong, especially if you give it a month or two to work out bugs, but...

I don't know, I'm now totally out of my depth, man, and I don't have experience with the older distributions, and I'm just getting started. Wait about a day or so, and bump the thread if no response...

Don't talk yourself down too much! One thing I like about Ubuntu is that it's pretty consistent across the versions (I'll refrain from finger pointing). I've been working with Linux & UNIX for years and I only joined the Ubuntu bandwagon from Gibbon onwards (after being disappointed by Debian Etch) and i've never looked back. I forced my current employer to switch the entire infrastructure (servers & desktops) from a medley of unreliable systems running all sorts of distributions to 100% Ubuntu Hardy and things are rock solid now.

---

