---
title: "Upgrades...6 month vs LTS to LTS"
date: 2014-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2014-09-26
I was wondering, for those who have had experience in recent years, doing both 6 month upgrades and LTS to LTS upgrades (every 2 years) using the online upgrade method, have they noticed any difference in reliability between the two?

My theory is, that a 6 month upgrade is probably generally more reliable then an LTS to LTS upgrade because over a 2 year period there are just so many major changes in ubuntu, that there is a greater chance that something will go wrong during the upgrade...

What are your thoughts on this, based on your actual experiences doing both types of upgrades? 
Thanks :D

---

### Post by andrew102 on 2014-09-26
Agree that you can expect by upgrading with each new release that it's probably not going to break. I've done a couple of 12.04 to 14.04 recently and turned out was better to do a fresh install.

The 13.10 to 14.04 upgrade was pretty smooth though.

---

### Post by craig10x on 2014-09-26
@andrew102:  Sounds like your experience pretty much confirms my theory about it...i prefer to do upgrades rather then clean install and have had great success doing the 6 month upgrades, but have never done the LTS to LTS method of upgrade...I was trying to decide whether to upgrade to 14.10 when it goes final or try to start doing LTS to LTS instead, but smooth upgrades are very important to me, and based on your experience, it sounds like i might be better off moving into each new version every 6 months rather then the other way...

Appreciate your input ;)   And would love to get more feedback from others who have had experiences doing both ways...

---

### Post by sudodus on 2014-09-26
I started with 7.10, upgraded to 8.04 LTS, but made a fresh installation of 8.04 LTS and still have that installation running via 10.04 LTS and 12.04 LTS. ***I think the LTS versions are more stable and polished than the short-life versions***, particularly after the first point release. I prefer to wait until the first point release (in the current case to upgrade from 12.04.5 to 14.04.1). But I am in no hurry, particularly for production platforms (the main system or 'work-horse').

Alongside that system I run several separate systems with new versions, even the development version (now Utopic to become 14.10), and different flavours of Ubuntu (Kubuntu, Lubuntu, Xubuntu etc).

Many people like to keep a separate ***home*** partition, and to make fresh installs. It is a straight-forward way to preserve a lot of the personal settings without getting too many problems. Another method is to keep the personal files (documents, pictures etc) in a separate ***data*** partition, and have a simple root file system, where program packages are installed, if and when needed. Such a system is very easy to maintain. Simply make a fresh installation alongside the current one, test it thoroughly and switch to the new system when you are happy with it. (You an keep the old system for a while.)

---

### Post by ian-weisser on 2014-09-26
Some users run into problems with LTS-to-LTS upgrades when they don't uninstall all their non-Ubuntu software (PPAs, Google stuff, etc). Poor version number choices and conflicting dependencies in those non-Ubuntu packages break upgrades.

I tell people that if they want newer software, go with the six-month releases. If changes annoy them, go with LTS.

---

### Post by MartyBuntu on 2014-09-26
I do a clean install of LTS versions only...every 2 years.

Because sometimes it's a nice feeling getting the broom out and batting away the cobwebs...;)

---

### Post by craig10x on 2014-09-26
I kind of like newer software, myself and since 6 month upgrades tend to be smoother then maybe it would be best for me to stay with doing each 6 month version...
If ones prefers to stay LTS, probably marty's method of doing a clean install each new LTS is probably the safest way to go ;)

The only PPA i use is google chrome which i uncheck before doing the upgrade...otherwise i pretty much run stock ubuntu stuff...that probably helps too...
My last upgrade (going from 13.10 to 14.04) was perfect except for 3 broken packages which the Synaptic Package Manager repaired in like about 30 seconds...otherwise it was flawless!
But it seems i do read an awful lot of postings on upgrade problems when they are done LTS to LTS...so i guess the 6 month is likely the safer way to go...

Ultimately, i did have to do a clean install of 14.04, but it had nothing to do with the upgrade...i accidently did a major bork which really messed things up and figured a clean install was the best
way to bail from the situation (and it was...lol)

