---
title: "Pangolin RAID configuration"
date: 2010-05-25
forum: System76 Support
---

### Post by Mendel314 on 2010-05-25
Dear helpful forumpeople,
My Pangolin is in the mail, and will arrive today. I was/am considering getting an SSD to replace the 5400rpm drive I initially opted for, but yesterday I found seagate 880gb external usb drives on sale at Best Buy for 89$, so I bought 4 and am considering setting up a RAID configuration. Does anyone know:
 
1. does the Pan Performance come with a native RAID controller?
2. What would the performance boost be like? (everything will be hooked up via USB, but I may add some of my other external HDs to the configuration if I go for RAID 0+1, in which case there might be one connected via eSATA also (not terribly important, but worth mentioning)
3. if I did this, would the SSD still add appreciably? probably, right?
4. The Pan P7 has a PCI card slot, right? So I could hook up an eSATA RAID array?
 
I'm almost definitely upgrading the native HDD, either a 7200 RPM drive (maybe waiting for the Momentus XT to be released on 2.5 in.) or an SSD
 
Disclaimer:
someone here will inevitably ask me why I need this stuff and what I will be using it for. I don't need it, I will be using this for movies, music, and games. I like cool toys, and find the thought that my machine can handle whatever I throw at it comforting. My resources aren't limitless, but given what I already have, and the pure fun factor of an SSD, that would be the last thing I might buy (probably an 80 GB one, then I figure with at least 2 HDs configured in RAID I'll probably have enough space.)

---

### Post by thomasaaron on 2010-05-25
> 1. does the Pan Performance come with a native RAID controller?

No. You would have to figure out how to do software RAID.

> 2. What would the performance boost be like? (everything will be hooked up via USB, but I may add some of my other external HDs to the configuration if I go for RAID 0+1, in which case there might be one connected via eSATA also (not terribly important, but worth mentioning)

There are performance differences between different types of RAID (for example: RAID 0, RAID 1, RAID 5, RAID 10). But I doubt setting up a bunch of external hard drives with RAID is going to actually improve your COMPUTER'S performance. It will just make your data redundant -- and thus safer.

> 3. if I did this, would the SSD still add appreciably? probably, right?

It's hard to say. Since it sounds like you'll have a bunch of mis-matched drives, I kind of doubt it. But I might be wrong.

> 4. The Pan P7 has a PCI card slot, right? So I could hook up an eSATA RAID array?

No, it doesn't have a PCI slot. But I *think* you mean an Express card slot. Not sure how that will help, though.

I'm not trying to be discouraging. I think experimenting is awesome, and it's a great way to learn -- even if from our mistakes (which is how I generally do it). But I'm trying to visualize your set-up, and it seems difficult, high-maintenance... and I'm not really seeing the value of it. There are a lot of good ways to back up data in Ubuntu's repos. 

RAID isn't something that is really meant to be hooked up and disconnected from your laptop. It's meant to be more of a permanent configuration. It could probably me *made* to work somehow/somewhat, but I'm not sure it's the best tool for the job, and you would definitely be trying to bend it into a configuration it was not meant for.

That said, I hope it succeeds. I've never seen anybody do it that way before! But whether it succeeds or not, I think you'll learn a heck of a lot. Good luck.

---

### Post by samalex on 2010-05-26
I agree with Thomas, setting-up a RAID on a laptop might be a great way to learn, but I don't see how it could be very practical.  I'd suggest finding or building a low-end or older box that can handle multiple drives and setting up a SAN of sorts using Software RAID in Linux.  This way you can connect to it via the network when you're on your home network, but there's nothing to physically connect or disconnect when you come and go.

Is your goal in going with RAID to have a backup of your laptop?  If so and if you do have some sort of server at home you can dump your stuff to, there are a number of backup apps or even shell scripts that'll do this as well without having to go through the hassle of configuring and maintaining a RAID... not that they're all that to maintain.

Just some thoughts --

Sam

---

### Post by JohnnyC35 on 2010-05-26
heh. set up a raid0 with the internal drive and an external. and if you do any border crossings (like US/Canada). The nosey guards can't look into your files then without the external hooked up  :P

sorry just trolling. no insight here

---

