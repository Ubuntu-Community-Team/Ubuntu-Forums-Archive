---
title: "Safe to install 12.04 beta2 ?"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by craig10x on 2012-04-02
I've been running the live iso of 12.04 beta2 for several days and it seems to be running very smooth...I was wondering if it would be safe to install at this point?

Will it automatically become the final release if i do all the updates?
How many updates do you average each day for this?  Do any bugs tend to get fixed in those updates?  
Also, if i were to install...is it best to install from beta 2 iso or just grab the latest "daily build" ?

Would appreciate some feedback...trying to decide whether to go ahead now or wait until end of month...Thanks! ;)

---

### Post by mcellius on 2012-04-02
I think it's very safe to install Precise beta 2 - into its own partition.  It works great for me and is pretty solid, but it's still important to remember that it is a beta and is being tested, so although I want to use it for actual work, I try to be careful.

Having said that, however, you'll probably be safe with it and, except for the occasional app crash, you're not likely to find it unstable or unsteady.  But since it is a beta, there are no guarantees.

---

### Post by sammiev on 2012-04-02
Stay where you are until 12.04 is released and maybe for a few weeks after. If it's not broken why rush. :)

---

### Post by Bucky Ball on 2012-04-02
> **sammiev said:**
> Stay where you are until 12.04 is released and maybe for a few weeks after. If it's not broken why rush. :)

+1. I usually wait a couple of months. The base kernel might be fairly robust but that doesn't mean there won't be breakages (updates could cause this). There is a lot that needs to work with the new kernel. 

Still testing. My old adage? If it ain't broke, don't fix it!

Having said that, yes, if you want to install to a separate partition and NOT use it for production work but instead help developers by reporting any issues you come across, by all means, go for it!

;)

---

### Post by craig10x on 2012-04-03
Thanks for the feedback...my 11.10 install has been running great so i guess i will hold off for the final release of 12.04...when i run the live session of 12.04 it seems to  be very stable and that is why i thought it would be ok to hard install now as my main operating system, take all the updates, and that it would become the final release automatically...but it  seems that the general thought here is to hold off (unless one wants to just be a "tester")...

---

### Post by philinux on 2012-04-03
> **craig10x said:**
> Thanks for the feedback...my 11.10 install has been running great so i guess i will hold off for the final release of 12.04...when i run the live session of 12.04 it seems to  be very stable and that is why i thought it would be ok to hard install now as my main operating system, take all the updates, and that it would become the final release automatically...but it  seems that the general thought here is to hold off (unless one wants to just be a "tester")...

I have two internal hard drives so I always test the dev version on disk 2.

I'll probably clean install on disk 1 a week before release date. I also have a laptop and data is backed up.

If you've already got the iso you can easily keep it up to date with zsync rather than download the whole thing again. This is what I do.

