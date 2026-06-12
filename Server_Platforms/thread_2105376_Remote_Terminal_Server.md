---
title: "Remote Terminal Server?"
date: 2013-01-15
forum: Server Platforms
---

### Post by sixstorm on 2013-01-15
Hello all.  I'm doing a little experiment for my job and would like your input.

I work for a technical school and am trying to setup a backup/remote way for our faculty to login remotely and check their email/grades/documents/etc.  The Windows admin in me says "Setup a terminal server!" but I want to know what the best solution for the Linux side is.  Currently, faculty can VPN in and run the applications they need from their own computers, but I'm finding that they upgrade or change laptops a lot and it involves me having to reinstall applications quite often.

I see that LTSP is available but seems to be geared more toward thin/thick clients, not just for remote RDP access.

TL;DR:  I would like my users to "RDP" (VNC I guess?) into an Ubuntu box and access basic Office and grading apps.  What is the best option for Linux?

---

### Post by Vegan on 2013-01-15
Most academic shops I have assisted use console linux and students can FPT or Telnet into their folder

world+dog all over web mail, I use microsft'/s mail but gmail is free but I have seen a lot of issues with linux

---

### Post by sixstorm on 2013-01-16
Any other ideas on this?  

If it's a last resort, I'm just going to setup a Windows 7 VM up on the virtual server and have open access to the faculty.  Would just rather have a Linux terminal server style solution instead.

Or what about a web interface where they can just run one application under wine?

---

### Post by collisionystm on 2013-01-16
You can install xrdp and use the native windows remote desktop to access ubuntu. It should function as a terminal server because each xrdp session will use its own X session.

---

