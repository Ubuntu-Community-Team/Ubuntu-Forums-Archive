---
title: "Wipe Swap?"
date: 2011-01-04
forum: Security
---

### Post by PDA1 on 2011-01-04
For the moment I want to wipe/clear/sanitize the SWAP drive (or partition where swap resides).

Do you have a recommended command to do it?


It probably would be smart to encrypt the swap (yeah, like I really know what I'm talking about!) as I've read other places users doing that but it's pointless to do that if it'll only provide a limited protection from snoopers.

---

### Post by artie_effim on 2011-01-04
Best to do that with a liveCD.

Boot up the live cd and use dd to wipe (or send zeros) the swap partition.  I can't give you the command to do so, it would violate the ToS here, but a google search will show you the way.  MAKE SURE you do it to the swap partition, because this is really destructive (by which I mean, if you do it to any other partition, you will be building the system from scratch next).

There is research that says a  [35 pass wipe]("http://en.wikipedia.org/wiki/Gutmann_method") is the best way to wipe magnetic media, others say [7 passes]("http://stackoverflow.com/questions/276832/how-does-a-7-or-35-pass-erase-work-why-would-one-use-these-methods") are enough, some say that just [overwriting with zeros]("http://www.anti-forensics.com/disk-wiping-one-pass-is-enough") is good enough.  Read 'em all and make your choice. As a CISSP I would use the single pass, it would take a nation-state to retrieve that data (maybe?).

As far as encrypting swap see [https://help.ubuntu.com/community/EncryptedFilesystemHowto]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")

---

### Post by Grenage on 2011-01-04
> **PDA1 said:**
> For the moment I want to wipe/clear/sanitize the SWAP drive (or partition where swap resides).

Do you have a recommended command to do it?


It probably would be smart to encrypt the swap (yeah, like I really know what I'm talking about!) as I've read other places users doing that but it's pointless to do that if it'll only provide a limited protection from snoopers.

Have you considered disabling the swap?

Regardless - you could temporarily disable the swap, fill it with nonsense, then re-enable it.

---

### Post by handy on 2011-01-04
I'm somewhat surprised that people on this forum would have data in their swap file that they are so concerned about other undesired people accessing!

Let alone actually going through the motions of zeroing it.

The thing gets perpetually overwritten anyway. If you have 1GB of RAM or more you don't even need /swap unless you do serious graphics &/or sound work.

I've not used /swap on my 1GB system for approaching a couple of years now.

---

### Post by HermanAB on 2011-01-04
Howdy,

I suggest that you read the swapon man page:
$ man swapon

---

