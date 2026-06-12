---
title: "Better to point to new ppas or install and reconfigure?"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by ewangr on 2013-03-29
So I have put in a decent amount of time getting my setup the way I want it, but I am hearing good things about this release. Part of me wants to just change my repositories to point to the new packages and let Software Center and Synaptic take it from there. But I am concerned that will leave enough "cruft" that things will be unstable. I could install from scratch, but in addition to the time to reconfigure, I'm a little nervous about making sure my 4 drives in a RAID array will still be seen as an array - while I don't have the OS on it, I'm not sure how the superblock would handle the version difference, etc.

Thoughts?

---

### Post by ManamiVixen on 2013-03-29
It depends on what version you are upgrading from. 12.04 to 13.04, you might have issues. But 12.10 to 13.04 is very easy since there isn't TOO much change. So pointing 12.10's ppa's to 13.04's ppa's is no trouble.

---

### Post by andrew.46 on 2013-03-29
Just to play the devil's advocate here: I am a firm believer in a clean install rather than an upgrade, even with a complex hdd setup. And against the flow of Ubuntu opinion I am not such a big fan of PPAs, too many possibilities of breakages in the less expertly built packages...

---

### Post by scottbomb on 2013-03-29
I installed Y PPA Manager from webupd8.org just for this purpose and it worked great. All the PPAs that were disabled are now enabled and I've had no issues (so far).

---

### Post by PJs Ronin on 2013-03-29
My 12.04LTS was stable and had a bunch tweaks (postgresql and VMs) that I could not afford to lose (and couldn't remember what they all were or where I got them from).   I also had a bad 12.04 setup in that my HD only contained two partitions, one for everything Ubuntu and one for data so I was leaning towards a new install with decent partitioning. I tested 12.10 in a VM and was not a happy camper.   I tested 13.04 in a VM and liked what I saw and ended up like OP... do I upgrade or new install.

I first decided on the upgrade route.   I got another HD same size as my original and did a DD clone of my current system and then updated the clone by pointing at the new repos.   I tried 12.04 -> 12.10 -> 13.04 and 12.04 -> 13.04 and nothing really worked well... the system always ended up borked enough that I was not happy with the result, but delighted with the potential.   In the end I decided to bite the bullet and do some decent partitioning on my new drive and do a fresh install.

I selected the raring mini.iso (I'm download constrained whenever I wander from a local mirror site) and then tried a CLI minimal install with (essentially) ubuntu-desktop and no recommends.   Again, I ran into a borked system.   Finally, I launched from the mini-iso again and this time let it do a 'proper' ubuntu-desktop install.   Success! All those things I thought I couldn't remember or find again have been overcome.   I now have 13.04 on a properly partitioned drive, with all my data intact and all my 'tweaks' back.   I also have the ability to migrate to 13.10, 14.04 etc with greater ease.

My recommendation... bite the bullet and go with a fresh install.

Edit: I hasten to add that I'm sure most of the borkage was due to my ineptness.

---