Actually, i figure i will do my upgrade on RC date (a week before release) at that point, there has been a kernel freeze and the developers freeze as far as any significant changes, so a good way to 
"avoid the rush" :biggrin:

---

### Post by endlessinstant on 2014-09-26
I've been an Ubuntu user since 7.10 myself and I eventually gave up on non-LTS releases as I'd rather have stability over newer features.   I am a fresh install proponent though.  If you prefer to keep constantly updated, IMO you should consider switching to a distro with rolling updates like Arch.   

I don't think I've ever done an LTS to LTS upgrade though.  I did go from 8.04 to 10.04 but that involved upgrading to 8.10, 9.04. and 9.10.

---

### Post by sammiev on 2014-09-26
I like to do a lot of testing and install often, but really I prefer a fresh install and just move my data over.

---

### Post by craig10x on 2014-09-27
I was hoping ubuntu would go rolling...it was discussed then dropped...but in more recent times, Mark Shuttleworth did say he would like (once convergence took place) the 6 month version of ubuntu to be replaced and to go to a kind of a rolling distro with a stable core and updated apps and stuff when they are stable and ready to be added in....so, if that actually happens there would be just 2 ubuntus...the LTS version and a kind of a semi-rolling release version (and no more 6 month ones)...

Meanwhile, maybe rolling with upgrading every 6 months is my best course of action...I would try something like Arch (which as mentioned is rolling) but i am just too fond of ubuntu :D

---

### Post by ian-weisser on 2014-09-27
> **craig10x said:**
> But it seems i do read an awful lot of postings on upgrade problems when they are done LTS to LTS...so i guess the 6 month is likely the safer way to go...

Those happen when users merely uncheck the PPA (or don't - the system will uncheck it for them anyway).
But the PPA software is still installed.
The user usually doesn't remember what they installed from the PPA (sometimes years ago). So they cannot uninstall it. So they cannot upgrade.

Eventually they do a fresh install, which is often the best solution. The tough part is patiently handling all their frustration and denial.

EDIT: The two specific problems caused by non-Ubuntu packages are 1) Dependency conflicts and 2) Version confusion. Many PPAs behave properly and don't cause any problems at all (like Chrome). A normal user has no way to tell if a non-Ubuntu package will cause one of these problems.

---

### Post by Rob Sayer on 2014-09-27
There's no way to predict whether an LTS v. non LTS release will be more reliable.

The only reason I'll use a non LTS ubuntu release is because of hardware support issues.

I've used non LTS ubuntu opn my netbook for that reason and it's a pain in the ****.  When you upgrade there is no guarantee that the config for hardware will be the same.

While I have upgraded a release before and I didn't have any problems, I've seen too many people here with problems that I won't do it again.  A clean reinstall is better.

A separate /home partition is very useful for this.  I highly recommend it because you can reinstall while keeping your data and user settings.  Just don't tick the format box for /home when you reinstall, and back up data anyway.

---

### Post by craig10x on 2014-09-27
@ian-weisser: I could see that happening... although i have found that simply unchecking the google chrome ppa is sufficient not to cause any problems and doesn't seem to interfere with the upgrade..it is the only ppa i use, fortunately...then again, if you go 6 month releases, then there is less incentive to start installing all kinds of ppas to get newer versions of things since you get the more frequently...All Chrome's ppa updater does is replace your current version of Chrome with the latest one...

---

