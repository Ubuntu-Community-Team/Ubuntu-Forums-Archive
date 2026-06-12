---
title: "Internet Café"
date: 2008-02-03
forum: The Cafe
---

### Post by rapha on 2008-02-03
Hi all,

I've been asked by the local internet café to fix their stuff and set everything up from the scratch. Unfortunately I don't think it is going to be economically feasible to have Ubuntu run on the customer machines (there's 12 of them), but maybe somebody here has experience with internet cafés in general.

What I'm looking for is some software (either Free or proprietary, if must be), with which to manage the whole thing. Like, enable access to a workstation, handle payment, and so on. Preferably the server part of it should run on Linux, with the clients being for Windows.

I've looked at freshmeat.net, and there pretty much seems to be "Cyborg" and "Open Kiosk", none of which look like they'd be in a real good shape. Any experiences with those?

Looking forward to whatever you'll have to say :-)

- Raphael

---

### Post by freebeer on 2008-02-03
[This]("http://ubuntuforums.org/showthread.php?t=669903&highlight=internet+cafe") might be of interest to you.

---

### Post by ice60 on 2008-02-03
there are windows programs that erase all changes made to the system when it's rebooted. and maybe the last security now podcast has something about locking down windows, i didn't listen to it because it doesn't interest me.
[http://www.grc.com/sn/SN-129.htm](http://www.grc.com/sn/SN-129.htm)

---

### Post by Catharina on 2008-02-03
Maybe there is something here for you:

[http://www.worldofinternetcafes.de/internetcafe_software_e.html]("http://www.worldofinternetcafes.de/internetcafe_software_e.html")

or this one: [http://silentcoder.co.za/silentcoder/content/view/67](http://silentcoder.co.za/silentcoder/content/view/67)

---

### Post by rapha on 2008-02-03
Hey, those are great hints, thanks - I'd been thinking about setting up some sort of one-click-reinstall, but this SteadyState thing sounds good as well.

The Cafe Con Leche thing looks very interesting for anybody wanting to run a Linux-only cafe. Apparently in some countries like Indonesia or the Philippines police have begun to raid internet cafes checking them for illegal Windows usage.

On the pay-side, I found [CafeSuite]("http://cafesuite.net/") to look the most promising and professional. 220$ for 12 computers, including one year of support sounds reasonable, too. Any experiences with it?

---

### Post by rapha on 2008-02-03
> **Catharina said:**
> 
http://www.worldofinternetcafes.de/internetcafe_software_e.html"]http://www.worldofinternetcafes.de/internetcafe_software_e.html
[http://silentcoder.co.za/silentcoder/content/view/67](http://silentcoder.co.za/silentcoder/content/view/67)

Thanks for those links as well! The second seems to be 404? I'm checking out the links from the first now :-)

---

### Post by ice60 on 2008-02-03
here are some of those roll back  and lock down programs, i haven't used windows for a long time, but a lot security nuts use these -
Deep Freeze
PowerShadow 3.0
[http://www.faronics.com/html/dfmappt.asp](http://www.faronics.com/html/dfmappt.asp)
RollBackRx 8.1
EAZ-FIX 
Anti-Executable
Returnil

and there's Software Restriction Policys too -
[http://www.mechbgon.com/srp/index.html](http://www.mechbgon.com/srp/index.html)

---

### Post by rapha on 2008-02-04
Thanks again, ice60 - I'm in the café right now and have to say it's pretty bad. 3 machines have stopped working and I'm sure now this will all have to be set up from scratch.

At the moment, I think I'm going to show both CybOrg, OutKast and CafeSuite to the owner and let her decide which one she prefers... reinstalling one of the computers now and downloading all the software...

---

### Post by jaffa_nz on 2008-02-04
mate.

Irrespective of the Management software you wish to implement for app deployment, controlling features etc, think of setting up a Linux Ubuntu Server with PXE, and some free or cheap imaging solution.  Then use Multicast type scenareo to redeploy the images automatically, simultaneously, each night.

ie. each pc connects to via PXE to the Linux server, and you press Go or some such and one image is blatted to all at the same time.  All clean.

and you use your management software etc to manage the dailies..

---

### Post by jaffa_nz on 2008-02-04
oops almost forgot.

LTSP Look into this for thin client distributions, awesomely easy to get going and of course to "re-image" machines that have been notably played with.

---

### Post by rapha on 2008-02-07
Hi all,

I've talked to the owner again and we've agreed to the following now. Since she doesn't make that much money with the internet PCs (her main income is from the telephone booths), we'll go slowly on this one. Whenever a PC breaks, I'll manually re-install Windows on it and get an image of that PC using the (excellent btw!) GParted/CloneZilla-LiveCD. In a couple of months all of her 12 PCs will have an image that way, thus being able to be restored by me in about an hour. We'll overhaul the whole thing with a new management software and possibly thin clients or some such solution when she re-launches her café, which will probably be next year or so.

Thanks for all your suggestions so far! I'll make sure  to keep this thread bookmarked ;-)

Best regards,
Raphael

---

