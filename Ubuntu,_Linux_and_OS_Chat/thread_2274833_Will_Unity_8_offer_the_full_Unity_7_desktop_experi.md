---
title: "Will Unity 8 offer the full Unity 7 desktop experience or will it be dumbed down?"
date: 2015-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by residualbit on 2015-04-22
Like the title says, I'm wondering what end-stage, ready-for-desktop Unity 8 will look like and whether it will break the Unity 7 workflow and additionally, things like shortcuts, window management, etc.

As other major OS's strive towards a convergence, it seems like the desktop experience gets nerfed in the name of 'simplicity.'

In short, for me, Unity on the deskop is perfect right now from a daily usage, workflow, and customization perspective. Will Unity 8 be at least on-par with that?

---

### Post by mc4man on 2015-04-22
I don't think anyone can say right now as the current unity8 (next) on a Desktop is a small step above worthless. I'd imagine that eventually they'll come up with something decent though no doubt it will be disappointing to a fair number of current Ubuntu desktop users. (myself included

In any event progress towards that is slower than previously anticipated so it's pretty much assured that 16.04 LTS will include unity7/compiz as an option for Desktop users.

---

### Post by residualbit on 2015-04-22
Makes sense. I've been playing around with Unity 8 off and on. I actually have it running on my nexus 7 and it's pretty awesome there. Previewing on the desktop though is another story altogether...I think I may have actually said "oh god" out loud when I first booted into it. I'm all for the convergence aspect, but not at the cost of a neutered desktop experience. The way I see it, at the very worst, if things never start  to look up, I have 4 more years with 14.04 and plenty of time to start adjusting to a different DE if need be. We shall see!

---

### Post by ian-weisser on 2015-04-22
See [http://news.softpedia.com/news/Unity-8-Won-t-Be-Very-Visually-Very-Different-from-Unity-7-477711.shtml](http://news.softpedia.com/news/Unity-8-Won-t-Be-Very-Visually-Very-Different-from-Unity-7-477711.shtml)

---

### Post by monkeybrain20122 on 2015-04-22
> **ian-weisser said:**
> See [http://news.softpedia.com/news/Unity-8-Won-t-Be-Very-Visually-Very-Different-from-Unity-7-477711.shtml](http://news.softpedia.com/news/Unity-8-Won-t-Be-Very-Visually-Very-Different-from-Unity-7-477711.shtml)

Yes, *visually*, but OP is interested in *functionally*, if any, as far as I can tell.;)

---

### Post by grahammechanical on 2015-04-22
The target has been set. If they do not hit the target then convergence will have failed.

Canonical does not want to maintain one code base for mobile devices and another code base for desktops and laptops. I do not think that Unity 7 can run in MIr. That is why they have developed Unity 8. 

Canonical definitely wants that Ubuntu super phone that can be a phone or tablet or PC. They see it as something that commercial enterprises will buy because it will reduce the IT costs. 

I am not sure about this comment

> Unity 8 is right now scheduled to make a default appearance in Ubuntu 16.04 LTS,

I have heard talk of Unity 7 being default with Unity 8 as log in option. There is a Ubuntu Desktop Next ISO image we can install. That uses the Xserver and LightDM up until the login screen. Then after logging in the switch is made to Mir and Unity 8 at its present stage of development on the desktop. Something similar might have to be done if 16.04 is going to give users the option of Unity 7 or Unity 8.

A lot of work has to be done if Unity 8 is going to be default in 16.04. We will see what 15.10 brings. Meanwhile, do not mess up an LTS.

Regards.

---

### Post by monkeybrain20122 on 2015-04-22
> **grahammechanical said:**
> The target has been set. If they do not hit the target then convergence will have failed.

Canonical does not want to maintain one code base for mobile devices and another code base for desktops and laptops. I do not think that Unity 7 can run in MIr. That is why they have developed Unity 8. 

Canonical definitely wants that Ubuntu super phone that can be a phone or tablet or PC. They see it as something that commercial enterprises will buy because it will reduce the IT costs. 

I am not sure about this comment



I have heard talk of Unity 7 being default with Unity 8 as log in option. There is a Ubuntu Desktop Next ISO image we can install. That uses the Xserver and LightDM up until the login screen. Then after logging in the switch is made to Mir and Unity 8 at its present stage of development on the desktop. Something similar might have to be done if 16.04 is going to give users the option of Unity 7 or Unity 8.

A lot of work has to be done if Unity 8 is going to be default in 16.04. We will see what 15.10 brings. Meanwhile, do not mess up an LTS.

Regards.

So how far is mir along the way? Do you think there is a chance that it will be default in 16.04? I think that even in the most optimistic scenario Mir is not likely to replace X in the next LTS and even if it does X will still be an option. if 16.04 runs X or have an option to use X would it make sense to either run unity 7 as default or as an option? I can be wrong but it seems that they are not working on xmir anymore and put their energy in mir proper instead.

---

### Post by grahammechanical on 2015-04-22
I do not have any influence but if someone was to ask my advice I would say, do not risk messing up the next LTS. Which means, as far as I can see, at least two things have to happen by the last week of April 2016

1) Mir has to be tested and proved as a replacement for X.
2) Unity 8 will have to be providing a very similar if not the same user experience as Unity 7.