### Post by Mike_Walsh on 2014-09-28
I'm fairly new to all this, and 14.04 LTS is my first install. But since I value stability over constantly updated new stuff (I tend to get my system just how I want it, and then keep it like that), I probably won't be upgrading till 16.04 (I may even leave it till 18.04, I don't know yet). 

All my personal data is kept on an external HDD anyway. This is probably the wrong place to ask this, but how **do** you go about setting up a separate /home partition.....and more importantly, how do you 'point' the system to it, so as to retreive the data as and when you want to access it?


Regards,

Mike.

---

### Post by craig10x on 2014-09-28
@Mike_Walsh: That's a good question...never have done that myself but was always curious about it, so i hope some will reply with their ideas about how to best go about that ;)

For myself, i will probably just continue on the upgrade path...Actually, might have stayed in 14.04, but i need to get away from the 3.13 kernel as soon a possible because it causes multimedia problems on my hardware and i don't think i want to wait it out until february when 14.04 will finally get the 3.16 (utopic) kernel...And 3.16 kernel works great for me (have run 14.10 live session many times)...I tried the mainline 3.16 kernel on 14.04, but it runs much hotter then the patched ubuntu version that is actually installed on utopic...so, looks like i kind of NEED to move on to 14.10...

---

### Post by sudodus on 2014-09-28
> **Mike_Walsh said:**
> ...This is probably the wrong place to ask this, but how **do** you go about setting up a separate /home partition.....and more importantly, how do you 'point' the system to it, so as to retreive the data as and when you want to access it?


Regards,

Mike.

I searched the internet for ***install ubuntu with home partition*** and found the following links

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://askubuntu.com/questions/285212/keeping-the-same-home-partition-after-a-clean-install](http://askubuntu.com/questions/285212/keeping-the-same-home-partition-after-a-clean-install)

Good luck :-)

---

### Post by Mike_Walsh on 2014-09-29
Thanks for those, sudodus!

Actually, I found the second link in your list some time before I came back to this thread, and following the beautifully clear instructions on the page:-

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) ,

I now have a dedicated /home partition! \\:D/ 

It's something I've been meaning to do for ages. I keep a detailed backup of every piece of data I've got in a special partition on my external HDD, along with a sub-folder for regular system backups, but it's still nice to have it all in it's own partition; so that when I **do** replace 14.04 (which, as I said to Craig, may be 16.04, may be 18.04), I shall simply do a clean install of the new version, whichever it turns out to be. Takes a fraction of the time it does to install any of Redmond's offerings.....I can install the OS, and be nearly done with installing the software, in the time it takes to install Windows! :p

Regards,

Mike.

BTW; Just as an aside, do I take it I can use the same /home partition with ANY of the 'buntu-related distros? I only ask, because I'm also running Lubuntu, and Zorin's Core OS 9.....which is based on Trusty Tahr anyway! It would be very handy if I can.

---

### Post by sudodus on 2014-09-29
Yes you can, but there might be some confusion or complication. It would be better within the official flavours of Ubuntu, than when some re-spins are involved. It also depends on the software you are using. I suggest that you try it in a separate installation before you do it with your production platform.

---

### Post by vicshrike on 2014-09-29
Fresh install. Upgrades break bad when they break.

---

### Post by Mike_Walsh on 2014-09-29
> **sudodus said:**
> Yes you can, but there might be some confusion or complication. It would be better within the official flavours of Ubuntu, than when some re-spins are involved. It also depends on the software you are using. I suggest that you try it in a separate installation before you do it with your production platform.

Hm. I suspected that might be the case. In that case I'll try it with Lubuntu; I only installed it again the other day (in a matter of hours!) so I could talk my sister through using it on the old laptop I donated to her, which is running the 32-bit version. Poor lass had a lightening strike on their house some weeks ago, and it blew the surge protectors as well as the trips, and reduced her nice new PC to a useless pile of chips'n'stuff... #-o

Won't take very long to re-install it if I DO cack it up!! Gets easier every time I do it...

Regards,

Mike.

---

### Post by mastablasta on 2014-09-30
> **craig10x said:**
> 
Meanwhile, maybe rolling with upgrading every 6 months is my best course of action...I would try something like Arch (which as mentioned is rolling) but i am just too fond of ubuntu :D

If you don't actually have to do work on your computer. otherwise be prepared to troubleshoot the problems and do a some  reading before doing updates. you could also try Manjaro which I think has semi roling model.

