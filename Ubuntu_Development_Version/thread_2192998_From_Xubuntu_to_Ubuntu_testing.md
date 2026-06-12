---
title: "From Xubuntu to Ubuntu testing"
date: 2013-12-10
forum: Ubuntu Development Version
---

### Post by OrangeCrate on 2013-12-10
I've been gone on an extended business trip for a couple weeks. I cleaned up and donated my test computer before I left, so, I needed to start over when I got home.

From this site,

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

I downloaded the 12/6 and 12/9 Xubuntu dailies. They loaded onto sticks just fine, but both hung, and wouldn't open. Today, I grabbed the 12/10 release, and it worked fine. Unfortunately it opened in a mid-east (?) language that I didn't understand.

So, I think I'll back off of Xubuntu 14.04 for a while, and will play with Ubuntu.

I downloaded the 12/10 daily, and it installed and booted just fine. As has been said by others, Unity is much cleaner, and more professional looking than I remember from the last time I used it.

---

### Post by PJs Ronin on 2013-12-10
I guess I picked one (or more) of those dates to download a Xubuntu image and got the same hangups.   And there I was thinking I was a total noob... sheesh!

---

### Post by Elfy on 2013-12-11
Lubuntu had the same issue I believe - some lightdm change caused it - it boots now - though you might find you need to supply a username/set the language ...

---

### Post by OrangeCrate on 2013-12-13
@ Elfy, I'm coming into my busy time of the year, with several extended trips planned. I'm going to back out of testing for a while. **I'll be back to Xubuntu testing some time in late January or early February** (though what I can contribute, of course, doesn't mean that much to the overall scheme of things).

Edit:

Probably not. I think I'm going to stay with Ubuntu for a while...

---

### Post by Elfy on 2013-12-14
> **OrangeCrate said:**
> @ Elfy, I'm coming into my busy time of the year, with several extended trips planned. I'm going to back out of testing for a while. I'll be back to Xubuntu testing some time in late January or early February (though what I can contribute, of course, doesn't mean that much to the overall scheme of things).

You'd be surprised how much 1 persons contribution is :)

From Trusty release to Thursday last, we'd had 7.3% of all the possible 64 bit image tests done and 13.2% of the 32 bit ones - by 5 and 4 people respectively ... 

Good luck with the trips and busy busy life and see you on the flipside.

---

### Post by NTL2009 on 2013-12-14
> **Elfy said:**
> Lubuntu had the same issue I believe - some lightdm change caused it - it boots now - though you might find you need to supply a username/set the language ...

I'd like to do some more testing. I tried the 2013-12-11 build for i386 32 bit. MD5SUM checks good, and I got to it to boot from USB stick created with Unetbootin. I found the login issue (requires xubuntu for name, no password), and it seems to help to select the language from the menu bar before logging in.

But when I tried to install to a couple spare partitions (separate /home) on my main machine (12.04 Xubuntu/xfce), the install failed ~ 80% into the copy files process (a couple minutes in). 

So I then tried the 'check disk' option at boot (which I understand will check file integrity of the USB drive), I get little rectangle characters on the bottom of the screen, nothing readable (maybe these are still in the mid-east language, but get displayed as rectangles?), so I can't tell what is going on.

Bottom line, I'm not really looking for help in troubleshooting this particular problem, more just wondering if these are known issues that might be fixed in an upcoming release. If so, I'll hold off on further attempts until those are resolved. Like I said, I'd like to help do some testing, but I'm not really knowledgeable enough to handle some of the more 'bleeding edge' issues. Just looking for a point where maybe it's a bit more stable. Make sense? I didn't see any notes on what changes/fixes are in the dailies.

-NTL2009

---

### Post by OrangeCrate on 2013-12-18
> **Elfy said:**
> You'd be surprised how much 1 persons contribution is :)

From Trusty release to Thursday last, we'd had 7.3% of all the possible 64 bit image tests done and 13.2% of the 32 bit ones - by 5 and 4 people respectively ... 

Good luck with the trips and busy busy life and see you on the flipside.

