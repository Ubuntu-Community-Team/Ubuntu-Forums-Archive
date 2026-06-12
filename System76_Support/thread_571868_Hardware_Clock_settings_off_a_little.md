---
title: "Hardware Clock settings off a little"
date: 2007-10-09
forum: System76 Support
---

### Post by steveneddy on 2007-10-09
I was having a problem booting and getting Grub to auto start and stuff today

See [this post]("http://ubuntuforums.org/showthread.php?t=571833")

and I noticed that the clock in the BIOS is off, fast actually, by 6 hours, and before I changed it, when I was having the problem in the post mentioned earlier, it was stuck at 7:am at each boot.

What could be causing this problem?

I have a Serval Performance type 1, Core 2 Duo, 2 Gig RAM, nVidia video.

And while looking at this today, do you think that you guys installed a bluetooth chip in my machine, because I didn't order one but I thought I saw the bluetooth module under the hard drive today while snooping around in the case.

Cheers - 

:popcorn:

---

### Post by steveneddy on 2007-10-10
OK - for those of you keeping score at home -[COLOR="Red"] today[/COLOR] when I run **hwclock** and **date**, they both match up.

What could have caused this problem yesterday?

:popcorn:

---

### Post by thomasaaron on 2007-10-11
Not sure.
Maybe a lower surge?

That's an interesting fix, though, on your other post. I've not heard of that one before.

---

### Post by steveneddy on 2007-10-11
It is a cool little software app that is in the repos, and after you install it, the log files are in /var/log/bootchart.

It literally gives you a graphical chart of the items that are starting up at boot time and how much time they are using.

That is actually how I found the problem and started searching the forums for hwclock issues.

***************

I was thinking about that day, and I think that I was shutting down the laptop to take it off site and during the power down period I unplugged the ac power, and that may have started something drastic that day.

That night, I unplugged the machine from any outside power source, powered down completely and checked it in the morning. I thought that the battery may have needed some use since it stays plugged in most of the time. You never know. I think that the BIOS and the OS were in sync by the morning and everything was OK after that.

:popcorn:

---

