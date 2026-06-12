---
title: "Cannot login with GUI on Xenserver 6.5 SP1"
date: 2015-08-06
forum: Virtualisation
---

### Post by Dok_Jest on 2015-08-06
[I](FYI - My skills are a beyond newb, I can read and follow advice - I have no problem at the command levels, and know what I want to do and how to look it up, but still don't know a lot)
[/I]
I'm running a Xenserver 6.5 SP1 on an Intel NUC (specifically model 5I7RYH) with 16gb RAM and a 500gb SSD. 
I have created a few VM's with Windows which function perfectly, but when I work with Linux, I have odd login behavior and I was wondering if anyone has any thoughts that might help:

I have a "functional" installation of Kali, but it will not log me in with anything other than ROOT. The user ID I created during installation does not work, BUT I can login with ROOT through the GUI.

I tried all 4 versions of both Ubuntu 14.04.2 LTS (Server, desktop, x86 and 64bt) as well as 15.04 (Desktop x86 and 64bt) and all have the same exact issue:

I create a default user ID - dokjest, a standard password which rates as fair (8 char. upper, lower, number, symbol)
The VM installs completely and reboots as expected, and brings me to the Ubuntu gui login screen. 
*NOTHING* I use with the gui will allow a login. when I use a user ID/password combo that is valid, it spins for about 10 seconds then returns back to the login prompt. When I use an ID/password combo that is invalid I get the normal login failed error on the top of the login prompt.

I would try logging in through a text shell, but not sure how to get there from this stage. I thought about SSH, but I don't see that service running, so I'm not sure how to test that type of login.

Any suggestions?

Thanks as always!
Dok Jest

---

### Post by Dok_Jest on 2015-09-03
As an update, I believe the screen is displaying at a resolution over 2560 and is not scaling, or scrolling. This is positioning in the center of the screen, not letting me reach any of the controls. I'm not sure of the cause of this, but I made good progress with UbuntuMate. It is scaling and letting me function. I would like to learn more about why Gnome is not functioning for me correctly, but I can at least do what I need under Mate.

---

### Post by pmc11 on 2015-11-29
I know its been a while but did you ever fix this?
I have just installed Xen on a Nuc5i5ryh and am having this exact problem.
I have VM's that worked on the last server and were migrated across via hdd (no pool) and also fresh ones all showing this behaviour.

Any help would be appreciated if you ever solved this.

P

---

