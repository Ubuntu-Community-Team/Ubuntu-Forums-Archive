---
title: "Dull Questions About Creating a File Server"
date: 2005-11-25
forum: The Cafe
---

### Post by Malphas on 2005-11-25
I currently have two 160GB and two 250GB (marketing GB that is) hard drives in my PC and am starting to run out of space.  I'm thinking that I'll take out all the hard drives and the RAID card and and use them for a file server and for my PC I'll just use my motherboard's on-board RAID chip with a couple Raptors or something.

I'd be interested to hear people's opinions and expertise on:

1) What would the best distro be for setting this up?  I was considering Debian, but I would go with Ubuntu if there's any good reasons to do so.

2) Any hardware recommendations with regard to cases, motherboards, network cards etc.?  Also, my current RAID card (Highpoint RocketRAID, can't remember the exact model) only supports 4 drives; if I decided to add more drives what would be the best course of action?

3) Should I just put all the discs in a JBOD array or set up two RAID arrays (striped) as I have presently?

The "server" will only really need to hook up to my main machine, which runs XP.

---

### Post by psoleko on 2005-11-26
Are you worried about data loss? Becuase RAID 0 or JBOD will not in any means protect your data should the worst happen. Otherwise RAID 0 for performance you will only get 2 x 160GB drives in that configuration though, you are losing almost 100GB :( or JBOD if you just want a giant hard drive (meager performance gains if any). I believe Ubuntu supports promise, highpoint, nvidia, via out of the box as well as more high end RAID adapters. If you add more drives at a later date you would need to rebuild your array which will once again mean reinstalling the OS unless you create a seperate array. As for hardware I always recommend AMD processors and nvidia chipsets. Hope some of that random jumble of thoughts helps.

---

### Post by Astrophobos on 2005-11-26
I personaly use a 3ware 7506-4lp on my server. 3ware cards are real hardware raid not like promise, via, intel, nvidia, etc solution that are only or partially software raid. 3ware cards have their drivers include in the kernel for some time now.

For data loss security I suggest raid10 if you can affort loosing 1/2 of your disc space or raid5 otherwise.

For speed I suggest raid0 over JBOD.

Hope it help a little.

---

### Post by Malphas on 2005-11-26
[QUOTE=psoleko]Otherwise RAID 0 for performance you will only get 2 x 160GB drives in that configuration though, you are losing almost 100GB[/QUOTE]
Huh?  Why would I lose 100GB by having the two 160GBs in a RAID 0 array?  And why couldn't I also have the two 250GB drives in another RAID 0 array?  That's how they're all currently configured in my PC.

---

### Post by psoleko on 2005-11-26
[QUOTE=Malphas]Huh?  Why would I lose 100GB by having the two 160GBs in a RAID 0 array?  And why couldn't I also have the two 250GB drives in another RAID 0 array?  That's how they're all currently configured in my PC.[/QUOTE]

Meh..was half awake when I read that. :confused: Thought you had one 160GB and one 250GB. If you put 2 drives of dis-similar size in RAID 0 it defaults to the smallest drive size.

---

### Post by Malphas on 2005-11-26
Ah right, gotcha.

---

