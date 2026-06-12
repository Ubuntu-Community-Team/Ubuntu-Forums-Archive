---
title: "Xubuntu for the Elderly?!"
date: 2009-05-30
forum: The Cafe
---

### Post by ExWindowsDude on 2009-05-30
Question

Wanted to get opinions on "training" my Pop to use Xubuntu 9.04 vs. Windows XP.

For a 70+ year old man, he's pretty good at listening/walking through commands.

However, for the LIFE of me--I can't get him to stop clicking links, looking at jokes friends send him (he STILL does not understand the concept of Malicious software can arrive from a friend's email). --thus his PC is always getting infected.

I've tried everything I can to "lock down" his Windows environment to no avail (i.e. Host Block, Spybot, WinPatrol, AVG--etc.etc.)

It either gets past that---and/or I "disable" his computer functionality to the point he can't use it when needed (ie HOST Block/WinPatrol--locked him out of something he needed. I had to teach him to turn off---then turn back on, etc.etc.)-I'm betting he disabled for good. 

I've even begged/pleaded him to STOP using Outlook Express---and he keeps going back to OE the first time something goes "wrong" with Thunderbird (or GMail). 

Questions:
1-He's on DSL (so I *think* he has a static IP)--is there an application similar to "GO TO MY PC" that can be used with Xubuntu--I can use to help him diagnose problems (vs. trying the walk through over the phone---last time I was 2-hours on the phone with him). 

2-Is there a VMWare (free of course)---like Application---that when he needs to access his i386 "only" applications---he can pop open his Session and get to that?!?! For example--He has some Charles Schwab application installed on his CPU--I'm willing to bet they don't offer that in Linux format--and if they did---I'd have no clue how to support it (much less have him have success calling them to help him). 

MY GOAL:I'm really tired of walking him through fixing his infested Windows XP---and want to give him a way to simply check his email, run Picasa, run Gmail, run Thunderbird---and when he hit's a wall---I can "dial into" his PC and see what's up/how I can help him. 

Thanks!

---

### Post by spoons on 2009-05-30
Only a small response but a lot of people on DSL are on dynamic IPs, you should check with the ISP about whether it's possible to assign him a static IP address.

---

### Post by mocoloco on 2009-05-30
My thoughts.

[LIST]
[*]DSL - Yeah, it's probably dynapic. Usually you pay extra for a static IP and that's unlikely.
[*]"Training" - In your shoes I go for it. Do whatever works, tell him it's an upgrade, or say you won't support XP anymore because you're sick of it, but you'll provide all the support he wants under Xubuntu.
[*] Windows Software - There's a great free VM called VirtualBox. You also might first see if his software will run in Wine, or has an equivalent native app he could switch to. Test this step thoroughly before switching him, or his experience will be a negative one.
[*] Remote support - If you can set up his router to do port forwarding then you can VNC through Ubuntu's Vinagre. Or you can reverse VNC with [Gitso]("http://code.google.com/p/gitso/"), in which case you set up the port forwarding on your side.
[/LIST]

If you can meet all his software needs he'll probably enjoy Xubuntu much better than his current security nightmare.

---

### Post by ExWindowsDude on 2009-05-30
> **mocoloco said:**
> My thoughts.
If you can meet all his software needs he'll probably enjoy Xubuntu much better than his current security nightmare.

Thanks everyone....and I agree 100% Mocoloco

