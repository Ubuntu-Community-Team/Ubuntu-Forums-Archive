---
title: "Scanners: which one to use: HP 4570c or Scanjet 3p"
date: 2008-10-12
forum: The Cafe
---

### Post by jonathonblake on 2008-10-12
All;

I'm not sure where to ask this question, but this seemed appropriate.

I don't have a SCSI card on my system.

I've got two SCSI HP Scanjet 3p scanners.
I do not have any manuals, cables, or anything else for those scanners.

I also have an HP Scanjet 4570c USB connection.
I don't have any cables,manuals, etc for it.

According to the HP website, both scanners provide the same optical resolution -- 2,4000 dpi.

Are their any major differences between these two scanners, and if so, which one would be preferable to keep, and locate cables for?(And why is it the preferable choice.)

xan

jonathon

---

### Post by mips on 2008-10-13
Keep the HP 4570c.

The Scanjet 3p series is much older and came out in the days prior to USB hence the SCSI interface.

The 3p has an 'optical' resolution of 2400dpi but that is the interpolated resolution (done in software), the actual hardware resolution is 300 or 600dpi. 
The 4570c hardware resolution is 2400dpi and the interpolated resolution will be much higher.
You need to compare apples with apples ;) Optical (interpolated software) resolution is a marketing gimmick.

For the inferior 3p you will have to purchase an old style SCSI adapter card and expensive SCSI cable. The 4570c just requires a cheap usb cable. In the old days they used SCSI because at the time it was the only available interface that could provide the speed needed. SCSI is great but is no longer required for consumer scanners.

We had the 3p at work yonks ago so I'm familiar with them. Go with the 4570c as it is the newer/better scanner.

Here are the manuals for your scanner:
[http://h10032.www1.hp.com/ctg/Manual/bps05710.pdf](http://h10032.www1.hp.com/ctg/Manual/bps05710.pdf)
[http://h10032.www1.hp.com/ctg/Manual/bps05769.pdf](http://h10032.www1.hp.com/ctg/Manual/bps05769.pdf)

---

### Post by jonathonblake on 2008-10-13
> **mips said:**
> Keep the HP 4570c.

Thanks for your explanation of why I should keep that one.

> 
The 4570c hardware resolution is 2400dpi and the 
I knew there was a reason not to trust optical resolution, but I couldn't remember what type of resolution I should be looking at.   

> 
Here are the manuals for your scanner:
[http://h10032.www1.hp.com/ctg/Manual/bps05710.pdf](http://h10032.www1.hp.com/ctg/Manual/bps05710.pdf)
[http://h10032.www1.hp.com/ctg/Manual/bps05769.pdf](http://h10032.www1.hp.com/ctg/Manual/bps05769.pdf)

Thanks for those URLs.

xan

jonathon

---

### Post by jonathonblake on 2008-10-21
> Keep the HP4570c

And now that I've gotten rid of the HP SCSI scanners, I discover that there is no Linux support for the HP 4570c.  :(

I thought that SANE worked for every scanner out there.

xan

jonathon

---

### Post by mips on 2008-10-21
> **jonathonblake said:**
> And now that I've gotten rid of the HP SCSI scanners, I discover that there is no Linux support for the HP 4570c.  :(

I thought that SANE worked for every scanner out there.


For that I'm truely sorry :oops: I only evaluated it on hardware specs. I did a search and there is no SANE support, even windows users seem to have issues as they need the software cd from hp.

I thought the same, especially seeing it is HP. This must be a rare case.

Did you sell the other ones? Maybe you could sell this one as well and then with the combined funds get another.

Once again I'm really sorry about this, I should have checked linux support when I replied to your post.

If it is any consolation the 3p has really crappy resolution so it would not have been that great and you would have had to splash out for a scsi card.

---

### Post by jonathonblake on 2008-10-21
> **mips said:**
> For that I'm truly sorry :oops: I only evaluated it on hardware specs.

It didn't even occur to me that drivers would be an issue.  

> Did you sell the other ones? 

I freecycled them.

> I should have checked linux support when I replied to your post.

Its an HP scanner.  It is a USB scanner.  I only started to look for a driver when it didn't come up.  I thought it was PEBKAC.  It was only after running a couple of diagnostics, that I I realized that that wasn't the problem.  

If I can get the drivers,I'll try running it either under WINE, or with Win2K as a virtual OS.  

> If it is any consolation the 3p has really crappy resolution so it would not have been that great and you would have had to splash out for a scsi card.

The big irony here is that I have the computer that it was originally used with.   A computer that has no SCSI card.   (Somebody stripped it out, prior to giving it to me.)

xan

jonathon

---

### Post by mips on 2008-10-22
> **jonathonblake said:**
> 
If I can get the drivers,I'll try running it either under WINE, or with Win2K as a virtual OS.  


[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=181&lc=en&dlc=en&cc=us&lang=en&product=77368#](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=181&lc=en&dlc=en&cc=us&lang=en&product=77368#)

---

### Post by gacb on 2010-08-29
> **jonathonblake said:**
> And now that I've gotten rid of the HP SCSI scanners, I discover that there is no Linux support for the HP 4570c.  :(

I thought that SANE worked for every scanner out there.

xan

jonathon

It's probably too late for you, but I have the 4570C up and running flawlessly in both Lucid and Maverick. At first there were a few glitches, but plugging in the TMA seems to have solved that.

---

### Post by fatality_uk on 2010-08-29
> **gacb said:**
> It's probably too late...
This is correct. Generally, reviving posts over a year old is considered necromancy!!! But glad you got it working.

---

### Post by jonathonblake on 2010-08-29
> **gacb said:**
> It's probably too late for you, 

Actually, I still have that scanner on my desk. (My desk is big enough that I can leave that, and a printer I don't use on it, and still have enough room to work at my desk.)

Bleh.  I don't appear to have the power cord for it. Do you know how many volts that input is supposed to be. (I found an online manual, but it didn't include any specifications.)

> I have the 4570C up and running flawlessly in both Lucid and Maverick. At first there were a few glitches, but plugging in the TMA seems to have solved that.

Which packages did you install?
I don't see anything that looks like a driver for it.  :(

jonathon

---

