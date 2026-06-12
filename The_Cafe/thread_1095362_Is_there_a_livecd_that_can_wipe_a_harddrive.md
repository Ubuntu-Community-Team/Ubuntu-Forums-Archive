---
title: "Is there a livecd that can wipe a harddrive?"
date: 2009-03-13
forum: The Cafe
---

### Post by NintendoTogepi on 2009-03-13
My test computer's harddrive is incredibly messed up, it won't even boot except from a live cd.

---

### Post by issih on 2009-03-13
Yes, just about all of them..open up the partition editor (gparted) and format the disk from there... one wiped disk.

Obviously this will kill all data on there, I assume you know that, but it doesn't hurt to reiterate it.

---

### Post by Mehall on 2009-03-13
If you REALLY wanan wipe everything (and I mean everything, to DoD levels) get the UBCD, which has DBAN on it.

DBAN, 7 run. Safest way of deleting everything this side of a hammer or a fire.

---

### Post by conundrumx on 2009-03-13
You only need to do one pass of zero's to completely erase a hard drive.  See:

[http://www.securityfocus.com/brief/888](http://www.securityfocus.com/brief/888)
[http://16systems.com/zero/](http://16systems.com/zero/)

Save yourself some time!

---

### Post by .Maleficus. on 2009-03-13
As Mehall said, DBAN (Darik's Boot and Nuke).  Takes a while depending on the size of the drive, but trust me, your hard drive will be clean, no questions asked.

Oh, and UBCD is 'Ultimate Boot CD'.  I don't have it but I should :).  Downloading now.

---

### Post by mividaloca on 2009-03-13
Like previous posts i would say dban, just run the PRNG stream once.

after boot hit enter to go into option mode, hit "m" to select method (PRNG) hit "v" to turn verification off, hit "r" to enter number of rounds and the f10 to start

be warned, 1 round of random PRNG will make it impossible to recover any data with forensic software (Encase)

---

### Post by Mehall on 2009-03-13
> **mividaloca said:**
> Like previous posts i would say dban, just run the PRNG stream once.

after boot hit enter to go into option mode, hit "m" to select method (PRNG) hit "v" to turn verification off, hit "r" to enter number of rounds and the f10 to start

be warned, 1 round of random PRNG will make it impossible to recover any data with forensic software (Encase)

that should be "without forensic software"

3 rounds of PRNG would do it, 10 or more if you want it to be a biotch to do it manually, and a fire to stop it altogether.

---

### Post by Therion on 2009-03-13
If you want to install Ubuntu as your sole OS on the borked drive, just boot to the LiveCD and choose to install.  
When prompted choose the "Guided Install, Use Entire Disk" option.  
*Voila*...  Disk reformatted and a fresh install of Ubuntu all in one fell swoop.

Unless you're hiding from the NSA, that should do the job.

---

### Post by mividaloca on 2009-03-13
> **Mehall said:**
> that should be "without forensic software"

3 rounds of PRNG would do it, 10 or more if you want it to be a biotch to do it manually, and a fire to stop it altogether.

:D Encase is forensic software and incapable of recovering anything from a one pass wipe, To try and get anything back you would need an electron microscope and that is highly expensive and time consuming.

---

### Post by Mehall on 2009-03-13
We have a forensics expert at our uni.

1-pass isn't always safe.

Safe from your average joe, yes, but good software with a competent user behind it will get those bits and bytes

---

### Post by Swagman on 2009-03-13
delete everything on target drive then connect a dv camcorder and let it fill it.

Data gone

---

### Post by mividaloca on 2009-03-13
> **Mehall said:**
> We have a forensics expert at our uni.

1-pass isn't always safe.

Safe from your average joe, yes, but good software with a competent user behind it will get those bits and bytes

The Great Zero Challenge
[http://16systems.com/zero/index.html](http://16systems.com/zero/index.html)

> "According to our Unix team, there is less than a zero percent chance of data recovery after that dd command. The drive itself has been overwritten in a very fundamental manner. However, if for legal reasons you need to demonstrate that an effort is being made to recover some or all of the data, go ahead and send it in and we'll certainly make an effort, but again, from what you've told us, our engineers are certain that we cannot recover data from the drive. We'll email you a quote."

Some experts claim to recover from a single pass but what has actually happened is they have run a "quick erase" that only takes out the first and last sectors, however if a HDD has bad partitions then data could be recovered from them but still unlikely.

Nothing new but some infos
[http://www.securityfocus.com/brief/888?ref=rss](http://www.securityfocus.com/brief/888?ref=rss)

---

### Post by DMcA on 2009-03-13
I'm no expert but I believe police (intelligence services (?)) forensics can look at the areas of the disk between where the disk is typically read/written to try and figure out previous magnetisation of nearby bits. Extremely time consuming and impossible to completely restore everything but there can still be some information lurking about on the platter.

---

### Post by mividaloca on 2009-03-13
> **DMcA said:**
> I'm no expert but I believe police (intelligence services (?)) forensics can look at the areas of the disk between where the disk is typically read/written to try and figure out previous magnetisation of nearby bits. Extremely time consuming and impossible to completely restore everything but there can still be some information lurking about on the platter.

:D And experts would differ

---

### Post by happysmileman on 2009-03-13
> **DMcA said:**
> I'm no expert but I believe police (intelligence services (?)) forensics can look at the areas of the disk between where the disk is typically read/written to try and figure out previous magnetisation of nearby bits. Extremely time consuming and impossible to completely restore everything but there can still be some information lurking about on the platter.

With an electron microscope this MAY be possible, it's never actually been demonstrated and there's debate as to whether it's actually possible.

The confusion is that people often get deleting and overwriting files mixed up, when you delete a file you don't actually delete any of the data, just the reference to it, and it gets marked as OK to overwrite. But it doesn't actually overwrite it.

---

### Post by DMcA on 2009-03-13
> **happysmileman said:**
> With an electron microscope this MAY be possible, it's never actually been demonstrated and there's debate as to whether it's actually possible.

The confusion is that people often get deleting and overwriting files mixed up, when you delete a file you don't actually delete any of the data, just the reference to it, and it gets marked as OK to overwrite. But it doesn't actually overwrite it.

Sure, I'm quite aware of that. Especially problematic [|beneficial] when you're using a journaling FS (like me, but then I don't have any data so incriminating I'd need to delete it into oblivion. And if I did it would be encrypted anyway)

---

