---
title: "Switching from KDE to Gnome in order to hit the next LTS release?"
date: 2008-01-05
forum: Server Platforms
---

### Post by MJN on 2008-01-05
Warning: I've got lots of thoughts/queries in my head and there's every chance there's going to be some waffling, so do please only read on if you've got some time to spare!! Your thoughts however would be greatly appreciated. :)

I currently run a server for family and friends providing e-mail, web hosting and backup facilities, in addition to meeting my own needs of a file server, media centre, and CCTV security monitoring. It's probably a fairly typical setup to many around here.

Anyway, whilst there is no commercial reliance on my system there is a heavy personal one and this, to me, is very important and hence I'm currently running Dapper 6.06 as an ultra-stable platform. This particular server also provides some day-to-day service as a general purpose PC and hence runs a GUI desktop environment - I use KDE as a personal preference over Gnome and hence fall under the Kubuntu camp.

I have decided to replace my somewhat ageing hardware in the not-too-distant future (my current stuff copes, but it would be nice to have a little more headroom with regards to capability) and my intention was to wait until 8.04 LTS was released however it is my understanding that there won't now be a Kubuntu 8.04 LTS given the current developments of KDE4 meaning that come April it will not be in a suitable state to allow  an LTS badge to be used.

This, to me, is somewhat of a nail-in-the-coffin for Kubuntu - perhaps that's a little melodramatic but whilst I've preferred KDE over Gnome (purely a familiarity thing I'm sure) I've always considered Kubuntu to be somewhat of a 2nd class citizen to Ubuntu and this has worried me for some time. I understand that supporting the KDE 3.5 series for another 3 years is a difficult one to do, and that KDE 4 is in no fit state to be completely supportable, however this difficult situation only reinforces my desire to move to Gnome.

Hence, I am considering switching to Gnome and stick to the Ubuntu path, taking up 8.04 LTS along the way.

From a server perspective there will be little differences for me - the vast majority of my 'server services' are desktop-independent however I use a number of KDE-centric apps such as k3b, Kompozer, digiKam, krita etc and so was wondering if I should attempt to continue to use these apps under Gnome (is it that simple?) or would you recommend getting to known and learn their Gnome counterparts?

See, I told you it would be all waffle for what is ultimately probably a simple question, however I would be also interested to hear your thoughts, and plans, with regards to the lack of a Kubuntu 8.04 *LTS* release and whether or not it makes any difference to you?

As an aside, it was my understanding that it would've been a simple dist-upgrade from 6.06 to 8.04 without any interim stages but given the lack of the LTS status (for Kubuntu) does anyone know if this is still to be the case?

Cheers,

Mathew

---

### Post by cryptoD on 2008-01-05
I'm a Gnome user but i use a lot of KDE apps because there are no similar apps in Gnome, they work fine just like in KDE!. I think that you should switch to Gnome and keep using your KDE apps.

---

### Post by MJN on 2008-01-05
That's good to hear - thanks.

I'm trying Gnome now on my laptop and I'm struggling a bit. I'm putting it down to unfamiliarity so will keep an open mind for a while longer!

Mathew

---

### Post by Dark Hornet on 2008-01-05
I have been using Gnome for a couple of years, and I love it.  As far as running KDE apps on Gnome, for the most part you shouldn't have any issues...with that said, there are some that (for me) have been an issue--such as Ktorrent--this program under Gnome tends to freeze my entire system.  So for the most part you should be fine, but watch out...some may get you...Good Luck, and glad to hear you are moving to Gnome!

---

### Post by jrusso2 on 2008-01-05
You could not pay me to use gnome it just is way to limiting for me.

---

### Post by Dark Hornet on 2008-01-05
> **jrusso2 said:**
> You could not pay me to use gnome it just is way to limiting for me.

In what way...I have no problems changing anything...I find that it is VERY flexible...now in relation to KDE, I am not very qualified to compare them, as my only experience with KDE was a one week time frame about 2 years ago.

I have a feeling though that Gnome and KDE are both just as configurable...I think it boils down to personal preference.

---

### Post by p_quarles on 2008-01-05
> **MJN said:**
> As an aside, it was my understanding that it would've been a simple dist-upgrade from 6.06 to 8.04 without any interim stages but given the lack of the LTS status (for Kubuntu) does anyone know if this is still to be the case?
It shouldn't be. The differences between the three main Ubuntu flavors are just the metapackages: ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop. They are not fundamentally different distributions. 

So, *if,* for some reason, the dist-upgrade doesn't work, you could always simply install the ubuntu-desktop metapackage and upgrade from there. (I seriously doubt that will be necessary). 

Likewise, Kubuntu 8.04 will continue to be supported for the normal cycle (18 months). So, really, you have until October of next year before you need to make any decisions.

---

### Post by MJN on 2008-01-05
Are you saying it *will* be a direct dist-upgrade from 6.06 to 8.04, or not?

Sorry for the misunderstanding... it's late and I've had beer! ;)

With regards to the dist-upgrade not working, I'd be screwed - these things usually fail quite catastrophically. (this question is asked notwithstanding the fact that I'm considering a hardware upgrade anyway as mentioned hence will be doing a standard backup/reinstall anyway, but I'm still curious).

Mathew

---

### Post by p_quarles on 2008-01-05
> **MJN said:**
> Are you saying it *will* be a direct dist-upgrade from 6.06 to 8.04, or not?

