---
title: "convert raid 5 to raid 6?"
date: 2009-11-21
forum: Server Platforms
---

### Post by twidget on 2009-11-21
hi,
I have a 3 disk raid 5 array on my server that i would like to add a disk to and convert into a raid 6 array. Is this possible or would I have to kill the array and start from scratch?

---

### Post by wirelessmonkey on 2009-11-21
There is [Some]("http://neil.brown.name/blog/20090817000931") information out there for you, but IMO, it depends on how RAID saavy you are and how important your data is.

---

### Post by Vegan on 2009-11-21
RAID6 has more complicated error correction algorithms and needs a powerful processor to make it useful.

---

### Post by twidget on 2009-11-22
how powerful are we talking? The cpu I'm using is an athlon xp 3000+ but I'm not running GUI.  I checked processor load last time I was transferring a large chunk of data and IIRC I wasn't using that much. Is there a good noob friendly explanation of mdadm out there that you can recommend?

---

### Post by insane_alien on 2009-11-22
your processor will be fine handling RAID6 i had a 500MHZ PIII running a RAID 6 and it handled it fine.

i'm not really sure how you'd transform the AID as they both use distributed parity blocks and would require the data to be rearranged on the disk. 

your safest method is going to be, do a full back up first(you should have one already anyway if you're being smart) and then just kill the RAID and make a new one. as you have a backup you can have a go at tinkering with it, but ti think its unlikely.

---

### Post by CharlesA on 2009-11-22
> **insane_alien said:**
> 
your safest method is going to be, do a full back up first(you should have one already anyway if you're being smart) and then just kill the RAID and make a new one. as you have a backup you can have a go at tinkering with it, but ti think its unlikely.

That would be the safest method. Always have a backup.

---

### Post by twidget on 2009-11-23
is there a viable backup method other than just burning to DVDs? I do that with the stuff I can't afford to lose but it would be nice if there was a way to do it without filling my apartment with DVDs. also since this RAID array does not contain the OS would it be easier to kill and rebuild from within Ubuntu or just do a fresh install of everything? i haven't done anything to the OS that I cant recreate in roughly half an hour so I'm still flexible as far as that goes.

---

### Post by CharlesA on 2009-11-23
> **twidget said:**
> is there a viable backup method other than just burning to DVDs? I do that with the stuff I can't afford to lose but it would be nice if there was a way to do it without filling my apartment with DVDs. also since this RAID array does not contain the OS would it be easier to kill and rebuild from within Ubuntu or just do a fresh install of everything? i haven't done anything to the OS that I cant recreate in roughly half an hour so I'm still flexible as far as that goes.

I use an external hard drive for backups. Backing up 1.5TB of data would require a lot of DVDs. ;)

I didn't see if you said it was a HW RAID or SW RAID. Basically what you'd have to do is back up all yer data to another device. Kill the RAID array, recreate it and copy it back.

---

