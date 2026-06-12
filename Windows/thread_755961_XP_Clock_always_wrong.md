---
title: "XP: Clock always wrong"
date: 2008-04-15
forum: Windows
---

### Post by Thelasko on 2008-04-15
I couldn't find an answer on Google so I figure I will try the folks here since I have found everyone to be very helpful.

My fiancée is a Windows XP user (I think it's home edition) and her clock is constantly wrong.  I don't think it's the CMOS battery.  She has tried synchronizing it to two separate internet servers and within a few minutes/hours it has the wrong time again.  We are talking **days** off sometimes more than a month.  Anybody have some suggestions?

---

### Post by Chiko2008 on 2008-04-15
Is the date correct?

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by lswest on 2008-04-15
have you tried setting it manually and disabling the automatic checking of an internet server?  If it occurs again, it's either a software or hardware issue.

---

### Post by Thelasko on 2008-04-15
No, the date is wrong too

---

### Post by Thelasko on 2008-04-15
@lswest
I should have thought of that.  I just cant figure out why the internet server would cause the problem.

I'll try it when I get home.

---

### Post by Chiko2008 on 2008-04-15
Try to manually correct the clock and the date and disable the option to automatically update the clock.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Battie on 2008-04-15
Is it ahead or behind?  If it seems to be losing time, it could be the CMOS battery.  I haven't heard of that happening in a while, but it makes sense.

I'm pretty sure the BIOS keeps time independent of Windows, so see if the time there is also very wrong.  If not, you can rule out hardware issues.

---

### Post by lswest on 2008-04-15
> **Thelasko said:**
> @lswest
I should have thought of that.  I just cant figure out why the internet server would cause the problem.

I'll try it when I get home.

Well, might be that the servers you connected to are downloading info for the wrong timezone, or maybe the connection is losing packets and the time isn't updated regularly, file is corrupted or so that's required to connect, etc.  In any case, the only internet server i use to update from is the one from my school, otherwise i just do it manually.  But yeah, sometimes the simple things work, and if it doesn't, at least you know it's not likely something you can fix without opening up the comp.

---

### Post by Shazaam on 2008-04-15
Make sure the bios time and date are set correctly. You might want to synchronize an external time source (using a watch/clock) with Windows and then check to see if the bios time is off along with Windows.

---

### Post by Thelasko on 2008-04-17
It's not the internet server.  I still have to try the BIOS clock.  Unfortunately, she is usually using the machine when I am at home.

---

### Post by lswest on 2008-04-18
i just noticed that the same thing happened on my XP system on my laptop (don't usually use it), but once i told it to update from the internet server again it worked fine, and if i set it manually it works too, so i dunno, maybe it's a bug in some update?  Never noticed it before (probably because i use XP like once every 4 months at the most XD)

---

### Post by Thelasko on 2008-05-28
I finally got around to playing with the BIOS.  It's quite strange, it will let you set the clock, but won't display the time.  I set the time manually in the BIOS and booted the computer.  When it finished booting it had the correct time, and then started drifting again.  Basically that didn't tell me anything.

---

### Post by smoker on 2008-05-28
> **Thelasko said:**
> I couldn't find an answer on Google so I figure I will try the folks here since I have found everyone to be very helpful.

My fiancée is a Windows XP user (I think it's home edition) and her clock is constantly wrong.  I don't think it's the CMOS battery.  She has tried synchronizing it to two separate internet servers and within a few minutes/hours it has the wrong time again.  We are talking **days** off sometimes more than a month.  Anybody have some suggestions?

how do you know it is not the cmos battery, unless you've tried a replacement?
also, is it a laptop? some laptops don't have a cmos battery, but have a small rechargable battery that does the same job. if it isn't holding a charge, it will be losing time, and need replaced. if it is a laptop, download a manual from the makers support site, and check which type of battery it takes. if it is a pc, then there's little cost involved in changing the cmos battery for a new one.

---

### Post by Thelasko on 2008-05-29
It is a laptop and I checked Dell's website and didn't find anything about changing the CMOS battery.  Off the top of my head it's an Inspiron 2200 (not at home right now to check).

---

### Post by Thelasko on 2008-05-29
I found [the instructions]("http://support.dell.com/support/edocs/systems/ins2200/en/SM/coincell.htm#1111212").  They call it a "coin cell battery" for some reason.

---

### Post by smoker on 2008-05-29
> **Thelasko said:**
> I found [the instructions]("http://support.dell.com/support/edocs/systems/ins2200/en/SM/coincell.htm#1111212").  They call it a "coin cell battery" for some reason.

yeah, that looks like a smaller version of a normal size cmos battery, and as usual with a laptop, you have to take the thing apart to replace it:confused:

---

### Post by msidhard on 2008-05-29
Just Disconnect From Net And Set The Clock Manually.  Check If It Works Correctly. He It Worked Perfectly Then Change The Time Zone Settings In Date And Time Option In Control Panel . Then Connect To Net And Enjoy.

---

### Post by Thelasko on 2008-05-29
> **msidhard said:**
> Just Disconnect From Net And Set The Clock Manually.  Check If It Works Correctly. He It Worked Perfectly Then Change The Time Zone Settings In Date And Time Option In Control Panel . Then Connect To Net And Enjoy.

I already tried that.  It was posted on the first page.

---

### Post by Thelasko on 2008-06-05
New development:
After reviewing an IM conversation she had, she discovered that the clock is stuck in a one hour loop.  For example, if she sets the clock to 4:05pm it will run fine for an hour.  When the clock gets to 5:04pm the next time it displays is 4:05pm.  This repeats over and over.

---

### Post by Thelasko on 2008-06-05
It appears to be similar to [this problem]("http://groups.google.com/group/alt.sys.pc-clone.dell/browse_thread/thread/1bde99771b7bd3d1/23ce434802f83e40?lnk=st&q=dell+clock+problem#23ce434802f83e40").  The page dates back to 2000 but this is a pretty old machine (Pentium III).  It could be related.  However, my fiancee's machine isn't behind one hour, it loses one hour and keeps losing more hours every hour.

---

### Post by Thelasko on 2008-06-05
Dell has removed documentation of this problem from their website.  However, I did find out how to fix it from [this site]("http://www.ahinc.com/wxp.htm").  In the command prompt type:
```
Net stop w32time
w32tm /unregister
w32tm /unregister
w32tm /register
Net start w32time

```

---

### Post by pricetech on 2008-06-05
Will your girlfriend let you run a live CD of Ubuntu, or Puppy, or whatever to isolate whether it's hardware or software ??

---

### Post by Thelasko on 2008-06-05
> Will your girlfriend let you run a live CD of Ubuntu, or Puppy, or whatever to isolate whether it's hardware or software ??
Good idea, if the fix I posted above doesn't work, I'll try that.

---

### Post by michaelzap on 2008-06-05
I had some clock weirdness with XP when I had my Gutsy installation. The clock would always be six hours ahead, and when I would reset it (in XP), the next time that I would reboot it would be hours ahead again. It turns out that my BIOS time was being set to GMT instead of my local time, and XP couldn't deal with that.

I don't use XP much so I didn't really try to figure out what was going on or why, but when I recently did a fresh installation of Hardy it asked me if I wanted the BIOS time set to GMT or my local time (and helpfully mentioned that this might be necessary for some other operating systems). At which point my brain made an "Ohhhhhhhhhhhhhh" sound and I checked the option to use local time. Since then XP and Ubuntu both have the correct time.

I'm not sure how you can change this after installation, but I bet a forum or Google search would turn up the answer.

---

### Post by Thelasko on 2008-06-05
@michaelzap I am aware of that issue.  Her machine only runs Windows at the moment, so the time zone issues shouldn't be a problem.

---

### Post by Thelasko on 2008-06-23
Update: I tried running the "w32time" code I posted previously, it seemed to fix it for a little while, but it came right back.  

I have no problems with the clock while running a Xubuntu Live CD.  I am also, under no circumstances, allowed to permanently install Linux on her machine.

---

### Post by ComputerGeek31618 on 2008-06-24
Just so you know, the sync clock feature almost certainly won't work.  It's a windows-wide problem.  I'd go into the BIOS, set the clock correctly, then set the time zone from windows (and clock if necessary) if there is a clock problem.

---

### Post by Thelasko on 2008-06-25
If i understood your post correctly, I already tried setting the clock from the BIOS.  It didn't help.

I'm thinking I have to crack it open and change the battery.  I'm not a big fan of opening up laptops.  Especially since it works otherwise.

---

### Post by ComputerGeek31618 on 2008-06-25
Would a low CMOS battery affect the hardware clock?  (and would it be run down in that particular computer?)

New thought.  There may be an update that changes clock/calendar settings.  When was the last time Windows was updated?  (or will an inaccurate clock prevent updates?  Ooooh, hmmmm.)

---

### Post by Thelasko on 2008-06-26
The machine has been updated several times since this thread was started.  Yes, the machine won't update if the clock doesn't move past the second Tuesday of the month.  If I reset the clock or reboot the machine it will update.

The funny thing is, using network time is useless because it relies in the system clock to schedule the next time the system clock is set.

---

