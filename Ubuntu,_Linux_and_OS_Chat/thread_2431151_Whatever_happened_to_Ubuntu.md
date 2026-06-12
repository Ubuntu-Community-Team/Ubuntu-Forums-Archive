---
title: "Whatever happened to Ubuntu"
date: 2019-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by rashid-aden-omar on 2019-11-12
I have recently upgraded to version 19.10 and I can't say I'm very happy with it. From being unable to fractionally scale, poor Bluetooth support, audio defaulting to monitor rather than external speakers and overall sluggish and slowness. I'm aware of gnome having replaced Unity but it does seem like a backwards step to me. And this whole poor support for 4k monitors in this day and age is simply unacceptable.

---

### Post by Tadaen_Sylvermane on 2019-11-12
I would suggest you use 18.04 and stick with LTS releases. The middle ones are more like testing grounds in my experience, and I've never had any success with any of them. I've been pure LTS for a few years now. That would be my first place to start. Then work from there. In the case of Ubuntu latest doesn't mean greatest.

---

### Post by rashid-aden-omar on 2019-11-12
You do have a valid point. I think I will have to go down that route.

---

### Post by mörgæs on 2019-11-12
Was 19.10 an upgrade or a fresh install? If the former then I recommend a fresh install.

---

### Post by CatKiller on 2019-11-12
If you're reinstalling anyway, you might like KDE more than Gnome. Its window manager does support fractional scaling, it doesn't have the same performance issues as Gnome, and it has its own audio framework. Those aren't the reasons I use it, but they might be the reasons you do.

---

### Post by rashid-aden-omar on 2019-11-12
Catkiller would you recommend Kubuntu 19.10 or 18.04?

---

### Post by CatKiller on 2019-11-12
> **rashid-aden-omar said:**
> Catkiller would you recommend Kubuntu 19.10 or 18.04?

I'd recommend using the LTS releases always.

---

### Post by uRock on 2019-11-12
> **CatKiller said:**
> I'd recommend using the LTS releases always.

+1 the short term releases can be buggy on some systems, while systems with new technology may require the latest versions.

---

### Post by mastablasta on 2019-11-13
there are also issues and regressions in newer kernels. phoronix tests just showed it is all getting slower due to added security and other features & regressions.
more here: [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.0-Net-Perf-Bisect](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.0-Net-Perf-Bisect)

---

### Post by jetsam on 2019-11-13
Development focus is on the server editions...  Public good will comes from the desktop.

It, honestly, was always thus.  It's unfortunate, but Canonical simply needs to follow the revenue stream.

Señor Shuttleworth throws some spanners into the works; he has ideas, he really does...

But it's just enough to ensure that some stuff is gonna break.  Following the short term releases is, for the most part, reserved for the new and innocent, developers, and the truly masochistic, perhaps the odd true believer.

It's not all bad...  More than a few bugs get reported.  In some universe, they call that productive.

---

### Post by g3kxyz on 2019-11-13
Always go with LTS vs the beta builds of Linux if you don't want to run into issues like you mentioned.

---

### Post by lammert-nijhof on 2019-11-13
Instead of advising to change the distro or release, read the complaints and provide a real solution instead of fake ones:
- Audio default problem: install "Pulse Audio Volume Control" and go to the configuration tab and "off-Line" the profile for the audio of your monitor.
- Fractional Scaling: Try this solution: [http://ubuntuhandbook.org/index.php/2019/10/how-to-enable-fractional-scaling-in-ubuntu-19-10-eoan/](http://ubuntuhandbook.org/index.php/2019/10/how-to-enable-fractional-scaling-in-ubuntu-19-10-eoan/)

Yes, Ubuntu 19.10 will be beaten by Ubuntu 16.04 in responsiveness, but the Ubuntu Team is improving Gnome with each release and they deserve our support. 
I have no problems with Bluetooth support with my laptop and I connect a speaker and my Samsung S5 gsm without any problems. So the problem might be in your hardware, but without additional info, I can't say anything about it.

---

### Post by SeijiSensei on 2019-11-13
> **rashid-aden-omar said:**
> Catkiller would you recommend Kubuntu 19.10 or 18.04?
While, like Catkiller, I generally think most people should use LTS releases, I installed Kubuntu 19.04, and since updated it to 19.10, to see the latest version of the "Plasma" desktop. I've had zero issues with both interim releases on three different machines, two laptops and a desktop. I used "do-release-upgrade" to go from 19.04 to 19.10, too, which can sometimes be fraught with issues. I've had none. If you take this route, you'll want to move to 20.04, the next LTS release, in April.

---

### Post by speedwell68 on 2019-11-14
> **CatKiller said:**
> I'd recommend using the LTS releases always.

Always.  I used to upgrade every six months and then spend six months getting it working properly.

---

### Post by jetsam on 2019-11-14
> always. I used to upgrade every six months and then spend six months getting it working properly. 

lol :)

I was amazed when I tried a Gentoo based rolling release distro (Sabayon Linux) and it was 99% problem free in daily use.  I dunno how they did it/ do it...

Somehow it's less buggy than Ubuntu's short term releases, but they're having their users recompile from source and release updates nearly daily.  Almost all software is the latest release version of the upstream code.  Portage rocks, and they do have a "bleeding edge" process that prevents bad code from being released to the general public.  It's surprisingly stable, though.  I thought when I first installed that it couldn't possibly work, but I was wrong.  I ran it about 10 months I think, and had, if I recall corectly, two and a half minor issues arise over the course of that time.  Two I could address after a forum check, and the half issue was an annoyance that went away a week later...

