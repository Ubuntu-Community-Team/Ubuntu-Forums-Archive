---
title: "staring shuts off after 30 seconds"
date: 2010-06-14
forum: System76 Support
---

### Post by jediborger on 2010-06-14
I have hit a strange issue which I have no idea how to deal with. In short as the title says, my starling shuts off after 30 seconds. 

So yesterday I was using it and I suspended it, forgot about it and turned it on today only to have it turn off on me because the battery was dead. This was expected and I have done this before. I left the laptop for a while to go run some errands and after about 4 hours grabbed the power plug and booted it back up. It shut off during boot, which stated it was checking the discs for errors, I presume fsck was running. It keep shutting off at the same point. Next I went to the bios to boot from a usb drive but it shut off while I was in the bios. So my problem is not the hard drive or the ubuntu install. I pulled the battery out and booted with the plug but even just sitting at the bios screen my starling now shuts off after 30 seconds.

Any ideas as to what's going wrong?

---

### Post by macabrem on 2010-06-14
> **jediborger said:**
> I have hit a strange issue which I have no idea how to deal with. In short as the title says, my starling shuts off after 30 seconds. 

So yesterday I was using it and I suspended it, forgot about it and turned it on today only to have it turn off on me because the battery was dead. This was expected and I have done this before. I left the laptop for a while to go run some errands and after about 4 hours grabbed the power plug and booted it back up. It shut off during boot, which stated it was checking the discs for errors, I presume fsck was running. It keep shutting off at the same point. Next I went to the bios to boot from a usb drive but it shut off while I was in the bios. So my problem is not the hard drive or the ubuntu install. I pulled the battery out and booted with the plug but even just sitting at the bios screen my starling now shuts off after 30 seconds.

Any ideas as to what's going wrong?


I'm sure Tom will be here helping you shortly.

I had this problem.  One of the first trouble shooting things you'll want to try is to blow the vents / air intakes out with a can of compressed air.  It *could* be an over heating issue.  Dust in the fans is only one possibility.  

Also, try taking the battery out and leaving it out for like 20 to 30 minutes.  Then put it back in and see if it works better.  I don't know why that might work, but I think I remember seeing that as a thing to try on a previous thread.

---

### Post by isantop on 2010-06-14
I'd try macabrem's suggestions first. It easily could be an overheating issue, especially if it's shutting down in the BIOS.

Also, the battery thing is worth trying. If there's a problem with the electronics anywhere in the computer, leaving it unplugged with no battery in for about half an hour should allow any residual charge to dissipate from the computer. after this, you can try booting again.

---

### Post by jediborger on 2010-06-14
Well unfortunately it is still turning off after both of your suggestions. Seems like the next logical thing is that the internal fan isn't working. I am having a hard time telling though since the fan was not very noticeable to begin with. Maybe I could look into a bios update? Although if the computer shuts off in the process that would make things worse.

---

### Post by macabrem on 2010-06-15
I'm surprised System 76 hasn't said to contact them about this (if it is under warranty).

---

### Post by isantop on 2010-06-15
Try re-seating the battery. Bad and unreliable battery contact could be causing your problems.

---

### Post by dlavi1976 on 2010-06-15
> **jediborger said:**
> I have hit a strange issue which I have no idea how to deal with. In short as the title says, my starling shuts off after 30 seconds. 
 
So yesterday I was using it and I suspended it, forgot about it and turned it on today only to have it turn off on me because the battery was dead. This was expected and I have done this before. I left the laptop for a while to go run some errands and after about 4 hours grabbed the power plug and booted it back up. It shut off during boot, which stated it was checking the discs for errors, I presume fsck was running. It keep shutting off at the same point. Next I went to the bios to boot from a usb drive but it shut off while I was in the bios. So my problem is not the hard drive or the ubuntu install. I pulled the battery out and booted with the plug but even just sitting at the bios screen my starling now shuts off after 30 seconds.
 
