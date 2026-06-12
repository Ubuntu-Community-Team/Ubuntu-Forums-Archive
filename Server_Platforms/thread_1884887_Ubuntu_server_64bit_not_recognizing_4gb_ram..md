---
title: "Ubuntu server 64bit not recognizing 4gb ram."
date: 2011-11-22
forum: Server Platforms
---

### Post by kostis12345 on 2011-11-22
Hi, I recently set up an ubuntu server box but I noticed that even though I'm using the 64bit version(I've doublechecked using uname -m, it returns X86_64 which I assume it means 64bit) it won't use all 4Gb of my ram. Do you think that enabling PAE would solve my problem? What about activating memory remapping in the BIOS settings?

Thanks a lot.

---

### Post by ian dobson on 2011-11-22
Hi,

Check for a BIOS update. It sounds like a BIOS error.

Also when you boot and run the memory test, how much memory does it display/test?

Regards
Ian Dobson

---

### Post by darkod on 2011-11-22
And how much does it see exactly?
If there is integrated graphics on the board don't forget that this takes part of the RAm memory usually, and it does it in such manner that it's unavailable for the system even when the graphics doesn't use all of it.
Some boards sometimes come with this setting on high value, so you might see even 512MB cut off, which is half a GB.
If it's not that, I have no ideas right now except faulty RAM modules (some of them).

---

### Post by kostis12345 on 2011-11-22
> **darkod said:**
> And how much does it see exactly?
If there is integrated graphics on the board don't forget that this takes part of the RAm memory usually, and it does it in such manner that it's unavailable for the system even when the graphics doesn't use all of it.
Some boards sometimes come with this setting on high value, so you might see even 512MB cut off, which is half a GB.
If it's not that, I have no ideas right now except faulty RAM modules (some of them).
Using freem -m I get a total of 3261. If I added a graphics card, would it change anything? anything. Thanks.
> **ian dobson said:**
> Hi,

Check for a BIOS update. It sounds like a BIOS error.

Also when you boot and run the memory test, how much memory does it display/test?

Regards
Ian Dobson
I'll try it when I get home, I'm on my mobile right now. Thanks.
I don't know if it's relevant but when booting I remember seeing that it lists something close to 3.3 GB.

---

### Post by ian dobson on 2011-11-22
Hi,

So if the BIOS only displays/checks 4Gb then the BIOS or you've got a bad ram module.

If so try:-
1) Resetting BIOS is defaults.
2) Try swapping your ram modules around(Different slots)
3) If you have several ram modules installed, try only installing 1 after the other and see if they work.

Regards
Ian Dobson

---

### Post by kostis12345 on 2011-11-22
I swapped the modules but it didn't work. When running memtest it lists 2 x 2GB Modules as it should in the memory spd informations but only shows 3319 M in the "Memory" line. I'll update the BIOS and see if it changes anything. Thanks for answering.

---

### Post by ian dobson on 2011-11-22
Hi,

Just try enabling memory remapping, that should do it. If not update your BIOS.

On my big backend server (16Gb ram), I had to get in contact with the motherboard supplier (asus) and get them to fix their BIOS which took 2 beta versions before they fixed it.

Regards
Ian Dobson

---

### Post by kostis12345 on 2011-11-23
I'll try that thanks :)

---

