---
title: "Question Regarding Utopic Unicorn Live Session"
date: 2014-07-02
forum: Ubuntu Development Version
---

### Post by craig10x on 2014-07-02
There is something that is puzzling me...i assume that if you run a live session of 14.10 it should contain everything up to that date...Recently, i burned an iso of ubuntu main edition (with unity) 64 bit and in the live session, assumed i was running the current utopic kernel (which from what i understand is 3.15 at the current time)....yet, when i opened the terminal and checked it with:  uname -r  what it said was that i was running 3.13.30 (which is the current Trusty kernel version)...anyone have a clue to why this would be?  

Also, if some of you could run a live session of a 14.10 daily build (w/unity and 64 bit) and tell me what kernel it is showing for you....would be appreciated... ;)

I wanted to test to see how 3.15 that is actually the ubuntu installed one is running as opposed to my ubuntu 14.04 install, where i am running 3.15 but from the mainline, which i assume isn't quite as customized as the ubuntu installed version is...On my 14.04 with mainline 3.15, it runs a few degrees hotter then i normally get on the ubuntu installed kernels..that is why i wanted to test it on 14.10 live session...

---

### Post by mc4man on 2014-07-03
Don't really have to install here to see - 
[http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.manifest)

---

### Post by craig10x on 2014-07-03
Thanks for that link...so according to that, it is 3.13 kernel, and yet, if you have the installed version, you are running 3.15 kernel aren't you?  (I have read that is the current kernel running on 14.10 development)...
That is strange...that the live session would run the older version where as the installed version runs the newer one...

---

### Post by mc4man on 2014-07-03
If I was to install from the current iso then I'd expect to boot up to what was on the iso which is marked as 3.13
Did you find that not to be the case?

---