I assume the body count of testers will increase after the release of an Alpha (tomorrow, I think), and more after a Beta release, but, the pre-Alpha count was/is pretty bleak.

---

### Post by Elfy on 2013-12-19
It increased a bit - at the last check we'd had 7 people (not counting me) report results.

---

### Post by Elfy on 2013-12-28
:)

---

### Post by OrangeCrate on 2014-01-11
Update...

I've been in and out of the country for the past four weeks, and as I indicated earlier in this thread, I loaded the Ubuntu version of Trusty (12/10 daily), and took it with me, to give it a real world workout.

I've been using it as my production machine, with no backup other than the final of 13.10 on a stick. This computer is my four year old Lenovo T400, with the 2.4 GHz Core 2 Duo, 4 GB RAM, and the Mobile Intel GM45 Express Chipset. The only thing I have done is to load the updates once a day. Otherwise, I just use it. Day-to-day programs include Chrome, Thunderbird, Writer, and Ubuntu One.

I am happy to report, that though we're still at the "Alpha" development stage, so to speak, I have had absolutely no problems with Trusty. It just works. There are a few fit and finish issues to be ironed out (certainly not unexpected), but, the guts of this release so far are superb. It feels really solid, and it's as quick as a weasel.

---

### Post by ventrical on 2014-01-11
> **Elfy said:**
> It increased a bit - at the last check we'd had 7 people (not counting me) report results.


 I test xubuntu all the time .. but that does not mean I always report results.

---

### Post by Elfy on 2014-01-12
> **ventrical said:**
> I test xubuntu all the time .. but that does not mean I always report results.

I'd guess that other's do the same - however as far as we are concerned - the only count we have is tracker reports - the numbers of people testing is very low.

Edit - mind you - after looking at the results for other flavours - it seems we get the best results, Ubuntu is less too, though I'd guess this is tempered by the autopilot testing which is skewed in their favour.

So perhaps after all it's a bit more  \\:D/ than I thought ...

---

### Post by craig10x on 2014-01-12
I'm using 14.04 (with unity) as my main, everyday system and in fact have nothing else and it has been VERY reliable except for the small glitches we all have been experiencing and i could not agree more with OrangeCrate's comments...i think it is going to an EXCELLENT release...and yep, everything is very fast...even the web surfing i have noticed...it's like everything is on steroids :D

---

### Post by OrangeCrate on 2014-01-12
> **craig10x said:**
> I'm using 14.04 (with unity) as my main, everyday system and in fact have nothing else and it has been VERY reliable except for the small glitches we all have been experiencing and i could not agree more with OrangeCrate's comments...i think it is going to an EXCELLENT release...and yep, everything is very fast...even the web surfing i have noticed...it's like everything is on steroids :D

I got a bit long winded with my last post (#10), so, I just shortened it up a bit. Glad to hear others are sharing similar experiences to mine. I'm leaving on another two week trip tomorrow, and I've decided to try another computer to further put 14.04 through it's paces. This one will start with the 1/11 daily, on a 30 GB partition cut out of my Core i5 Lenovo X220 (also with an onboard Intel chipset). I do have Windows 7 on this laptop, but, I won't use it, unless Trusty borks for some reason, which I certainly don't expect.

I'll update this thread again sometime...

---

### Post by Elfy on 2014-01-12
Nice to see you in and out reporting on using trusty in the real world :)

---

### Post by OrangeCrate on 2014-01-12
> **Elfy said:**
> Nice to see you in and out reporting on using trusty in the real world :)

Thanks.

I'm typing this from a stick loaded with the 1/11 Xubuntu daily. I mentioned early on in this dev cycle, in another thread, that I was having problems with goofy borders on windows with Xubuntu on both 14.04 and 13.10. I didn't read that anyone from the Nvidia crowd was having a similar problem, so, I assume it was Intel related. It was easy to replicate by just using the OS, but, everytime I tried to take a screenshot of them, they'd disappear when I opened the screenshot program. I don't have this issue with Ubuntu, just Xubuntu.

I'll play with this for a while, and if I don't have the problem today, I'll go ahead and install this daily on the T400, along with Ubuntu, and I will take them both with me on this next trip, and leave the X220 at home. Because it has Windows on it, my wife uses that one more than me anyway.

