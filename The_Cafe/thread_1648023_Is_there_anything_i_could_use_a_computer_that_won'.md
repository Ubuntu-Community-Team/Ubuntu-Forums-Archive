---
title: "Is there anything i could use a computer that won't boot from hard drives for?"
date: 2010-12-18
forum: The Cafe
---

### Post by Macfunky on 2010-12-18
Basically it's a 2ghz computer that was working fine for a long time, then all of a sudden it wouldn't boot from any hard drive with any operating systems on them. I have tried changing setting in the bios but nothing. After having put up a question regarding it on a few different forums and asking I.T. friends i have come up with nothing and it's still lying idle. It's a shame to see it not getting any use. It still boots from live CD's so it's not knackered yet. Is there any purpose for which it would serve nicely if i continue to not be able to find out why it won't boot up from hard drives? Anyone have any ideas? By the way it doesn't support booting up from flash drives. I look forward to any suggestions :)

---

### Post by Spice Weasel on 2010-12-18
Have you tried using a boot cd to get it to boot from the hard disk?

---

### Post by Macfunky on 2010-12-18
> **Spice Weasel said:**
> Have you tried using a boot cd to get it to boot from the hard disk?

No, how would i go about that?

---

### Post by Spice Weasel on 2010-12-18
You know how Live CDs have that menu where you can select to boot from hard disk? Try that. AFAIK you need to press a key (ESC or one of the F keys) to get to the menu in Ubuntu when it boots the CD.

---

### Post by Macfunky on 2010-12-18
> **Spice Weasel said:**
> You know how Live CDs have that menu where you can select to boot from hard disk? Try that. AFAIK you need to press a key (ESC or one of the F keys) to get to the menu in Ubuntu when it boots the CD.

Thanks, I will try this out later and let you know how it goes.

---

### Post by Linux_junkie on 2010-12-18
It sounds like the HD has failed and if it has then it doesn't matter what you do it won't work.  

When I bought my laptop (second hand) it came with Windows Vista and after booting up it would not recognise the HD and on other occasions it did.  When on one occasion it did "see" the hard disk I formatted it and installed Ubuntu and it has worked fine ever since.

To this day I still do not know whether it had a boot sector virus that was causing the problem or if there was a problem with the system files.

If you can access the hard disk try and format it and install (or re-install) your operating system.

---

### Post by cgroza on 2010-12-18
If it won't boot any HDDs maybe its something wrong with the controler?

---

### Post by grahammechanical on 2010-12-18
Have you tried re-setting the BIOS to its default settings? The BIOS settings program may have a function that lets you do this. There may be a jumper on the motherboard that you can change the link of that will take the motherboard back to the factory settings. You can try updating the BIOS if it is a flash BIOS. You can even try removing the little battery on the motherboard and leaving it out for a while.

My motherboard user guide says this:

> Jumper Clear RTC RAM (CLRTC) This jumper allows you to clear the Real Time Clock (RTC) RAM in CMOS. You can clear the CMOS Memory of date, time, and system parameters by erasing the CMOS RTC RAM data. Information is then given on how to proceed. You should research this feature of your motherboard. Take heed of the warnings. But what do you have to lose? If all else fails you could buy a new motherboard and use parts from the old system.

Regards.

---

### Post by K.Mandla on 2010-12-18
> **Macfunky said:**
> Is there any purpose for which it would serve nicely if i continue to not be able to find out why it won't boot up from hard drives? Anyone have any ideas? 
Try something like PLoP or Smart BootManager and see if it will start up that way. Or maybe you already tried that. ... :|

Provided it can still *access* a hard drive, you could use it as an in-house file server, with something like [FreeNAS]("http://freenas.org/").

You could use it to run something like Slitaz, which operates completely in memory and saves configurations, etc., to a USB disk or different drive.

There are some other things you could try. ;)

---

### Post by donkyhotay on 2010-12-18
The previous suggestions are all good ideas. Assuming you can't get it working with one of the recommendations above the only other use I can think of for a computer that won't boot would be:

1. paperweight

2. parts for a frankenputer

3. something to dissect to learn more about computers

4. paperweight

5. doorstop

6. impromptu hammer

7. paperweight

8. white elephant gift for someone you don't like

9. target for target practice

10. have I mentioned paperweight already?

If you don't like any of those suggestions I personally would just recycle the thing myself. Of course if you can get it working then that would be best.

---

### Post by Macfunky on 2010-12-18
> **cgroza said:**
> If it won't boot any HDDs maybe its something wrong with the controler?

It won't boot any drive at all. Any drive or any operating system.

---

### Post by Macfunky on 2010-12-18
> **grahammechanical said:**
> Have you tried re-setting the BIOS to its default settings? The BIOS settings program may have a function that lets you do this. There may be a jumper on the motherboard that you can change the link of that will take the motherboard back to the factory settings. You can try updating the BIOS if it is a flash BIOS. You can even try removing the little battery on the motherboard and leaving it out for a while.

My motherboard user guide says this:

 Information is then given on how to proceed. You should research this feature of your motherboard. Take heed of the warnings. But what do you have to lose? If all else fails you could buy a new motherboard and use parts from the old system.

Regards.

I re-setted the BIOS. No luck there either

---

### Post by Khakilang on 2010-12-18
Why don't you change the motherboard. I am sure there is some available from eBay. Worst come to worst boot from external USB hard disk.

---

### Post by grief -l on 2010-12-18
I use TinyCoreLinux on a live CD, and the Home file system is saved to an 8Gig USB. The more memory you have the better. Don't need a clunky disk.

---

### Post by handy on 2010-12-18
It has a worthwhile amount of CPU power.

Why not buy a controller card that you install in an expansion slot?

I have done that in the past with motherboards that have lost their HDD controller & it worked fine.

I think I used one made by Promise, which was quite cheap & that was many years ago.

---

