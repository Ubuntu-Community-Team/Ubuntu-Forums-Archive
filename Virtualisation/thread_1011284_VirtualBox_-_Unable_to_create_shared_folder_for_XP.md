---
title: "VirtualBox - Unable to create shared folder for XP."
date: 2008-12-14
forum: Virtualisation
---

### Post by Swerve1000 on 2008-12-14
Hi,

I've been trying for two days now to configure a client XP SP2 virtual machine to gain access to a shared folder on my Ubuntu 8.10 host machine.

None have been worked for me which has been extremely frustrating.

So, I have completely reformatted everything and come here with everything set as default.

I have just made a new XP virtual machine. It can access the internet through the hosts ethernet connection.

Now, I would like to create one single folder on the host Ubuntu machine which the XP machine will able to read from. NOT write to, JUST read from.

What should I do?

Many thanks to anyone who can advise me on the first step. 

I'm flipping out right now! lol.

---

### Post by howefield on 2008-12-14
Have a look at the post by StuipedandUgly in this thread

[http://ubuntuforums.org/showthread.php?t=627847](http://ubuntuforums.org/showthread.php?t=627847)

Or read chapter 4.6 in the Virtualbox manual.

---

### Post by albinootje on 2008-12-14
Your posting is not very clear about what exactly goes wrong.

Are you using the virtualbox-ose from the Ubuntu repositories or the PUEL binary from the Virtualbox web-site ?
Last time i looked the OSE version didn't support shares (and USB and remote desktop).

---

### Post by howefield on 2008-12-14
> **albinootje said:**
> Last time i looked the OSE version didn't support shares (and USB and remote desktop).

Look again, OSE does support shared folders., (but your right about the other functions)

---

### Post by albinootje on 2008-12-14
Okay, thanks for the information!

---

### Post by Swerve1000 on 2008-12-14
At last!!!!! :guitar:

This is the first time I've read about Guest Additions.

All of the tutorials, video tutorials I've read etc never once mentioned this. I installed it and bang! Network drive working exactly how I wanted.

For future reference - XP/Guest working with no floppy, CD, networking or USB set in virtualbox. 

Only access XP has to the outside world is via My Computer>Network devices where it can reach the Read-Only shared folder. 

Firestarter does not need to be set to allow access for XP to access the network drive, the client cannot contact the 'outside world' at all.

Just what I wanted. 

:)


EDIT - One strange thing though, activating Guest Additions wiped my hosts wallpaper. Weird.

---

