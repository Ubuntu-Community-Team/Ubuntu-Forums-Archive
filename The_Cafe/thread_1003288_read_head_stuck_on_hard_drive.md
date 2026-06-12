---
title: "read head stuck on hard drive"
date: 2008-12-05
forum: The Cafe
---

### Post by wilbbe01 on 2008-12-05
I have a hard drive of a friend.  Like most people he didn't think to backup his data.  When I give the hd power I can hear the arm trying to move out.  It sounds like it is getting stuck, and that continues for a few minutes until it gives up.  Does anyone have any ideas how to get that broken loose long enough to get his data off?  A colleague of mine claims he has heard of people who are able to get data off if they remove the cover of the drive.  To me this seems like suicide while injured, but maybe it would work to relieve whatever pressure is stopping that arm from moving, and keep it unstuck long enough to let me get all the data off.  Thanks for any suggestions.

---

### Post by CholericKoala on 2008-12-05
Do you give it power through usb?  I know that mine makes loud clicking noises if it does not receive enough power.

---

### Post by wilbbe01 on 2008-12-05
Yeah, it has enough power.  It is from a laptop, it was clicking inside the laptop excessively (as though it sounds stuck).  Now I have it sitting on my tower powered up there.

---

### Post by CholericKoala on 2008-12-05
I've had that problem a lot but it was never attributed to the hard drive itself.  It works on some of my operating systems, and some it doesnt.  One of my usb cables would work and another would not.  The one with a split end so it can be plugged in twice into a tower gave it the umph it needed to work for me.  I would suggest trying it on different computers.  Good Luck!

---

### Post by wilbbe01 on 2008-12-05
It has the same problem on multiple computers.  I only have it plugged in to power so operating system shouldn't matter, and wouldn't with what this drive is doing anyway.  Any other ideas anyone?

---

### Post by psusi on 2008-12-06
You can try paying one of those data recovery labs $1000 or whatever they are asking these days and hope they can pull it apart and get something out of it, or if the data isn't worth that much to you, write it off and consider it a lesson learned about keeping regular backups.

---

### Post by wilbbe01 on 2008-12-06
I don't need the lesson, my friend does.  I suppose if I do manage to get the data off of it I suppose it would just teach him not to back it up in the future.  I might try that.  Or maybe I'll take the cover off of another drive I dont' need and see if it still works, and if it does I'll take the cover off of this drive too.

---

### Post by smoker on 2008-12-06
you could try sticking it in the freezer overnight, in a airtight bag of course. it may work long enough next day for you to get the data off:
[http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html](http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html)

best of luck

---

### Post by az on 2008-12-06
> **wilbbe01 said:**
> I have a hard drive of a friend.  Like most people he didn't think to backup his data.  When I give the hd power I can hear the arm trying to move out.  It sounds like it is getting stuck, and that continues for a few minutes until it gives up.  Does anyone have any ideas how to get that broken loose long enough to get his data off?

I do data recovery.  I only use software means.  If a drive is not able to identify itself to the computer as it powers up, there is nothing that can be done from a software point of view.

If the drive is not recognized wither by the bios (if connected directly to the motherboard) or by the kernel (if connected by removable storage), the hardware is damaged.

In that situation, the click you are hearing is commonly called "the click of death" and it can be caused by a few different things, all of which can *only* be dealt with by opening up the drive and fixing the problem, if thats even possible.

In short, you can't open up a drive at home and expect to be able to fix the problem.  The heads are not "stuck", they are unable to read information on the disk that the drive's internal environment need to boot up (e.g. firmware).  The heads try a set number of times to read this data and give up -  that's the clicking you hear.

Not to mention it's recommended (although not strictly necessary) to open up a drive in an environment free of dust particles known as a level 100 clean room.
  
So, when a customer approaches me with a drive such as yours, I refer them to someone else who can repair hardware and who charge up to 100 times more than I do.  I don't even try to look at the drive since I don't charge any fee if I don't recover any data.

---

### Post by mips on 2008-12-06
> **az said:**
> I do data recovery.  I only use software means.

az, mind sharing what utilities you use and any methodologies etc?

I've done data recovery for a few people but usually end up using some form of windows utility. If there is a hardware issue I send it off to a datarecovey company, they give me a quote before they proceed though.

---

### Post by Dr Small on 2008-12-06
> **smoker said:**
> you could try sticking it in the freezer overnight, in a airtight bag of course. it may work long enough next day for you to get the data off:
[http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html](http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html)

best of luck
I plan to try that on one of my hard drives one day.

---

### Post by Polygon on 2008-12-06
> **mips said:**
> az, mind sharing what utilities you use and any methodologies etc?

I've done data recovery for a few people but usually end up using some form of windows utility. If there is a hardware issue I send it off to a datarecovey company, they give me a quote before they proceed though.

photorec is a good one (i believe you have to install some other program to get this one tho in the ubuntu repos). just be sure to have a drive with lots of space available (and run photorec from that drives directory, aka like /media/DISK, cause its going to be dumping all the files it recovers into the directory its running from!) Also, be sure to run it from a folder as it just dumps random files it recovers, without any folder heirarchy, but it worked for me when i totally trashed a partition doing something stupid and no utility could even see the partiton, let alone repair it.

---

### Post by az on 2008-12-06
> **mips said:**
> az, mind sharing what utilities you use and any methodologies etc?

I've done data recovery for a few people but usually end up using some form of windows utility. If there is a hardware issue I send it off to a datarecovey company, they give me a quote before they proceed though.

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by mips on 2008-12-06
> **az said:**
> [http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I will have a look and try to install all the software in Arch at some point.

---