> **craig10x said:**
> @Mike_Walsh: That's a good question...never have done that myself but was always curious about it, so i hope some will reply with their ideas about how to best go about that ;)

For myself, i will probably just continue on the upgrade path...Actually, might have stayed in 14.04, but i need to get away from the 3.13 kernel as soon a possible because it causes multimedia problems on my hardware and i don't think i want to wait it out until february when 14.04 will finally get the 3.16 (utopic) kernel...And 3.16 kernel works great for me (have run 14.10 live session many times)...I tried the mainline 3.16 kernel on 14.04, but it runs much hotter then the patched ubuntu version that is actually installed on utopic...so, looks like i kind of NEED to move on to 14.10...

no. there is hardware enablement stack which means you will be able to install newer kernel on 14.04: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)


> **Mike_Walsh said:**
> Hm. I suspected that might be the case. In that case I'll try it with Lubuntu; I only installed it again the other day (in a matter of hours!) so I could talk my sister through using it on the old laptop I donated to her, which is running the 32-bit version. Poor lass had a lightening strike on their house some weeks ago, and it blew the surge protectors as well as the trips, and reduced her nice new PC to a useless pile of chips'n'stuff... #-o

Surge protector for 18 EUR (probably even cheaper in US) would take care of that. always have one when in house and with expensive devices in network...

---

### Post by craig10x on 2014-09-30
@mastablasta: You're right, of course, 14.04 will get the utopic (3.16 kernel) but as noted from the schedule, not until next February...where as if i switch to 14.10 i can get it now...
Of course, i could install the mainline version but i tried it and it runs much, much hotter then the patched ubuntu version that is actually being used on ubuntu 14.10 ( which runs very cool on my hardware)...so while it solves my multimedia problem, it causes another problem (higher temps)...so, the quickest way to get the ubuntu patched 3.16 is to move into 14.10...

By the way, does 14.04 get it automatically (if you are already running it) or do you have to add that hardware enablement stack (by entering the terminal commands) ?
Still, it's kind of a long wait for me...

By the way, i remember you from when i use to participate in the kubuntu forum (i was on kubuntu for a while but switched back to ubuntu when it moved over to the unity desktop)... 
Nice to see you over here :D

---

### Post by deadflowr on 2014-09-30
> [COLOR=#000000]By the way, does 14.04 get it automatically (if you are already running it) or do you have to add that hardware enablement stack (by entering the terminal commands) ?[/COLOR]

If it's like precise was, if you have installed from 14.04, or 14.04.1, then you would need to install the stack yourself.
But if you install the second point release image when it comes out in February, then you would have the stack automatically.


Per the thread, though, As far as standard releases or lts to lts, I'm at a point where I'm getting so lazy in reinstalling that, as of right now, I'm almost thinking that with the support of lts being long enough I can skip one, so instead of going lts to lts, I'm thinking Lts ... skip ... lts(16.04).

Now, some food for thought on that, do you think when 16.04 comes out, those running precise will get an upgrade option for it?

---

### Post by ian-weisser on 2014-09-30
> **deadflowr said:**
> do you think when 16.04 comes out, those running precise will get an upgrade option for it?

That's currently not planned.
Similarly, 10.04 server users did not receive an upgrade path directly to 14.04.
The four-year gap will include a _lot_ of changes.

If a group of 12.04 users want to get together and plan out the transition at an Ubuntu Online Summit, it could certainly be added to the plan.
It would need to be driven and done by those users.

Diagramming out the changed packages and dependencies isn't difficult. All the testing and bugfixing takes the effort.

---

### Post by craig10x on 2014-09-30
Thanks deadflowr, i thought that is how it worked as far as getting the newer kernel on LTS that is already installed...I guess i will be moving along into 14.10 (using the upgrade)...sounds like you will need to upgrade to 14.04 if you plan on upgrading to 16.04, otherwise, you will end up having to do a fresh install at that time...

---

### Post by mastablasta on 2014-10-01
use what works best for you. if 14.04 is heating it all up too much then by all means use 14.10. 

there is a way to upgrade kernel only though (besides the enablement stack) I am not sure what that would mean or if it would bring any bugs. but it is sure possible to add newer kernel. of course it is much easier to install 14.10 and be done with it. 

but here is my experience with non LTS. I did it like you and installed 12.10. it all worked perfectly. I then upgraded to 13.04. it still worked well but there were some very minor issues (USB plugs not handled properly it seems - pluging usb stick while mouse is in results in mouse being disconnected) - hardware related. I then installed 13.10 and 2 FN keys stopped functioning. an easy workaround. then came 13.10 which worked about the same. and now 14.04 where more Fn keys stopped working as well as "prt scr". I made some workaround using the windows key but this is getting ridiculous. when I install 14.10 will the camera then stop working? or what? 

backwards support is just terrible. bug are reported, but remain unsolved.

mind you this is a Ubuntu certified laptop model (well actually I think only the Wi-Fi is replaced with an out of the box working one). I had to try it again with 12.04 to see if I am going crazy or something. and sure enough everything works out of the box there. all keys everything.

well I guess I do not need ot mention that nothing got ruined with win7 updates on the other side of the disk :-P

---

### Post by craig10x on 2014-10-01
Right, we know NOTHING every goes wrong with windows updates ;)
Yeah, the thing is i need that ubuntu patched version which you can get but it's kind of complicated (unlike grabbing a mainline kernel) and also, then you don't get any kernel updates on it (which you know sometimes includes security updates, and other improvements) and the only way to get that is to have it on an ubuntu version that is actually running it...