Later...

---

### Post by OrangeCrate on 2014-01-12
> **OrangeCrate said:**
> Thanks.

I'm typing this from a stick loaded with the 1/11 Xubuntu daily. I mentioned early on in this dev cycle, in another thread, that **I was having problems with goofy borders on windows with Xubuntu on both 14.04 and 13.10.** I didn't read that anyone from the Nvidia crowd was having a similar problem, so, I assume it was Intel related. It was easy to replicate by just using the OS, but, everytime I tried to take a screenshot of them, they'd disappear when I opened the screenshot program. I don't have this issue with Ubuntu, just Xubuntu.

I'll play with this for a while, and if I don't have the problem today, I'll go ahead and install this daily on the T400, along with Ubuntu, and I will take them both with me on this next trip, and leave the X220 at home. Because it has Windows on it, my wife uses that one more than me anyway.

Later...

I didn't see them on the USB drive, so, I went ahead and installed, and, they're still there. For the time being, Xubuntu is a no go for me to use on a daily basis. I'll leave the partition on the machine until we hit final, to see if the situation sorts itself out...

---

### Post by Elfy on 2014-01-12
> **OrangeCrate said:**
> I didn't see them on the USB drive, so, I went ahead and installed, and, they're still there. For the time being, Xubuntu is a no go for me to use on a daily basis. I'll leave the partition on the machine until we hit final, to see if the situation sorts itself out...

screenshot of what you mean when you get time will help :)

---

### Post by OrangeCrate on 2014-01-12
> **OrangeCrate said:**
> Thanks.

I'm typing this from a stick loaded with the 1/11 Xubuntu daily. I mentioned early on in this dev cycle, in another thread, that I was having problems with goofy borders on windows with Xubuntu on both 14.04 and 13.10. I didn't read that anyone from the Nvidia crowd was having a similar problem, so, I assume it was Intel related. **It was easy to replicate by just using the OS, but, everytime I tried to take a screenshot of them, they'd disappear when I opened the screenshot program.** I don't have this issue with Ubuntu, just Xubuntu.

I'll play with this for a while, and if I don't have the problem today, I'll go ahead and install this daily on the T400, along with Ubuntu, and I will take them both with me on this next trip, and leave the X220 at home. Because it has Windows on it, my wife uses that one more than me anyway.

Later...

> **Elfy said:**
> screenshot of what you mean when you get time will help :)

See my comment above.

---

### Post by Elfy on 2014-01-12
sorry - my bad, I had similar corruption at login screen - resorted to camera in the end

---

### Post by OrangeCrate on 2014-01-12
> **Elfy said:**
> sorry - my bad, I had similar corruption at login screen - resorted to camera in the end

No bad, I skim most posts too.

I'm not into digital cameras, and I gave my Droid smartphone to one of my son-in-laws, so for now, I have a regular cell phone with a great slide out QUERTY keyboard, but, a really, really crappy camera.

I tried to take a pic of the windows borders, but the resolution is not good enough to pick them up clearly. Anyway, like I said, I'll keep the partition, and will continue to update it. If anything changes, I'll post an update here in this thread.

---

### Post by OrangeCrate on 2014-01-25
Update:

The rendering problem with the borders seems to be a ghost in the machine for my T400. Xubuntu 12.04 is not a problem on my T43, and Xubuntu 14.04 is not a problem on my X220. Oh well, such is life.

Moving on...

---

### Post by OrangeCrate on 2014-01-26
Just a casual comment...
 
I was looking at a bug report on Launchpad this morning, and I noticed an unusual number of "me too" posts after the bug had been confirmed. I would hope that people would realize that "piling on" to bug reports with those type of posts is considered poor etiquette, but, apparently not.

I'm always busy doing other things, but, when I have the time to research something I've noticed on a development release, I always seem to be tail end Charlie. I don't have any exotic bits and pieces on or in my computers, so, I have found, that when I do see a bug, by the time I look at it, many times it's been kicked to death on Launchpad.