---

### Post by rashid-aden-omar on 2019-11-14
I wasn't very familiar that non-LTS versions of Ubuntu can be this buggy. Well now I know.

---

### Post by rashid-aden-omar on 2019-11-14
> **lammert-nijhof said:**
> Instead of advising to change the distro or release, read the complaints and provide a real solution instead of fake ones:
- Audio default problem: install "Pulse Audio Volume Control" and go to the configuration tab and "off-Line" the profile for the audio of your monitor.
- Fractional Scaling: Try this solution: [http://ubuntuhandbook.org/index.php/2019/10/how-to-enable-fractional-scaling-in-ubuntu-19-10-eoan/](http://ubuntuhandbook.org/index.php/2019/10/how-to-enable-fractional-scaling-in-ubuntu-19-10-eoan/)

Yes, Ubuntu 19.10 will be beaten by Ubuntu 16.04 in responsiveness, but the Ubuntu Team is improving Gnome with each release and they deserve our support. 
I have no problems with Bluetooth support with my laptop and I connect a speaker and my Samsung S5 gsm without any problems. So the problem might be in your hardware, but without additional info, I can't say anything about it.

Thanks a lot. I will give that a go.

---

### Post by mörgæs on 2019-11-14
> **rashid-aden-omar said:**
> I wasn't very familiar that non-LTS versions of Ubuntu can be this buggy. Well now I know.

They aren't. Trust only your own experiments. If people can't point to a specific bug chances are they are just echoing conventional wisdom. 

I have installed all sorts of buntus during the latest 13 years and I can't see a systematic difference. One of the least stable was 12.04.

---

### Post by jetsam on 2019-11-14
Oh yes...  there's the forum effect.  I suffer from that for sure.  Seeing so many support threads over time makes you think everything is only ever broken all the time.  :)

---

### Post by CatKiller on 2019-11-14
> **rashid-aden-omar said:**
> I wasn't very familiar that non-LTS versions of Ubuntu can be this buggy. Well now I know.

They aren't buggy. What they are is *experimental*.

Before Canonical are going to support some shiny newfangled thing for five years they need somewhere to test it out. That somewhere is the interim releases.

If you're on the upgrade hamster wheel you'll have all sorts of things changed, or put in and taken out again, or whatever, every six months, between LTS releases. If you're on the LTS releases you just smoothly glide through that period with no major changes and all the security updates you might want.

The last interim before an LTS can be especially hairy, since that's the last opportunity for testing every crazy plan they might have had since the last LTS.

---

### Post by mastablasta on 2019-11-15
it's like windows Home and Windows enterprise.

on home the force updates on you. on enterprise the updates are deliberately help back for year (only security updates are made). so while i read about UI improvements in win 10 and black themes and such... they haven't reached my enterprise version for a year or 2 later and even then i had to ask for install of newer version.

stable OS means - functions and apps are kept on same working version (frozen). only security updates are made. 

in non LTS there are also feature updates and other bugfixes because nonLTS also features some new versions of apps that still need the bugs crushed.

---

### Post by Cushie on 2019-11-15
I have the same feeling about **19.10** version. The **Gnome 3.4** desktop appearance and function leaves a lot to be desired. I've spent two days trying to improve typeset (fonts in MS speak) examples are not described when making a selection it's just "suck and see" as are the icon sets. There are missing routines to cancel error messages in **G.Tweak** selecting themes. Hope it can be sorted soon
I think I should have a lie down now!

---

### Post by rashid-aden-omar on 2019-11-15
> **cushie said:**
> i have the same feeling about **19.10** version. The **gnome 3.4** desktop appearance and function leaves a lot to be desired. I've spent two days trying to improve typeset (fonts in ms speak) examples are not described when making a selection it's just "suck and see" as are the icon sets. There are missing routines to cancel error messages in **g.tweak** selecting themes. Hope it can be sorted soon
i think i should have a lie down now!

lol

---

### Post by mörgæs on 2019-11-16
> **CatKiller said:**
> They aren't buggy. What they are is *experimental*.

Before Canonical are going to support some shiny newfangled thing for five years they need somewhere to test it out. That somewhere is the interim releases.

If you're on the upgrade hamster wheel you'll have all sorts of things changed, or put in and taken out again, or whatever, every six months, between LTS releases. If you're on the LTS releases you just smoothly glide through that period with no major changes and all the security updates you might want.

The last interim before an LTS can be especially hairy, since that's the last opportunity for testing every crazy plan they might have had since the last LTS.

That might be what people could expect but reality is different.

If one takes a look at what software was released as part of [16.04]("https://en.wikipedia.org/wiki/Ubuntu_version_history#Ubuntu_16.04_LTS_(Xenial_Xerus)") I would say that this one was the experimental release. Compare 16.04 to 15.04, 15.10, 16.10 and 17.04 and one will see that these four were stable releases with only minor changes.

Long term support means exactly this: Support is longer. No more, no less. 

The only approach I can recommend: Test a number of releases on the specific hardware in question. Choose one based upon the test results. For Xubuntu 19.10 I can only give top marks. 

Noone in here has a foundation for guessing what will be shipped in future short- and long term releases so it doesn't make sense to broadly recommend this or that.

---