Any ideas as to what's going wrong?
 
I had what sounds like the same problem.  When I first got my Starling I had this problem the first time I started it up.  After a number of restarts it started working again.  Then a few weeks ago it happened again.  I sent in the Starling for warranty repair.  I am still waiting to hear as to what the problem is or if they have been able to reproduce it.

---

### Post by jediborger on 2010-06-15
I do not believe it is the battery as the issue still occurs without the battery attached (and the power plug attached). I purchased this about this time last year, so my warranty is probably coming up in a week or so. Figures. At least it waited until the day I got back from school to give me problems.

---

### Post by dlavi1976 on 2010-06-15
> **jediborger said:**
> I do not believe it is the battery as the issue still occurs without the battery attached (and the power plug attached). I purchased this about this time last year, so my warranty is probably coming up in a week or so. Figures. At least it waited until the day I got back from school to give me problems.
 
 
When I had the issue,  I tested it on battery power, plugged in with the battery inserted, and plugged in with no battery.  My conclusion was the same that it was not related at all to the battery.

---

### Post by macabrem on 2010-06-15
I had to send mine for a repair under warranty also.  Talked with Tom.

---

### Post by dlavi1976 on 2010-06-15
Do you know what they did for the warranty repair or what the problem was?  Did they fix it or give you a new machine?  I have not heard yet what the repair folks found or the solution (they have had my computer for 12 days).

---

### Post by jediborger on 2010-06-18
Well now it's working. I can feel the air coming out the side vent so somehow the fan has started working again after sitting in my room collecting dust . . . This is all really weird. I'll see how long it lasts until it starts acting up again.

BTW, I was able run memtest and it complete successfully with no errors.

---

### Post by CrimsonS on 2010-06-20
I've just had what seems to be the same problem occur to my starling. Yesterday, it shut off suddenly as if the battery ran out. Now whenever I try to turn it on, it shuts off as soon as it gets past the boot loader, whether trying to load the ubuntu install, or a live USB.

I've trying the couple of suggestions mentioned here, and no luck yet.

---

### Post by dlavi1976 on 2010-06-20
System 76 has had mine for over 2 weeks and they have not been able to duplicate the problem.  It is interesting that so many people are having the issue.

---

### Post by neophyte_of_linux on 2010-06-20
About a week ago my non-system76 desktop system running 8.04 Hardy Herron suddenly turned off on me.  The first time anything strange like this.  It was exactly like the power went out while the system was up and running.  Something Update related??

---

### Post by dlavi1976 on 2010-06-20
That sounds different.  My shut off then when restarted it shut off again.  I don't think that this is update related because the first time it happened to me was the first time I turned on my Starling when I got it last fall.  It went away until recently.

---

### Post by CrimsonS on 2010-06-20
Just to keep those of you following this thread up to date, the problem went away soon after I posted my last post. I also had a recurring (at least 6 times) problem of the laptop shutting off just after it boots.

I did blow compressed air into it, so that might have solved the problem. Other than that, I'm pretty stumped. Just hope it doesn't happen again too soon

---

### Post by thomasaaron on 2010-06-21
Let us know if it recurs. If re-seating the battery doesn't fix the problem, we usually need to bring it in for repair.

---

### Post by DGer on 2010-06-22
This same thing just started happening to me this morning.  I'm one month past my 1 year warranty.  Purchased mine 5/16/2009.
 
The netbook has worked flawlessly since day 1.  Upgraded to Lucid yesterday, downloaded and installed the latest driver set from System76, verfied everything worked and then shut it down.  First boot this morning shut down after the login screen.  It does this whether battery is installed or not.
 
Is this potentially a software problem?  Can't see myself shelling out for another Starling 1 month outside of warranty.

---

### Post by DGer on 2010-06-23
Update...
 
After powering it on numerous times, it finally booted all the way up and seems to be behaving normally now.
 
Strange.

---