Personally, if I see that the bug has been confirmed, I just move on, and I would hope others would adopt this method of bug hunting. Reading the stickies at the top of this forum, which provide some guidance on what, when, why, where, and how, of all things testing related, would be most helpful for people wanting to be involved with the testing process. Searching out other articles, and wiki entries, would be helpful too.

---

### Post by cariboo on 2014-01-26
If I run into a bug report that affects me, I usually just click the affects me too link, then if I want to add a comment I do that too. I also subscribe to bugs that affects my system, so that I can keep an eye on what is happening as far as the bug is concerned.

---

### Post by OrangeCrate on 2014-01-26
> **cariboo907 said:**
> If I run into a bug report that affects me, I usually just click the affects me too link, then if I want to add a comment I do that too. I also subscribe to bugs that affects my system, so that I can keep an eye on what is happening as far as the bug is concerned.

Those are good ideas, thanks for posting.

---

### Post by OrangeCrate on 2014-02-06
> **OrangeCrate said:**
> Update:

The **rendering problem** with the borders seems to be a ghost in the machine for my **T400**. Xubuntu 12.04 is not a problem on my T43, and Xubuntu 14.04 is not a problem on my X220. Oh well, such is life.

Moving on...



I downloaded and installed the 2/4 Xubuntu 14.04 daily, to check if there were still problems with the borders on my T400. There are, so I'll try again closer to release.

---

### Post by OrangeCrate on 2014-02-16
According to the following Xubuntu blog post, threads/posts like these are unappreciated, so, I'm marking this thread "solved".

> While testing the developer versions in any way possible is a great idea, there isn’t much benefit in messages telling us Xubuntu works on machine X, or there were no problems with upgrading machine Y.

[http://xubuntu.org/blog/](http://xubuntu.org/blog/)

---

### Post by Elfy on 2014-02-16
Threads like this are appreciated ;)

I'd not post in them if they weren't. The blog post is a general push to try and get reports of bugs is all.

---

### Post by OrangeCrate on 2014-02-16
> **Elfy said:**
> **Threads like this are appreciated** ;)

I'd not post in them if they weren't. The blog post is a general push to try and get reports of bugs is all.

Nice of you to say Elfy, but, this thread is done. Good luck with the balance of your dev cycle.

---

### Post by OrangeCrate on 2014-03-04
> **OrangeCrate said:**
> Nice of you to say Elfy, but, **this thread is done**. Good luck with the balance of your dev cycle.

I lied.

For anyone that was following this thread, with a similar rendering issue, I downloaded yesterday's daily of Xubuntu 14.04, and the odd looking borders are finally gone (an ongoing problem since 13.04).

---

### Post by VMC on 2014-03-04
I've been reading this topic from the beginning, and enjoyed your input. Thanks for the last link. From earlier on 14.04 Xubuntu appeared similar to previous updates. I haven't been reading Xubuntu or XFCE blogs until now. The Whisker Menu was a surprise. In fact I thought I needed to tweak it to get back my "normal" menu.

I do read the changes Archives from time to time, but never paid much attention to the obvious. That link revealed my lack of attention: "
[LIST]
[*]The panel layout is updated, and now uses Whiskermenu as the default menu"
[/LIST]
Since I have an older, aka nvidia 6150 graphics, and nouveau doesn't cut if any more, Xubuntu with nvidia drivers works the best. Ubuntu is not near as smooth as Xubuntu, so  I'll be sticking with Xubuntu and keeping up on that blog.

---

### Post by Elfy on 2014-03-04
> **OrangeCrate said:**
> I lied.

For anyone that was following this thread, with a similar rendering issue, I downloaded yesterday's daily of Xubuntu 14.04, and the odd looking borders are finally gone (an ongoing problem since 13.04).

Thanks for letting us know your odd borders were no more :)

---

### Post by OrangeCrate on 2014-04-16
> **Elfy said:**
> Thanks for letting us know your odd borders were no more :)

I just ran Xubuntu 14.04 through it's paces. It's a thing of beauty, and definitely a keeper. Congrats to you, and all involved in this dev cycle.

---

