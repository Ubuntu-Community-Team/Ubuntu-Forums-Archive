---
title: "some general server issues: hardware/ubuntu"
date: 2012-01-07
forum: Server Platforms
---

### Post by badperson on 2012-01-07
Hi,
server admin is definitely not my area of expertise, but I've got a home server that I use to learn on and I've recently had some issues. 

I have a headless system that runs ubuntu server on a quad core amd machine. I have the machine connected to my wireless router via ethernet and log on from my other machines (desktop that dual boots ubuntu and win7 and a macbook) from ssh/putty/whatever. 

I mainly use it for a samba share and to host some webapps that I wrote. Typically I leave the machine on all the time, but when I went away on vacation, I decided to shut it down. 

When I got back, when I started it back up I was unable to log on, so I had to dig in the back and connect it to a monitor/keyboard. I found that I was getting some errors such as "ata1: softreset failed (device not ready)". 

I wasn't sure what they were, from the googling I did it sounded kind of harmless and related to some older packages, so I took the opportunity to run "do-release-upgrade". 

That error went away, but then I started running into some other problems...when I logged onto the server via ssh from my ubuntu desktop, I got a read i/o error...leading me to believe my HD was fried. So I left it off for a few days. 

when I pulled my machine out today, I started it up and got an error in bios, saying that it was starting the machine with a lesser amount of memory. Then it went into the bios setup area. I hit escape and was brought to a new screen (before the grub menu) where I got an error: "error: fd0 read error". 

Then it went into the grub menu and began spitting out some lines before getting to the login prompt, and among them was "mountall: fsck /boot [385] terminated with status 1".

Eventually I got to the logon screen and logged in, and was able to get to the hard drive that I had been unable to access before. So, I backed everything up to another hard drive. 

When I rebooted again, I did not get the error related to the lower memory, but did get the fd0 read error. 

I'm going to review my /etc/fstab and make sure everything is ok, and maybe remount everything. But I suppose my overall question is, how can I best ensure my server runs reliably without these kinds of issues? If the machine were in a colocation I would be totally screwed. Are there steps I should take to make sure I have the best hardware and to set it up optimally for a machine that stays on all the time? 

[also, I realize I need to do a better job documenting the types of issues I come across]


thanks, 
bp

---

### Post by drdos2006 on 2012-01-07
A BIOS error does not sound good. Try opening the box, reseating the memory and rebooting. Use LiveCD and run the memory test.

regards

---