[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

n.b. I have the iso in Downloads folder so I cd to that folder and then issue the zsync command.

---

### Post by Bucky Ball on 2012-04-03
As suggested, you could install it to another partition, keep using it, get regular updates, and it *will* become the released version in time. Once its stable simply kill the 10.04 LTS partition and expand 12.04 into the freed space. 

BUT, I would leave your stable 11.10 there for now and either create a separate /home for 12.04 when you install to another partition or use the existing /home if you already have one.

To do the former choose 'Something Else' when you get there and untick /home for formatting during install; 12.04 will then use the existing /home as its /home also and you will be able to retrienve the files using 11.10 if 12.04 crashes. (I am presuming 12.04 is fine adopting the existing /home which is the norm for other releases.)

---

### Post by squilookle on 2012-04-03
Kubuntu 12.04 is working very nicely for me, but it's the same with any upgrade - there is always the risk it may not work as well as your current install, so if what you have works and does everything you need, there is probably no reason to rush into the upgrade.

---

### Post by craig10x on 2012-04-03
yes i guess that is certainly true...i suppose i got "revved" up about it when i ran the live iso...i will have to calm down and exercise some restrain and patience until the final release! :lolflag:

---

### Post by cariboo on 2012-04-03
Most of us regulars in this sub-forum always run the testing release along side a stable release, just in case there is a showstopper on the testing release. Gparted will allow you to resize your present partition, all you need is about 10GiB of empty space to successfully run a testing release, be it Ubuntu, Kubuntu, Lubuntu or Xubuntu.

---

### Post by craig10x on 2012-04-04
I did decide to install it after all....last night i downloaded the daily build and made an iso and installed 12.04 to my hard drive...So far seems very smooth and stable...

The only bug i detected so far is that i don't get any ubuntu "theme sound" when i boot up...anyone else experiencing that?  Not that big a deal, actually...but was curious...

---

### Post by ventrical on 2012-04-04
I got the drums when I log off and log back in  but I am on an automatic log-on. This is a fresh install from beta2 ISO.

---

### Post by cariboo on 2012-04-04
The startup sound is turned off by default. you can turn it back on again, by going to the cog wheel in the upper right corner, and select Startup Applications from the menu, things will be pretty self evident from there.

---

### Post by Irihapeti on 2012-04-04
There's a setting somewhere to set the sound on login to "on", if you want it. I think you have to be running Unity for it to be accessible.

I've been using 12.04 as my main system for a while now. As far as I'm concerned, it's stable enough for what I want to do. But I've still got a version of 10.04 that I keep up to date, just in case.

---

### Post by craig10x on 2012-04-04
thanks for the tip, cariboo907...i did what you suggested and put it on...wasn't aware that it was turned off by default...

however, it still doesn't come on when i boot up (i checked the box that was unchecked in startup applications)....

irihapeti...from what i am seeing so far, it does seem very stable and haven't really noticed any serious bugs...

so, then i guess that i just need to do all the updates that come in to the update manager and it would become the final edition at the end of the month?
(assuming it all goes smoothly...lol)...

i was really daring...i wiped out my 11.10 and replaced it with 12.04...so keeping my "fingers crossed" (lol)

---

### Post by sammiev on 2012-04-04
> **craig10x said:**
> thanks for the tip, cariboo907...i did what you suggested and put it on...wasn't aware that it was turned off by default...

however, it still doesn't come on when i boot up (i checked the box that was unchecked in startup applications)....

irihapeti...from what i am seeing so far, it does seem very stable and haven't really noticed any serious bugs...

so, then i guess that i just need to do all the updates that come in to the update manager and it would become the final edition at the end of the month?
(assuming it all goes smoothly...lol)...

i was really daring...i wiped out my 11.10 and replaced it with 12.04...so keeping my "fingers crossed" (lol)

Even though I do not recommend it to people with only one or two OS, I use it as my main but I have a USB HD I backup to weekly. I can come back from a major crash in 30 min or less. So far with 12.04 I never had to do a restore yet from its per-alpha stage. :)

---

### Post by craig10x on 2012-04-04
that sounds very encouraging! ;)

well, i think i figured that this has gone through alpha stages and now in it's final beta stage prior to release in just 3 weeks time...so my thought was, at this point, there shouldn't be anything major that you would get in the updates that would wreck havoc on it (lol)....so i think that is what encouraged me to put it on at this time...

And, thus far, the only (minor) bug i have had is that i can't get that ubuntu log in sound to work!

---

### Post by cariboo on 2012-04-05
A simple thing that I have a problem with at times, is the volume turned up enough to hear the sound at login?

---

### Post by craig10x on 2012-04-05
> **cariboo907 said:**
> A simple thing that I have a problem with at times, is the volume turned up enough to hear the sound at login?

hmmm...i will try that...but though i only had the alert volume turned up a small amount, i would think i would hear something....but i will give it a shot....

i assume it's the alert volume that works with that...my regular volume is up to 100% level...

weird i would have a problem with such a little thing like that when everything else is running great...

edit: i tried that....nothing...yet volume works fine for everything else!

---

### Post by prusswan on 2012-04-05
It wasn't any worse than beta 1 as far as I can tell. The sound still does not work properly for certain hardware (something to do with how pulseaudio is loaded) and some quirks remain with the built-in themes, apart from these setbacks one pretty much has the latest libraries.

---

### Post by terrykiwi83 on 2012-04-05
Question here for you. If I upgrade from 11.10 x64 to 12.04 x64 beta 2, will it upgrade to the final version once its released or will it remain as a beta until I remove it and install 12.04 fresh?

---

### Post by cariboo on 2012-04-05
> **terrykiwi83 said:**
> Question here for you. If I upgrade from 11.10 x64 to 12.04 x64 beta 2, will it upgrade to the final version once its released or will it remain as a beta until I remove it and install 12.04 fresh?

