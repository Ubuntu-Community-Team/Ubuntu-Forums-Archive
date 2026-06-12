---
title: "Server crashed! Malicious?"
date: 2011-08-02
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-08-02
Hi guys.
I have a ubuntu 11.04 LAMP server at home.

Its runnign a few small sites on a drupal CMS.

This morning I found none of the sites were responding.
The server itself sounded like it was thrashing the hard drive.

It wasnt responding to the FTP client or SSH connections.
Web pages just sat there like they were loading very slowly but never actually loaded.

How can I find out what went wrong. I dont have a massive amount of experience with linux, particularly the server variant.

Its worried me a little that the drupal report shows several page not found errors like someone (a bot maybe) was trying to see what php setup files they could access.
I've attached a pic to show what I mean.
These all come from the same IP address.

---

### Post by ian dobson on 2011-08-02
Hi,

Looks like a scripting bot that's just looking for standard scripts/holes in the system.

What hardware are you running the server on. I quite often get hit by script bots, and my server doesn't miss a beat. I'm running on a somewhat over speced box (SandyBridge 2600,16Gb ram, Dual Gbyte lan, 6Tb RAID array) which I use for heavy duty data processing/Video recording and processing.

Regards
Ian Dobson

---

### Post by bigmonmulgrew on 2011-08-02
its an athlon x2 240e
3 GB of RAM
250GB WD HDD
GB LAN (although the current router only supports 10/100)

The server is only used to host a few small sites and to occasionally backup important files to.

---

### Post by bigmonmulgrew on 2011-08-02
How do I know if it found a hole in the system? I'd like to fix it if it found one

---

### Post by ian dobson on 2011-08-02
Hi,

If your server is hacked, then it's hard to fix as you can't trust any application/os installed on the system.

I just keep the system uptodate doing updates often and early.

Regards
Ian Dobson

---

### Post by tgalati4 on 2011-08-02
Check all of the files in /var/log.

Install fail2ban

sudo apt-get install fail2ban

Check that your UPS is working properly.  Yank the plug from the wall (or better, throw the breaker--so the ground says connected) and time how long your machine runs.  You need at least 10 minutes of run time to be safe.

If you are not running an UPS, then you should be.

---