I'm convinced his problem(s) all that ill him are OS related. 
"slow computer" (I gave him a BRAND NEW Vostro--it's SCREAMING FAST on my dual boot--Win2k3/Xubuntu.

(by the way Facebook---EASILY 10x faster on Xubuntu-(even without ADBLOCK)

-the "conspiracy theorist in me things MSFT is up to dirty pool--they oown 5% of Facebook.....I think this because I have Sygate installed on my Win XP CPU--and the KERNEL!!!! the Windows NT KERNEL has tried to "phone home"---why does the NT Kernel need to phone home? Needless to say---I blocked/locked it--no problems with my PC).

My old man is so "funny"---he'll call me and say his computer is "broken"--if for (whatever reason)--the cookie is expired/gone--God only knows why with his computer---if his iGoogle Desktop is missing (you know the "special desktop" you can set up on your Google Account).

I can walk him through any Windows Problems in my sleep (been using it so long)---but I need to "see" and or "touch" what he's doing with Xubuntu to feel comfortable telling him what to do 

(I still don't feel 100% comfortable myself---so my set up is still "Beta" in my mind---and I break stuff every now and then---and simply reinstall Xubuntu). 

I guess ultimately  I need 3-solutions

1-a way to "dial into" his PC when something goes wrong.

2-a way to "roll back" or "give him back" the settings he "lost" (several times I've given up and simply had him use MSFT restore--which I HATE---but). 

3-A way for him to use 1386 applications--in a native Linux environment---I don't want him using dual boot--because he'll simply always boot to the XP--and "give up" on Linux--the first time something "goes wrong".

Thanks,

---

### Post by stwschool on 2009-05-30
> **ExWindowsDude said:**
> Thanks everyone....and I agree 100% Mocoloco

I'm convinced his problem(s) all that ill him are OS related. 
"slow computer" (I gave him a BRAND NEW Vostro--it's SCREAMING FAST on my dual boot--Win2k3/Xubuntu.

(by the way Facebook---EASILY 10x faster on Xubuntu-(even without ADBLOCK)

-the "conspiracy theorist in me things MSFT is up to dirty pool--they oown 5% of Facebook.....I think this because I have Sygate installed on my Win XP CPU--and the KERNEL!!!! the Windows NT KERNEL has tried to "phone home"---why does the NT Kernel need to phone home? Needless to say---I blocked/locked it--no problems with my PC).

My old man is so "funny"---he'll call me and say his computer is "broken"--if for (whatever reason)--the cookie is expired/gone--God only knows why with his computer---if his iGoogle Desktop is missing (you know the "special desktop" you can set up on your Google Account).

I can walk him through any Windows Problems in my sleep (been using it so long)---but I need to "see" and or "touch" what he's doing with Xubuntu to feel comfortable telling him what to do 

(I still don't feel 100% comfortable myself---so my set up is still "Beta" in my mind---and I break stuff every now and then---and simply reinstall Xubuntu). 

I guess ultimately  I need 3-solutions

1-a way to "dial into" his PC when something goes wrong.

2-a way to "roll back" or "give him back" the settings he "lost" (several times I've given up and simply had him use MSFT restore--which I HATE---but). 

3-A way for him to use 1386 applications--in a native Linux environment---I don't want him using dual boot--because he'll simply always boot to the XP--and "give up" on Linux--the first time something "goes wrong".

Thanks,
1. Two methods. VNC if you prefer something visual (you can walk him through terminal commands to get the IP address, trust me that's much easier than a walkthrough of a gui app). SSH if you're cool with command line. You'll need to install ssh package on your machine and his.
2. Roll back is easy enough. Zip up the whole hard drive and store the backup somewhere else (ie DVDs or an external drive). If he breaks it, just unzip to write back over the old content. Linux lets you do that, where windows doesn't. Once the setup is 'final', you'll only need to periodically backup the home directory mostly and just grab the whole thing once a month say. You could even give him a script to do that for him, or setup sbackup for him.
3. Wine. [www.winehq.org](www.winehq.org) for more. I find it runs most programs, especially if you use winetricks to add on a few bits and pieces like directx (for games) and vcrun2005, 2008, vb6 runtimes, etc. Btw don't forget to get everything from his c:/windows/fonts folder and put it in /home/yourname/.fonts or some programs might look odd.

---

### Post by Mirages on 2009-05-30
VMWare alternative ----> VirtualBox, you can find it in the repository

WINE is a windows compatibility layer so you can run M$ applications in linux without having to log into a virtual machine or dual boot. most stuff works in it.

Remote Desktop Viewer perhaps? could allow you to view and take control of the computer? not certain on that never used it but worth looking into?

I run ubuntu cause I like the gnome desktop environment vs. xubuntu xfce desktop environment there is also kubuntu which uses the KDE enivronment, KDE looks more windows-ish. there is stuff out there to make the GUI look like windows. perhaps he would like that?

lots of options I hope you it works out!

EDIT: also in addition if he doesn't like thunderbird, and its a serious issue Ubuntu comes with Evolution email client by default which is pretty much exactly the same as outlook express. Xubuntu comes with thunderbird by default I think and Kubuntu comes with Kmail.

again lots of options :)

---

### Post by MikeTheC on 2009-05-30
[font=arial][size=5]@ OP: What'd you say, sonny? Speak up when you post.[/size][/font]

[-X

---

### Post by lykwydchykyn on 2009-05-30
If you can forward a port on his router, you can set up and account with dyndns.org so that he won't need a static IP.  See:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

The best performer as far as remote GUI software is NXserver from nomachine.  It can run entirely over SSH.  It's not open source, but there is a free-as-in-cost version that will run two simultaneous connections. You can get it from [www.nomachine.com](www.nomachine.com).

I'll second or third the recommendation for VirtualBox, I've used it for years and it's quite easy.  Even my seven-year-old can use it.

---

### Post by Warpnow on 2009-05-31
sudo apt-get install lxlauncher
lxlauncher &

---

### Post by HappyFeet on 2009-05-31
So many opinions, so little time. A lot of it has to do with how good of a teacher you are. All my linux people are real happy. Thank god they never call me, except to install it for them on something else. :D

---

### Post by Dr. C on 2009-05-31
> **ExWindowsDude said:**
> Question

Wanted to get opinions on "training" my Pop to use Xubuntu 9.04 vs. Windows XP.

For a 70+ year old man, he's pretty good at listening/walking through commands.

However, for the LIFE of me--I can't get him to stop clicking links, looking at jokes friends send him (he STILL does not understand the concept of Malicious software can arrive from a friend's email). --thus his PC is always getting infected.

I've tried everything I can to "lock down" his Windows environment to no avail (i.e. Host Block, Spybot, WinPatrol, AVG--etc.etc.)

It either gets past that---and/or I "disable" his computer functionality to the point he can't use it when needed (ie HOST Block/WinPatrol--locked him out of something he needed. I had to teach him to turn off---then turn back on, etc.etc.)-I'm betting he disabled for good. 

I've even begged/pleaded him to STOP using Outlook Express---and he keeps going back to OE the first time something goes "wrong" with Thunderbird (or GMail). 

Questions:
1-He's on DSL (so I *think* he has a static IP)--is there an application similar to "GO TO MY PC" that can be used with Xubuntu--I can use to help him diagnose problems (vs. trying the walk through over the phone---last time I was 2-hours on the phone with him). 

2-Is there a VMWare (free of course)---like Application---that when he needs to access his i386 "only" applications---he can pop open his Session and get to that?!?! For example--He has some Charles Schwab application installed on his CPU--I'm willing to bet they don't offer that in Linux format--and if they did---I'd have no clue how to support it (much less have him have success calling them to help him). 

MY GOAL:I'm really tired of walking him through fixing his infested Windows XP---and want to give him a way to simply check his email, run Picasa, run Gmail, run Thunderbird---and when he hit's a wall---I can "dial into" his PC and see what's up/how I can help him. 

Thanks!

Here are some thoughts. 

By i386 application do we mean a 16 bit Windows Application that was originally designed for Windows 3.xx on a 386? If so DOS 6.22 / Windows 3.1 or Windows 3.11 in a virtual machine is an option. Why because no one writes malware for 16 bit Windows these days. 

As for virtualization software there is 
Virtual box (free as in speech and beer or free as in beer) 
VMware Server (free as in beer) 
among others.

A second choice would be Wine but here again there is the slight possibility that malware written for Windows would run on Wine. Wine is getting a lot better these days. As for Windows XP in a VM one runs the risk of a heavily malware infected XP in a VM on Xubuntu.

---

### Post by Mirages on 2009-05-31
> **FineE said:**
> A second choice would be Wine but here again there is the slight possibility that malware written for Windows would run on Wine. Wine is getting a lot better these days. As for Windows XP in a VM one runs the risk of a heavily malware infected XP in a VM on Xubuntu.

that being said... maybe you should just find open source alternatives for all has windows apps, to avoid risk of infection. [www.osalt.com](www.osalt.com) provides alternatives for alot of commercial apps.

I don't see much risk in running a VM or app in WINE usless hes doing risky things that involve an interent connection and non-trustworthy links and programs. everything internet orientated that puts him at risk for infections should be done in the native ubuntu environment not the VM.

if keeping him from using windows is a problem I wouldn't install a VM because he might just end up using that instead of ubuntu for everything that ubuntu can do (unless you strip down the windows VM so that all it does is run those few extra windows apps he needs)

although rather drastic I would consider just finding alternatives for his windows apps and leaving it at that. he will learn to use and accept them like he did with windows.

---

