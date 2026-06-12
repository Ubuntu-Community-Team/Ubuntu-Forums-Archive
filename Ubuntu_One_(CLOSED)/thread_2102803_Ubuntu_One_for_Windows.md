---
title: "Ubuntu One for Windows"
date: 2013-01-08
forum: Ubuntu One (CLOSED)
---

### Post by lz1dsb on 2013-01-08
Here's my setup, I use Ubuntu One on Ubuntu, Android and Windows 7.
I recently updated my Ubuntu One client for Windows, don't know which exact version. And by the way, where can I check that?
It works. But the strange thing is that when I open the Ubuntu One app, I see the indication "File Sync in progress..." and it stays that way all the time. 
But, it works! Also when I click the right mouse button in the notification on the Ubuntu One icon, I see the options and the menu says : "File Sync is up to date"
And it really is. I just checked it by modifying a couple of files and than logging from the Web interface. The files were synchronized.
Has anybody else come across this?

---

### Post by LuciferRex on 2013-01-08
For your app version, go to control panel->programs and features-> highlight ubuntu one, then at the bottom, it will list the version (I am running 4.0.0.)

As far as your syncing 'issue' I have something similar on my laptop (Ubuntu 12.04)  Force closed, and no issues since.

---

### Post by lz1dsb on 2013-01-08
> **LuciferRex said:**
> For your app version, go to control panel->programs and features-> highlight ubuntu one, then at the bottom, it will list the version (I am running 4.0.0.)

As far as your syncing 'issue' I have something similar on my laptop (Ubuntu 12.04)  Force closed, and no issues since.
Yes, indeed. I'm running exactly the same version like you. But... what you mention is for a client in Ubuntu. The issue I'm having is for the Windows client...

---

### Post by uzumakifahim on 2013-01-08
> **lz1dsb said:**
> Yes, indeed. I'm running exactly the same version like you. But... what you mention is for a client in Ubuntu. The issue I'm having is for the Windows client...

I think, LuciferRex is telling procedures to know the version on Windows 7, not on Ubuntu.

---

### Post by LuciferRex on 2013-01-08
> **uzumakifahim said:**
> I think, LuciferRex is telling procedures to know the version on Windows 7, not on Ubuntu.

Correct..that is how you find the version in Windows 7...sorry i wasn't more clear on that

---

### Post by lz1dsb on 2013-01-25
Since a while I can't get my Win7 Ubuntu One client working. When I start it, it hangs at "Getting information, please wait..." During that time it's inactive.
I found this link:
[http://askubuntu.com/questions/210555/ubuntu-one-windows-7-stuck-at-loading](http://askubuntu.com/questions/210555/ubuntu-one-windows-7-stuck-at-loading)
but I can't verify whether I have the same issue, I can't locate the syncdeamon-exception.log file. Where should I search for it?

---

### Post by lz1dsb on 2013-01-28
So after a half day of searching I was able to find this link with instructions on how to debug my Ubuntu One installation:
[https://wiki.ubuntu.com/UbuntuOne/Contribute/WindowsTesting](https://wiki.ubuntu.com/UbuntuOne/Contribute/WindowsTesting)

There are a lot of packages needed so I took me the next half of the day to install them. I did it in the order that is given on the site. Now I'm stuck on the section
**Run the ubuntu-sso-client service**

where after executing:
python bin\windows-ubuntu-sso-login
I get the following error:
C:\Users\user\ubuntu-sso-client>python bin\ubuntu-sso-login
Traceback (most recent call last):
  File "bin\ubuntu-sso-login", line 65, in <module>
    qt4reactor.install()
AttributeError: 'module' object has no attribute 'install'


Has anyone came across this?

---

### Post by lz1dsb on 2013-01-28
I just filed a bug in Launchpad
[https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/1108045](https://bugs.launchpad.net/ubuntuone-windows-installer/+bug/1108045)

---

### Post by lz1dsb on 2013-02-03
The issue seems to be related to the proxy in one of the networks where I'm using my Win7 laptop. So closing the thread.

---

### Post by alk224 on 2013-02-04
I'm having the exact same problem.  U1 worked beautifully for the last two years across my linux (11.10, 12.04) and windows (XP, 7) computers.  The client asked to upgrade (I think it installed version 4) and the whole thing ground to a halt.  Just as described, it hangs at "File sync starting" from the system tray.  If I open the client, it always says, "gathering information."  Rolling back to the previous version I had that worked (2.3) until this issue gets properly addressed.

---

### Post by lz1dsb on 2013-02-05
> **alk224 said:**
> I'm having the exact same problem.  U1 worked beautifully for the last two years across my linux (11.10, 12.04) and windows (XP, 7) computers.  The client asked to upgrade (I think it installed version 4) and the whole thing ground to a halt.  Just as described, it hangs at "File sync starting" from the system tray.  If I open the client, it always says, "gathering information."  Rolling back to the previous version I had that worked (2.3) until this issue gets properly addressed.
Hi, that's interesting. It could be that version 4.0.0 for Win7 is having this issue. Where I could download from an older version of Ubuntu One for Win7?

---