### Post by craig10x on 2014-07-03
Except i was under the impression that 14.10 is running in kernel 3.15...in fact, this link from zika from another thread i posted on, when i asked him what 14.10 was currently running, he directed me to this:
[http://packages.ubuntu.com/utopic/linux-image-generic](http://packages.ubuntu.com/utopic/linux-image-generic)

So, if that is the case, why is 14.10 live session's kernel completely different from what 14.10 installed is currently using, when the daily builds iso are supposed to be up to the day of posting?

---

### Post by zika on 2014-07-03
Look at production dates of files You're talking about:
[utopic-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso")[COLOR=#000000]           **20-May-2014** 07:53  1.0G  Desktop image for 64-bit PC (AMD64) computers (standard download)
[/COLOR][utopic-desktop-amd64.manifest]("http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.manifest") **20-May-2014** 07:42 56K Desktop image for 64-bit PC (AMD64) computers (contents of live filesystem)
[http://packages.ubuntu.com/utopic/linux-image-generic](http://packages.ubuntu.com/utopic/linux-image-generic) is a bit fresher... ;)
Nothing serious that one upgrade from &#8222;current&#8220; to *current* (not as &#8222;current&#8220; as in live image files (pun intended ;))) state would not fix.

---

### Post by rrnbtter on 2014-07-03
Greetings,
Try this one [http://www.cdimage.ubuntu.com/daily-live/20140702/](http://www.cdimage.ubuntu.com/daily-live/20140702/)
You should have little to no updates after the installation. You can zsync your existing image over the the new one.

---

### Post by Mateusz Stachowski on 2014-07-03
> **rrnbtter said:**
> Greetings,
Try this one [http://www.cdimage.ubuntu.com/daily-live/20140702/](http://www.cdimage.ubuntu.com/daily-live/20140702/)
You should have little to no updates after the installation. You can zsync your existing image over the the new one.

As others already mentioned the last images in daily-live/current are from 20th May. However there were many newer images like the one which **rrnbtter** links. To get the freshest Utopic images you have to constantly change dates. 

For what I know those images don't complete the CI automatic tests and that's why they don't get copied to daily-live/current.

---

### Post by mc4man on 2014-07-03
they seem to be using a different system, the latest is now 'pending' , so just use that (word)
[http://www.cdimage.ubuntu.com/daily-live/pending/](http://www.cdimage.ubuntu.com/daily-live/pending/)
index - 
[http://www.cdimage.ubuntu.com/daily-live/](http://www.cdimage.ubuntu.com/daily-live/)

---

### Post by craig10x on 2014-07-03
Thanks guys for clarifying that...it was confusing the heck out of me ;)
I'll try the one that rrnbtter linked to and check it in the terminal when i run the live session...

---

### Post by Mateusz Stachowski on 2014-07-03
That's not exactly how it is:

>  current/                02-Jul-2014 08:22    -   Latest images to have passed any automatic testing; try this first
            pending/                02-Jul-2014 08:22    -   Most recently built images; not yet automatically tested

---

### Post by craig10x on 2014-07-04
I downloaded that live session of 14.10 development 64 bit he gave me and indeed it IS running the 3.15 kernel, so i was able to do my tests...what i am noticing is the ubuntu patched version on 14.10 does run somewhat cooler then the mainline one does....The mainline version is called 3.15.0 (which i have installed on my 14.04) the ubuntu patched version of 14.10 is called:  3.15.0-6.11....

Is there any (simple) and safe way to install the utopic ubuntu patched version on ubuntu 14.04?
If so, where do you get it from and how do you do it?

---

### Post by zika on 2014-07-04
> **craig10x said:**
> I downloaded that live session of 14.10 development 64 bit he gave me and indeed it IS running the 3.15 kernel, so i was able to do my tests...what i am noticing is the ubuntu patched version on 14.10 does run somewhat cooler then the mainline one does....The mainline version is called 3.15.0 (which i have installed on my 14.04) the ubuntu patched version of 14.10 is called:  3.15.0-6.11....

Is there any (simple) and safe way to install the utopic ubuntu patched version on ubuntu 14.04?
If so, where do you get it from and how do you do it?Of course...
Just take the same route that was mentioned here (above:#5(about a post of mine)):
[http://packages.ubuntu.com/utopic/linux-image-3.15.0-6-generic](http://packages.ubuntu.com/utopic/linux-image-3.15.0-6-generic)
[http://packages.ubuntu.com/utopic/linux-headers-3.15.0-6-generic](http://packages.ubuntu.com/utopic/linux-headers-3.15.0-6-generic)
[http://packages.ubuntu.com/utopic/linux-image-3.15.0-6-generic](http://packages.ubuntu.com/utopic/linux-image-3.15.0-6-generic)
[http://packages.ubuntu.com/utopic/linux-headers-3.15.0-6](http://packages.ubuntu.com/utopic/linux-headers-3.15.0-6)
[http://packages.ubuntu.com/utopic/linux-firmware](http://packages.ubuntu.com/utopic/linux-firmware)
(I hope I did not forget some) and install those .deb files as You would from mainline...
Just be carefull to install only specific .deb  files not a pointers for packaged so You would get regular updates for 14.04 and still have option to use newest kernel (from 14.10, for example) in 14.04...
Beware that automatic upgrade will not work for this kernel and its constituents and that You will have to purge this and install newer kernel every time it appears...

---

### Post by craig10x on 2014-07-04
Ah, Zika comes through again ;)
You know, i am Mr. "technophobe" so you will have to help me along a bit...would i just need to download a deb from one of these mirrors (on the page i show here)?
[http://packages.ubuntu.com/utopic/amd64/linux-image-3.15.0-6-generic/download](http://packages.ubuntu.com/utopic/amd64/linux-image-3.15.0-6-generic/download)

And, then, how would i install? (is it just one deb package) can i open it in ubuntu software center and have it install for me?
Also, should i need to remove it, will i be able to do it using the synaptic package manager? (which is they way i have been removing the mainline kernels)?

If i need multiple packages from that website...which specific ones are needed for the 64 bit version (generic not low latency)...
I'm surprised no one puts out a guide on how to do it...many sites show you easily how to install the mainline kernel (using 3 terminal commands to download the debs and 1 command to install)...but seems like no one spoon feeds it like that for the ubuntu patched version of the same kernel...

Do you mean i have to install all 5 of those deb packages (you linked above)...this all sounds a lot more confusing :confused:

Seems like the easiest way i can actually get the ubuntu patched version is to upgrade my 14.04 to 14.10 development but as i have mentioned, i only have 1 computer and use 1 Os only and i have been getting the impression that i wouldn't be able to count on 14.10 to be as reliable as 14.04 is...if i could, i'd upgrade in a heart beat ;)

---

### Post by Elfy on 2014-07-04
whichever way you read it, this IS the dev version - if it breaks, that's what it does

if you only have 1 computer and 1 OS then you really shouldn't run dev

I use vm's a lot just to check what the dailies are like, I check in here prior to updating, I check a few m/l's I read to see what's happened, I read the backlog in some IRC channels - then I STILL update and break it

if you can't do those things for whatever reason you're in the wrong place :)

---

### Post by craig10x on 2014-07-04
I guess so, Elfy...still i wonder if anyone could outline for me an easy way to get the ubuntu patched version of the the 3.15 kernel on to my 14.04 install...then i could run with it until 14.10 is final released and get it (or even the 3.16 kernel by then if that is what it gets released with) by default...

I'd need [COLOR=#000000]3.15.0-6 in the 64 bit version...so if anyone can give me an a-z outline of exactly what to do to get it on here, i'd be very grateful [/COLOR];)

---

### Post by craig10x on 2014-07-05
I came upon this site...would this be good to use? seems like he compiles the ubuntu kernel (in this case 3.15.0-6) and puts it in a zip file....instructions seem to say to unzip it then run the terminal command he gives to install it (i am assuming you would copy and paste the 3 lines together as one and enter in the terminal?)...perhaps this would be an easier way for me to get that kernel on my 14.04 install?
[http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/](http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/)

---

### Post by zika on 2014-07-05
> **craig10x said:**
> Ah, Zika comes through again ;)
You know, i am Mr. "technophobe" so you will have to help me along a bit...would i just need to download a deb from one of these mirrors (on the page i show here)?
[http://packages.ubuntu.com/utopic/amd64/linux-image-3.15.0-6-generic/download](http://packages.ubuntu.com/utopic/amd64/linux-image-3.15.0-6-generic/download)

And, then, how would i install? **(is it just one deb package)** can i open it in ubuntu software center and have it install for me?
Also, should i need to remove it, will i be able to do it using the synaptic package manager? (which is they way i have been removing the mainline kernels)?

**If i need multiple packages from that website...which specific ones are needed for the 64 bit version (generic not low latency)...**
[COLOR=#daa520]*I'm surprised no one puts out a guide on how to do it...many sites show you easily how to install the mainline kernel (using 3 terminal commands to download the debs and 1 command to install)...but seems like no one spoon feeds it like that for the ubuntu patched version of the same kernel...*[/COLOR]

**Do you mean i have to install all 5 of those deb packages (you linked above)...this all sounds a lot more confusing** :confused:

Seems like the **easiest way** i can actually get the ubuntu patched version is to upgrade my 14.04 to 14.10 development but as i have mentioned, i only have 1 computer and use 1 Os only and i have been getting the impression that i wouldn't be able to count on 14.10 to be as reliable as 14.04 is...if i could, i'd upgrade in a heart beat ;)If that is the &#8222;easiest way&#8220; than we do have very different metrics about &#8222;easy&#8220;.
Bolded was answered in my reply...
[COLOR=#daa520]ad italic:[/COLOR] That is for sure not the way of using those kernels that anyone would encourage and that would make a mess more that it would make any good... Purpose is not to make Frankenstein installs, I'm sure...

> **craig10x said:**
> I guess so, Elfy...still i wonder if anyone could outline for me an **easy way** to get the ubuntu patched version of the the 3.15 kernel on to my 14.04 install...then i could run with it until 14.10 is final released and get it (or even the 3.16 kernel by then if that is what it gets released with) by default...

I'd need [COLOR=#000000]3.15.0-6 in the 64 bit version...so if anyone can give me an a-z outline of exactly what to do to get it on here, i'd be very grateful [/COLOR];)Define &#8222;easy way&#8220; so it would be easy(er) to answer.

> **craig10x said:**
> I came upon this site...would this be good to use? seems like he compiles the ubuntu kernel (in this case 3.15.0-6) and puts it in a zip file....instructions seem to say to unzip it then run the terminal command he gives to install it (i am assuming you would copy and paste the 3 lines together as one and enter in the terminal?)...perhaps this would be an **easier way** for me to get that kernel on my 14.04 install?
[http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/](http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/)You were active while I was asleep...
Kernel You're mentioning is not the one that do have patches that made Your machine cooler... Again difference in what &#8222;easier way&#8220; is if it do not fullfill constraint given... Not to mention that I do not see any reason to introduce third party kernel now into discussion... Unsecure way of thinking...
Last night I've just simply answered (with direct and clear instructions) (simply DL all the packages given, checking one again if I did forget or give a package more than it is needed, in a folder, I use /tmp, and issue simple ```
sudo dpkg -i *.deb
```while being in that folder, and that it's it. Be sure to watch for questions that dpkg might throw at You and answer very restrictively.)  to Your question:
> **craig10x said:**
> I downloaded that live session of 14.10 development 64 bit he gave me and indeed it IS running the 3.15 kernel, so i was able to do my tests...what i am noticing is the ubuntu patched version on 14.10 does run somewhat cooler then the mainline one does....The mainline version is called 3.15.0 (which i have installed on my 14.04) the ubuntu patched version of 14.10 is called: 3.15.0-6.11....

**Is there any (simple) and safe way to install the utopic ubuntu patched version on ubuntu 14.04?**
**If so, where do you get it from and how do you do it?**During the night You've opened several new ones...
I thought that You've asked for one specific kernel that worked on Your machine well and that You've tried...
As I see it, as kids and fashionable ones nowadays say, the easiest way is to fuhgeddaboudit.
Let alone the fact that You've driven me into deep offtopic (talking about 14.04) (for which I apologize to others) so I will refrain myself from getting any deeper... Only because at least one FA partcipated in this off-topic so I'll (I hope) be cleared.

Update&#8321;: It might be just linux-firmware that could be the reason that Your machine runs cooler with 14.10, think about that... ;

---

### Post by craig10x on 2014-07-06
Just wanted to let you all know that this morning, i upgraded into 14.10 development! I figured it was the one way i could get the ubuntu patched 3.15 kernel i wanted with little fuss...so now i have the kernel that solves my multimedia stability problem but at the same time, much lower temperatures then the "mainline" kernel....

I used the upgrade in terminal method for the first time (as suggested by d_cosner) and it worked GREAT...took only about 25 minutes and i lost nothing....everything i had before (apps, data, settings) is exactly the same as i had on 14.04...the terminal did tell me at the end that there were about 5 broken packages, but once i opened package manager and fixed them, i was good to go ;)

Then the updater had a huge slew of updates to do (apparently to complete the upgrade process) and that's when the 3.15.0-6 kernel was added! 
Now, if this will just run smooth to the release date i will be a very happy camper :D

If it does...then when 14.10 final is released i will either use the iso to re-install and carry over my data and apps or perhaps just do a clean install...wasn't really going to get back into development but i guess i just wanted that kernel so bad (lol)...

---

### Post by zika on 2014-07-11
There is an easier solution to the question asked here about installing Utopic kernel in Trusty: [B]ppa:canonical-kernel-team/ppa
[/B]So, if there is anybody that still needs help, just ask...

---

