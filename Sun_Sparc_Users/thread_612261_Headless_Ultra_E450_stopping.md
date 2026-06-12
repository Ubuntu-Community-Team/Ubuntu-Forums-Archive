---
title: "Headless Ultra E450 stopping"
date: 2007-11-13
forum: Sun Sparc Users
---

### Post by tizroc on 2007-11-13
I just threw in 4 new 18 gig HDDs(no seagates) to test Ubuntu server on sparc. The install 7.10 went without a hitch and set LAMP, and OpenSSH default server packages.

However (I don't have the exact time pinned down) after some inactivity the system breaks out to the OBP. It starts right back up with a normal go, and there appear to be no ill effects. It is almost like the powersave in Solaris, but I cannot find anything equivenant in Ubuntu.

Quad 400s, 4 gigs plain jane no other cards. As previously stated running headless. Only messages around the time are as follows right after I start, but there doesn't even seem to me any time loss in the logs.. Just all services are externally un-responsive, until you tell it to go. There are TONS more of those --Mark-- entries durring what appears to be the downtime.

Nov 13 06:13:56 QueenMab -- MARK --
Nov 13 06:25:26 QueenMab syslogd 1.4.1#21ubuntu3: restart.
Nov 13 06:53:56 QueenMab -- MARK --
Nov 13 07:13:56 QueenMab -- MARK --
Nov 13 07:33:56 QueenMab -- MARK --
Nov 13 07:53:56 QueenMab -- MARK --
Nov 13 08:13:56 QueenMab -- MARK --
Nov 13 08:33:56 QueenMab -- MARK --
Nov 13 09:09:47 QueenMab kernel: [41918.627338] eth0: Happy Meal out of receive descriptor
s, packet dropped.


:confused:
Thanks
Tizroc

---

### Post by tizroc on 2007-11-14
Well the cause is found, although the reason is still unclear.  As this does not occur on Solaris, RH, or any other flavor of NIX that has been used. Only on Ubuntu.

When the latop monitoring the health through the serial port goes into power save, it appears to drag the e450 with it. To me this is a wierd reaction, however since I have stopped performance monitoring ON the box, all services had remained up.

Anyone see anything similar, or know why the system believes it has recieved an alt-b (break) from tera term while going into power save mode? Yet only breaking out on ubuntu?

Cheers.
-Forest
](*,)

---

### Post by drosky on 2007-11-14
> **tizroc said:**
> Well the cause is found, although the reason is still unclear.  As this does not occur on Solaris, RH, or any other flavor of NIX that has been used. Only on Ubuntu.

When the latop monitoring the health through the serial port goes into power save, it appears to drag the e450 with it. To me this is a wierd reaction, however since I have stopped performance monitoring ON the box, all services had remained up.


On an RS-232 interface, anytime the receive data line is held low for longer than a word time, this is interpreted as a "break" signal.  When your laptop goes to sleep, the RS-232 TD line is probably going to zero forever, causing the the other machine to see a physical break signal.

Ubuntu must process the break differently than Solaris.

Dave

---

### Post by tizroc on 2007-11-14
Thank you Dave, I had an idea that it was some communication that must be sent. I wasn't sure how it worked until you explained. I am still puzzled as to why each would act so differently, and if there is a standards and practice or RFC on the communication.

I do appreciate the information.
-Forest
8-[

---

### Post by mips on 2007-11-17
> **tizroc said:**
> Thank you Dave, I had an idea that it was some communication that must be sent. I wasn't sure how it worked until you explained. I am still puzzled as to why each would act so differently, and if there is a standards and practice or RFC on the communication.

I do appreciate the information.
-Forest
8-[

Log it as a bug on launchpad as that behaviour does not seem correct.

---

