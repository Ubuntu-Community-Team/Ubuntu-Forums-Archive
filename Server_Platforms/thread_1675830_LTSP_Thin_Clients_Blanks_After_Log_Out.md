---
title: "LTSP Thin Clients Blanks After Log Out"
date: 2011-01-26
forum: Server Platforms
---

### Post by dstudio101 on 2011-01-26
Hi, all!

Just started learning the ropes with LTSP Ubuntu (10.10)  Installed successfully and run successfully with some thin clients.

However, I have some thin clients -- different hardware spec than the working ones (Intel P4, 256MB)  Using gPXE netboot.

I could successfully boot this and login for the first time -- every power up.  However, when I logout -- it just show a blank screen.

oh, yea -- I had to specify in the lts.conf that this specific computers need this:
XSERVER=vesa

whereas the other working -- I mean the log out return them to the login window -- doesn't need the XSERVER=vesa parameter.

How to troubleshoot?

Thanks!

---

### Post by dstudio101 on 2011-01-27
Additional trouble:
This thin client hang when rebooting -- needed to wait - 30min or so before I could boot it up normally again.

---

### Post by dstudio101 on 2011-02-06
I see, this is really a problem, isnt' it?

---

### Post by dstudio101 on 2011-02-21
How do I troubleshoot a thin client that hangs after a logout?
Where can I find logs for this?  So I could trace any errors that may have occured?
I've posted some details above about the thin client.

I believe it's a fairly modern computer as it is a Pentium 4 2.x GHz cpu with 256 MB ddr400 RAM.

I can boot normally when powering up.  Rather the login screen will show after a power up. - There's also this configuration option I've set up to make the display work: XSERVER=vesa -- placed in lts.conf.

Thanks for any reply.

---

