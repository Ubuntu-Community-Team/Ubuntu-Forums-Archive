---
title: "[SOLVED] Address not found on startup of firefox /  seamonkey"
date: 2008-10-31
forum: Ubuntuzilla
---

### Post by Head4Home on 2008-10-31
Just install SeaMonkey with your script and the install seemed to go ok except for not being able to find some of the download sites.
When I opened the program I received the above error.  Tried remove and reinstall several times but still the same problem.  Next I tried installing Firefox thinking maybe seamonkey had to link to it somehow.  No good either with the same Address not found but from the firefox website this time.  Had to uninstall firefox just to get back on the internet. Thank goodness you uninstall script works well.

I have Ubuntu 8.04-64 bit installed on an AMD64 computer.

Anyone have any ideas about where I should start looking for a resolustion to this problem?  I'm sure its just some kind of beginner error or something like that.

Thanks in advance.

---

### Post by Head4Home on 2008-11-01
Well, looks like I may have figured out a fix, or at least a work-around.

I discovered that seamonkey was not finding my name server in my router.  I could connect to web sites by entering their IP addresses but not by URL.  Ran across a  post on the firefox website that mentioned something about sometimes IPv6 causes problems and to try disabling it in the seamonkey config file.  I did.  I can now connect normally.

Still haven't determined whether the problem lies in my older D-Link router, in seamonkey, or in Ubuntu configuration.  I do remember that I never did get my Ubuntu to work with static IP addresses.  It will only work with dynamic IP.

Anyway I just wanted to let everyone know the fix in case it could help someone else.

---

