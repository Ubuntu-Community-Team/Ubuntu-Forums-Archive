---
title: "LTSP with xfce on ubuntu 6.06 lts + upgrade failure"
date: 2008-11-20
forum: Server Platforms
---

### Post by lievendp on 2008-11-20
Good day everyone.

I have been reading the ltsp related info all around the net this last week but could not yet find a solution for my problem. (I might have looked over it because of the mass of information)

The situation:
Ubuntu 6.06 with ltsp client.
ltsp client works as a kiosk but is not the --kiosk version as far as I can see. 
ltsp client is xfce window manager.

the problem: firefox 1.5 installed, need firefox 3 for various reasons.
1) Upgrading the host server is working fine (following the 6.06lts to 8.04lts upgrade path)
2) upgrading the client (chrooted, proc mounted, following instructions provided at ubuntuLTSP) fails because of lots of missing dependencies which I'm unable to resolve. they have to do with "X-server"

My "solution" so far:
* installing a 8.04lts and installing ltsp-server on it (according existing procedures)
* creating a client there and moving it then to the other server.

Is it even possible to have an ltsp client from a newer ltsp version running on a server with older ltsp? (new = 8.04 LTS and old = 6.06 LTS)

I manage to create a client but alas, cannot login to the x login screen, it just shows the login screen over and over again, however login to the thinclient via ssh works fine.

BIG QUESTION: did anybody manage to upgrade a 6.06 with ltsp to the newer 8.04? How can it be done?

Thanks for any light someone might shed on this.
Do I need to put more info here? (output from logs or anything?)

kind regards,
Lieven

---

### Post by lievendp on 2008-11-20
I rephrase my text, one question (to know if I should proceed this)

Can I create a ltsp client on ubuntu 8.04 lts and expect it to run under a ubuntu 6.06 lts server?

---

### Post by mike010 on 2008-11-20
what are you using as thin clients disk less windows mac linux etc.?
i set mine up but i did not upgrade i did a fresh install of 8.04 
using windows xp as thin clients what VMware or are you using any?
never mind i see xfce.

as to your next quistion you should be able to do a lts 3.06 and 
run it on 8.04 but i would upgrade the server to 8.04 just in case
6.06 lts is coming from your server not on your 8.04 box so all you
will have there is a a window in to your 6.06 box all the stuff will 
be running from there and not the 8.04 box

---

### Post by lievendp on 2008-11-20
Thanks Mike,

I need to run firefox3 on the clients. Also later versions of Open office.
ff3 on 6.06 is a pain, however possible, I'd like to avoid that. ([http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html](http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html))

So if I understand correctly then I'll need to run ltsp v3.06 on the ubuntu 8.04 box (which has version 4 by default, correct?) Then I might be able to create an 8.04 version instance of the client which maybe can run on the existing 6.06 servers.

What a job, after all it seems like a bad idea to keep the old 6.06lts servers. I'll better upgrade them too. It seems that 4-5 years of support for an os version is just too short... :)
Isn't there a linux distro that has longer official support? my main problem is; i have to go through all this trouble just because of firefox3 and openoffice...

rgds,
Lieven

---

### Post by mike010 on 2008-11-21
> **lievendp said:**
> Thanks Mike,

I need to run firefox3 on the clients. Also later versions of Open office.
ff3 on 6.06 is a pain, however possible, I'd like to avoid that. ([http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html](http://techieblurbs.blogspot.com/2008/09/how-to-run-firefox3-on-ubuntu-edgy.html))

So if I understand correctly then I'll need to run ltsp v3.06 on the ubuntu 8.04 box (which has version 4 by default, correct?) Then I might be able to create an 8.04 version instance of the client which maybe can run on the existing 6.06 servers.

What a job, after all it seems like a bad idea to keep the old 6.06lts servers. I'll better upgrade them too. It seems that 4-5 years of support for an os version is just too short... :)
Isn't there a linux distro that has longer official support? my main problem is; i have to go through all this trouble just because of firefox3 and openoffice...

rgds,
Lieven


why do you need firefox 3?you should have some kind of vmware or remote desktop software to log into ts with ubuntu has client software in it.Your server is a 6.06 so what comes up on your desktop when you log into ts will be 6.06 your running software off your server so just run ff3 and oo from there.I run ubuntu lts 8.04 and ubuntu 8.04 desktop and windows xp pro
well my wife uses win xp pro (that dont say much for her does it)
running 6.06 you may need to run a older piece of software i would need to see your pc specs.to know for sure... i would upgrade openoffice too.
If you need any vmware just send me a email. Good luck

I would upgrade the lts server if you can here some reading on lts

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

and here you should find how to upgrade lts with little or no problem

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

**"friends don't let friends use windows"**
(but my wife might anyway she cant get linux)

---

### Post by mitchroberts on 2008-11-21
so what he is saying is he is running a linux terminal server
6.06 and needing it to work on 8.04 desktop?Why don't he just 
upgrade the server or is that the problem?6.06 will run on 8.04 
desktop

---

### Post by lievendp on 2008-11-21
Hi, thanks for the replies.

The thing is: I have a ubuntu 6.06lts server on which ltsp-server was installed (not the standalone version)
On that server, there is a i386 client. (/opt/ltsp/i386)
There are multiple thinclients which pxe boot and get the chroot from the server.
=> that works fine.

New situation: the thinclients need a new openoffice version because they need to be able to open newer MS office files. They also need firefox 3 because of issues with certain websites etc.

Problem: it is 6.06. and for above mentionned programs it needs to be 8.04

I tried to upgrade the chroot environment from dapper to hardy using the well-described procedure which fails due to lots of independencies which I cannot fix.
     -> chroot /opt/ltsp/i386 /bin/bash
     -> fix apt-sources
     -> apt-get update
     -> apt-get upgrade / dist-upgrade
     -> apt-get install update-manager-core / do-release-upgrade 
     -> FAILS in the chroot...
     -> However, an upgrade of the server itself from dapper to hardy seems to work fine.

I was hoping I could upgrade the chroot but that's not working. And then I decided to create a new ltsp server and build a new client for it, but I could not login to the thinclient (pxeboot) however, logging in to the thinclient using ssh works. Has to do with the users on that chroot I think.

Sorry for being nog clear in my explanations.

thanks again for reading.

Cheers,

Lieven

---

