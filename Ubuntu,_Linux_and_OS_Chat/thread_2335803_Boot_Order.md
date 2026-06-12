---
title: "Boot Order"
date: 2016-09-01
forum: Ubuntu, Linux and OS Chat
---

### Post by KitchM on 2016-09-01
This has been bugging me for some time now, and I am hoping someone knows the answer.

   Why is their no precision in the software when a computer is booting up the operating system?  Sometimes one things starts first, and sometimes another.  Sometimes items, like the the pulse audio system tray, starts up and sometimes it doesn't.  Sometimes an internal drive shows up as an icon on the desktop and sometimes it doesn't.
What's going on here?

Thanks.

---

### Post by user1397 on 2016-09-02
Not sure, doesn't happen to me.  If anything bugs out I usually just restart and it solves the problem.  Perhaps you have some deeper issues with your hardware?  Hard to say.

---

### Post by KitchM on 2016-09-02
Even what you might describe as a "bug" is a serious flaw.  Computers always do the same thing over and over unless acted upon by humans thru programming, or as you say, hardware issues.  But even with hardware issues, one would expect the exact same problem continuously, regardless of number of reboots.

As an example of odd programming, I just installed audio-recorder and for some reason it loads every time the system comes up to the desktop.  That is non-standard programming, and it forces the user to close it every time.

---

### Post by buzzingrobot on 2016-09-02
Processes and services that should run at startup and do not run are legitimate problems. If that system is configured correctly, they may be bugs.

Processes and services appearing to launch in a different sequence from boot to boot may be an effect of the software used to list them.  Some processes run, finish, and end.  Some processes launch and remain active until that session is shut down.  Adding, removing, or changing processes or services, including drivers, can impact the boot sequence.  E.g., one process may require the successful launch of another. A default Ubuntu install, like other desktop Linux systems, does not list processes/services as the kernel starts them when it boots.

Programs  -- applications installed by a user -- can be set to launch when a new session begins (at boot or when that user log ins). If an application that should not launch then is, in fact, launching, it's likely due to an error in how it was installed, either by the user or in that app's installation routine.

---

### Post by user1397 on 2016-09-02
Have you looked at your startup services?

---