Sorry for the misunderstanding... it's late and I've had beer! ;)
Hey, no problem. It's early evening here, and I've also had beer. ;)

> With regards to the dist-upgrade not working, I'd be screwed - these things usually fail quite catastrophically. (this question is asked notwithstanding the fact that I'm considering a hardware upgrade anyway as mentioned hence will be doing a standard backup/reinstall anyway, but I'm still curious).

Mathew
There will almost certainly be better information about whether or not you can upgrade directly from Kubuntu 6.06 to Kubuntu 8.04 when the date nears. As of now, I don't see how it would be logistically possible for the devs to enable this feature for Ubuntu without enabling it for supported derivatives. 

What I'm saying, though, is that if there is *any *question about that, you could simply run:
```
sudo apt-get install ubuntu-desktop
```
in your 6.06 installation, select GDM when it asks, and you will then have the Gnome edition of Ubuntu. That should eliminate all doubt about the ability to dist-upgrade to 8.04.

---

### Post by snickers295 on 2008-01-05
i have used several kde apps in gnome and it works fine.
i liked kubuntu for awhile but it was always unstable for me so the fact that they won't be a LTS is kinda upsetting, i will just have to stick with Ubuntu.

---

### Post by MJN on 2008-01-05
I gotcha p_quarles, thanks.

That particular question was more out of curiosity, as it will unlikely affect me now anyway if I do replace the machine.

I think my main concern is based on the premise that LTS releases are more than just a 3yr supported platform, but also an acknowledgment that that particular release is intended to be stable beyond any other 'interim' release which tend to focus on having the latest-and-greatest. Hence, does the lack of a Kubuntu LTS (for 8.04 at least) mean not only that it will not be supported for 3yrs (this much is clear) but also that it is not making the same level of claim regarding outright stability?

I'm probably asking too much, too early, and perhaps in the wrong place(!), but I am curious nevertheless!

Mathew

---

### Post by snickers295 on 2008-01-05
> **MJN said:**
> I gotcha p_quarles, thanks.

That particular question was more out of curiosity, as it will unlikely affect me now anyway if I do replace the machine.

I think my main concern is based on the premise that LTS releases are more than just a 3yr supported platform, but also an acknowledgment that that particular release is intended to be stable beyond any other 'interim' release which tend to focus on having the latest-and-greatest. Hence, does the lack of a Kubuntu LTS (for 8.04 at least) mean not only that it will not be supported for 3yrs (this much is clear) but also that it is not making the same level of claim regarding outright stability?

I'm probably asking too much, too early, and perhaps in the wrong place(!), but I am curious nevertheless!

Mathew
curiosity is great. thats how you learn things.
if not for it, i would be stuck using windows xp and knowing squat about computers.

---

### Post by p_quarles on 2008-01-05
> **MJN said:**
> I gotcha p_quarles, thanks.

That particular question was more out of curiosity, as it will unlikely affect me now anyway if I do replace the machine.

I think my main concern is based on the premise that LTS releases are more than just a 3yr supported platform, but also an acknowledgment that that particular release is intended to be stable beyond any other 'interim' release which tend to focus on having the latest-and-greatest. Hence, does the lack of a Kubuntu LTS (for 8.04 at least) mean not only that it will not be supported for 3yrs (this much is clear) but also that it is not making the same level of claim regarding outright stability?

I'm probably asking too much, too early, and perhaps in the wrong place(!), but I am curious nevertheless!

Mathew
My current understanding is that 8.04 will include both KDE 3.5.8 and KDE 4.0 in the repositories. The former is stable, but isn't likely to be maintained through 2011, and the latter is completely untested at this point. If this is correct (and we'll know better in March), stability shouldn't be a concern. 

I use Fluxbox as a WM, on top of KDM, and with mostly KDE apps, so I can vouch for the fact that the current KDE is stable, and since it isn't getting much attention from developers at the moment, should stay that way for some time.

---

### Post by MJN on 2008-01-05
> **p_quarles said:**
> My current understanding is that 8.04 will include both KDE 3.5.8 and KDE 4.0 in the repositories.

I suppose that makes sense. Aside from those wanting the LTS 'badge' it does at least provide the ability to satisfy those that require stability and/or those that want something more uptodate.

It would however raise the potential for a split distribution given that applications developed for KDE 3.x may well not work under 4.x and, even more likely, vice versa.

Whilst part of me is wanting to avoid the issue altogether and give Gnome a chance another part is saying 'no - stick with what you know/like' as I'm just not liking Gnome at all so far. Again though, unfamiliarity could well be my only enemy here.

Mathew

---

### Post by snickers295 on 2008-01-05
> **MJN said:**
> I suppose that makes sense. Aside from those wanting the LTS 'badge' it does at least provide the ability to satisfy those that require stability and/or those that want something more uptodate.

It would however raise the potential for a split distribution given that applications developed for KDE 3.x may well not work under 4.x and, even more likely, vice versa.

Whilst part of me is wanting to avoid the issue altogether and give Gnome a chance another part is saying 'no - stick with what you know/like' as I'm just not liking Gnome at all so far. Again though, unfamiliarity could well be my only enemy here.

Mathew
hey, at least your not forced to use kde 2 like i did.
when i started linux, i started with suse 7.3 and had dial up so couldn't download and couldn't use shipet or whatever its called.

---