I think i am going to do the upgrade today (14.10 is only 3 weeks from final release now)...so, wish me luck :D

---

### Post by craig10x on 2014-10-01
Well, did the upgrade to 14.10 this morning and 100% success...I forgot to disable my chrome ppa but it did it for me (and told me as such)...took roughly 1 hour (or about 30 minutes more then a clean install) and it also gave me the option of cleaning out 53 no longer needed packages (including all the 3.13 kernels from 14.04) and i had it do that...Everything is the same as before as far as apps installed, data , files, etc...everything totally intact...All i had to do was re-check the chrome ppa again and i was good to go! :D 

So now i am running the 3.16 kernel which gets me away from the problems i was having on the 3.13 kernel...so glad i decided to go ahead...

---

### Post by sammiev on 2014-10-01
> **craig10x said:**
> Well, did the upgrade to 14.10 this morning and 100% success...I forgot to disable my chrome ppa but it did it for me (and told me as such)...took roughly 1 hour (or about 30 minutes more then a clean install) and it also gave me the option of cleaning out 53 no longer needed packages (including all the 3.13 kernels from 14.04) and i had it do that...Everything is the same as before as far as apps installed, data , files, etc...everything totally intact...All i had to do was re-check the chrome ppa again and i was good to go! :D 

So now i am running the 3.16 kernel which gets me away from the problems i was having on the 3.13 kernel...so glad i decided to go ahead...

Glad it all worked out for you. I usually try the upgrade and they work but I found a fresh install usually runs faster. House cleaning I guess. :p

---

### Post by craig10x on 2014-10-01
Thanks sammiev ;)

Interestingly enough, mine is running very fast and snappy...Perhaps the clean up process has improved considerably...53 packages were removed, including all the 14.04 kernels, so it seems to do a very efficient job these days...I figured it would be very good but i was shocked to find that everything was 100% perfect...i salute canonical! :D
It really does feel like a fresh install...and it saved me extra work...

I feel very encouraged now to stay on a 6 month rolling of ubuntu, using this method...especially if the results are as consistent as this was...

---

### Post by help_me2 on 2014-10-02
> **sammiev said:**
> I like to do a lot of testing and install often, but really I prefer a fresh install and just move my data over.
I always do a fresh install but keep the same /home folder. But I remove all .config files from /home except for chrome, firefox, and thunderbird. That way I don't have to move any files back to home. Always works great.

---