Yes, see the sticky at the top of the page.

---

### Post by craig10x on 2012-04-06
and how would it work in my case?...i installed an ubuntu 12.04 daily build around a week after beta2 was released....

when the final is released, will update manager offer to upgrade me to the final? or is it just a matter of installing all the updates each day?

If it's an upgrade...is it safe to use (no problems...in other words...lol)???

I'm just a little confused about this (first time i ever installed prior to a final release)....so clarification would be most appreciated...

---

### Post by cariboo on 2012-04-06
> **craig10x said:**
> and how would it work in my case?...i installed an ubuntu 12.04 daily build around a week after beta2 was released....

when the final is released, will update manager offer to upgrade me to the final? or is it just a matter of installing all the updates each day?

If it's an upgrade...is it safe to use (no problems...in other words...lol)???

I'm just a little confused about this (first time i ever installed prior to a final release)....so clarification would be most appreciated...

Do daily upgrades, and you'll end up with the final version.

---

### Post by jerrylamos on 2012-04-06
"Unstable" still in development.

I have a relatively new Acer Asoire 5253 newish with all sorts of features notebook which is having a lot of trouble with updates since they do a update-grub when the kernel changes, frequently making the pc unbootable so I run Super-Grub2-USB to get going again.  It's a multi-boot.  Yes there's a launchpad bug.

There's another 2005 IBM Thinkpad where install 12.04 Alpha worked but install Beta 2 fails copying files and I have to repair boot to get going again, that's a multi-boot as well.  Yes there's a launchpad bug.

Three others of my pc's Beta 2 installed just fine.

Release is imminent, just wait.  I've even had install problems post-release....better luck a couple weeks after release for fixes to come in.

Jerry

---

### Post by JHCKX on 2012-04-06
Whether or not a new release is safe tends to depend on your hardware. I was never able to install 9.10 due to an incompatiblity with my video card but it worked fine for others. Search the "Installation and upgrades" forum 6 months ago and you're bound to find other examples.

Even if the alpha or beta is stable on your machine, you still might want to wait for the official release. There are a lot of updates for development versions which can be a pain if you want to get anything done. Best to wait if that would be an issue for you.

---

### Post by saneearth on 2012-04-06
I have been running 12.04 off and on as the primary since the Alpha. It is still not by far bug free yet. I would wait a while after the release until I would install as my primary if I were you. Many applications are not working up to par in either the Ubuntu desktop or Gnome 3. I would be patient and wait.

---

### Post by craig10x on 2012-04-06
Thanks for the extra input, guys....though i did actually install it earlier in the week and so far it's running well (other then not getting the jungle drums boot up sound...lol) of course, the amount of updates each day is huge (like 80-100!) but things seem to be getting smoother as the updates come in (except still no boot up sound)...

Now that i actually have it on, i was wondering if it would just become the final release and was told that it would...Still of course, i wonder if i might be better off re-installing after final release, or would it not likely make any difference???  would there be any advantage to that???

---

### Post by 2F4U on 2012-04-06
> Thanks for the extra input, guys....though i did actually install it  earlier in the week and so far it's running well (other then not getting  the jungle drums boot up sound...lol) of course, the amount of updates  each day is huge (like 80-100!) but things seem to be getting smoother  as the updates come in (except still no boot up sound)...


Seems as this has been fixed with today's updates, at least on my installation.

> Now that i actually have it on, i was wondering if it would just become  the final release and was told that it would...Still of course, i wonder  if i might be better off re-installing after final release, or would it  not likely make any difference???  would there be any advantage to  that??? 

If you keep updating it will automatically become the final release. Absolutely no need to reinstall and also no benefit.

---

### Post by philinux on 2012-04-06
The login sounds are off by default. You enable it in startup items

---

### Post by craig10x on 2012-04-06
Thanks 2F4U...that is good to know...and Phil, even with today's updates (i saw one for pulseaudio in there) i still don't get the start up sound...even though i have the box for it checked on the start up applications...

Funny part is it worked fine on my previous 11.10 hard install...but 12.04 doesn't seem to like my laptop as far as that goes anyway (lol) I have a new toshiba with intel i3core processor and intel graphics...

---