There is another issue and Xmir is proving useful. Some applications such as Libreoffice run on X. They will need to run on Mir. They can be made to run on Mir using Xmir.

Check out these videos. See the one from last December

[http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986/10](http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986/10)

In this video the developer has put the phone in desktop mode. He is doing it in the Ubuntu emulator

[http://discourse.ubuntu.com/t/ubuntu-phone-in-desktop-mode/2045](http://discourse.ubuntu.com/t/ubuntu-phone-in-desktop-mode/2045)

It will very interesting following the development release over the next 12 months.

Regards.

P.S. There were some comments on yesterday's Community Q & A on this subject

[https://www.youtube.com/watch?v=t6IYI1Ax4mA](https://www.youtube.com/watch?v=t6IYI1Ax4mA)

---

### Post by ventrical on 2015-04-23
If this all be the case then it is most likely that xubuntu and lubuntu will be the GO TO desktop experiences during testing and , up to  16.04 release. I'll miss testing unity7(types) on the desktop. It is good that we have it LTS until 2019.

Regards.

---

### Post by mc4man on 2015-04-23
> **0xnate said:**
> Makes sense. I've been playing around with Unity 8 off and on. I actually have it running on my nexus 7 and it's pretty awesome there. Previewing on the desktop though is another story altogether...I think I may have actually said "oh god" out loud when I first booted into it. I'm all for the convergence aspect, but not at the cost of a neutered desktop experience. The way I see it, at the very worst, if things never start  to look up, I have 4 more years with 14.04 and plenty of time to start adjusting to a different DE if need be. We shall see!
Myself also sticking with 14.04 though keeping 'contact' with dev to 16.04. So then you could run 16.04/7/compiz for maybe 5yrs. if 8 isn't suitable.
(- saying maybe because I figure at some point Ubuntu needs to be a going concern on phones/tablets or what's the point of it continuing other than  purely community..

I've 2 nexus7's, one in daily use, the other just occasional updates & left around  50% charge. Maybe I'll try Ubuntu on the daily one once it seems to have reached the crest of it's lifetime.

---

### Post by vtpoet2 on 2015-04-24
I try Unity7 with each new iteration, but continue disliking it because [insert complaint]. I'm an XFCE & KDE convert.

But Unity8 looks fascinating. I can't wait to try it. And each time Canonical delays its implementation I just want to go out and kick something. I can't get excited about yet another release of an updated-obsolete DE, which is really how I think of Unity7 -- a cork in the bottom of the boat.

I know the hurdles, but really, can we just get on with it? Can we just try it? Soon?

---

### Post by mc4man on 2015-04-24
> **vtpoet2 said:**
> I try Unity7 with each new iteration, but continue disliking it because [insert complaint]. I'm an XFCE & KDE convert.

But Unity8 looks fascinating. I can't wait to try it. And each time Canonical delays its implementation I just want to go out and kick something. I can't get excited about yet another release of an updated-obsolete DE, which is really how I think of Unity7 -- a cork in the bottom of the boat.

I know the hurdles, but really, can we just get on with it? Can we just try it? Soon?
you're free to try it all you want [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)
or use windows8/10, likely similar

---

### Post by vtpoet2 on 2015-04-24
Yeah I''m aware of these daily builds, but you can't judge a cake before it's been baked. 

I'm waiting for the supported version.

However, if you still prefer windows8/10 or whatever works for you, I'm okay with that. I've really gotten so that I love the flexibility of linux.

---

### Post by monkeybrain20122 on 2015-04-26
Not sure how up to date this is (posted oct 2014)

[http://mhall119.com/2014/10/unity-8-desktop/](http://mhall119.com/2014/10/unity-8-desktop/)

> 16.04 LTS: Unity 8 default / Unity 7 as an option
..
Unity 7 and Compiz have a team dedicated to maintenance and bug fixes  and so the quality of it continues to improve with every release.  For  example; windows switching workspaces when a monitor gets unplugged is  fixed, if you have a mouse with 6 buttons it works, support for the new  version of Metacity (incase you want to use the Gnome2 desktop) &#8211; added  (and incidentally, a lot of that work was done by a community  contributor &#8211; thanks [Alberts]("https://launchpad.net/%7Ealbertsmuktupavels")!)
 Unity 7 is the desktop environment for a lot of software developers,  devops gurus, cloud platform managers and millions of users who rely on  it to help them with their everyday computing.  We don&#8217;t want to stop  you being able to get work done.  This is why we continue to maintain  Unity 7 while we develop Unity 8.  If you want to take Unity 8 for a  spin and see how its coming along then you can; if you want to get your  work done, we&#8217;re making that experience better for you every day.  Best  of all, both of these options are available to you with no detriment to  the other.
 

As long as unity7 is maintained and kept as an option for 16.04 transition should be smooth.

---

