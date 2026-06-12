---
title: "Linux and wireless"
date: 2012-04-04
forum: The Cafe
---

### Post by Lloydb39 on 2012-04-04
Thought I'd share this for others. I was given an old Dell Dimension 4600 so I put on Ubuntu 11.10, replacing Windows XP. Worked fine but I had no wireless card so I bought a Belkin N300. Wouldn't install from the CD so I started reading and getting wireless to run on Linux sounded horrendous. Contacted Belkin and they assured me it wouldn't work. Finally, in desperation, I copied the driver files from the CD to my computer and stuck the device in a USB port. Connected to my home network right off and it runs great! Final trick was to get Thunderbird working via AT&T, but I got that done. I'm spending another $40 for an extra gig of memory but my total cost for a fully operating, reasonably powerful computer will be $80. I'm starting to like open source....

---

### Post by nothingspecial on 2012-04-04
Not a support request.

Moved to the cafe.

---

### Post by coffeecat on 2012-04-04
> **Lloydb39 said:**
> I copied the driver files from the CD to my computer and stuck the device in a USB port. Connected to my home network right off and it runs great!

The driver files on the CD would be Windows ones, so the device probably would have worked right off in Ubuntu anyway!

Good luck! :)

Out of interest, where did you copy them to? What were the file names and to which folder?

---

### Post by Lloydb39 on 2012-04-05
net8192su.cat/.inf/.sys and I put them in a drivers folder that I created in home

---

### Post by nothingspecial on 2012-04-05
Are you using ndiswrapper?

---

### Post by Lloydb39 on 2012-04-05
I'm not sure. I have it, but I don't think I did anything to invoke it....

---

### Post by doorknob60 on 2012-04-05
> **Lloydb39 said:**
> I'm not sure. I have it, but I don't think I did anything to invoke it....
Then copying those drivers from the CD didn't do anything, it should have worked by just plugging it in. 99% of the time the CDs that come with hardware won't do you any good under Linux, just plug it in and see what happens :popcorn:

---

### Post by wolfen69 on 2012-04-06
> **Lloydb39 said:**
> I'm not sure. I have it, but I don't think I did anything to invoke it....

Like others have said, just copying files over won't do anything. Without "invoking" ndiswrapper and specifically setting it up to use those files, it would do nothing. After you install ubuntu, just go to "Additional Drivers" in your system, and check for any drivers you may need. (be plugged into a router/modem first)

---

### Post by coffeecat on 2012-04-06
Just to add to what others have said and to go back to what you said in your OP:

> **Lloydb39 said:**
> I started reading and getting wireless to run on Linux sounded horrendous.

You probably found a lot of dated information and/or unnecessarily complicated howtos on personal blogs. Most wireless cards "just work" in Ubuntu with the inbuilt drivers, or as wolfen69 mentions, you simply need to install proprietary drivers with the Additional Drivers utility for some Broadcom cards. In fact I find configuring wireless with Network Manager in Ubuntu far more straightforward than in Windows - even Windows 7. Admittedly there are a few wireless chipsets that are problematic in Linux, but if you are not using ndiswrapper then those files you copied are simply sitting unused in a sub-folder in your home folder.

---

### Post by Lloydb39 on 2012-04-06
Thank you all. My original mistake probably was not plugging the adapter into the USB port earlier, but after the CD failed on auto play I never went to that step until after trying to do research. More confusion was added by talking to Belkin tech. But I'm rolling now and I know more than I did.
















th

---

