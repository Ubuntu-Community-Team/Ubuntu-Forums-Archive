---
title: "Are upgrades smoother not staying with LTS?"
date: 2014-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Lester_Ingber on 2014-10-24
I've had Ubunutu x64 on my VPS for quite a few years. Right now I'm on 14.04.1 LTS.  Most of the time upgrades have not at all been smooth.  I was trying to keep up with the latest upgrades, but the real issue for me now is to ensure the smoothest path for future upgrades.

I am looking for feedback on whether simply upgrading only LTS (every other year?) is a smoother path to take rather than upgrading every six months.

Thanks.

---

### Post by thiebaude on 2014-10-24
All I do is clean installs of Ubuntu every 6 months.:p

---

### Post by grahammechanical on 2014-10-24
It all depends upon how much you modify the user interface and whether you install software that is not available in the software centre. Some of us do recommend a fresh install. My advice if you are seriously considering your options for the next 18 months is to create another 20GB partition and practice the upgrade on an installation in that partition before trying it on your main install.

Ubuntu 15.04 will still be using Xserver, LightDM, Compiz and Unity 7 but from Ubuntu 15.10 on to 16.04 Ubuntu will be using Mir and Unity 8 instead. How well upgrades will then work I have no idea. My advice is to stick with 14.04 unless you want to track Ubuntu development towards convergence. Even then do not do it with your only install of Ubuntu.

Regards

---

### Post by craig10x on 2014-10-24
I think it is the opposite...6 month upgrades are probably much smoother and more reliable then LTS upgrades because soooo much changes over 2 years as opposed to 6 months...
I have been doing upgrades every 6 months for the last 2 cycles and they have been 100% perfect...but then, i don't do major modification to my system...and i think that helps also...
Best way to do it (i have found) is with the software updater and not upgrading from the iso disc...and always best to turn off any ppas temporarily while upgrade is being done...

---

### Post by vasa1 on 2014-10-24
I upgraded from 14.04 to 14.10 and forgot to disable the google chrome ppa. No problem. Just went back and re-enabled it because the upgrade process warned me that ppas would be disabled.

The only issue was something involving "syslinux-themes-debian". I had to run **sudo apt-get install --reinstall syslinux-themes-debian** to sort that out.

---

### Post by speedwell68 on 2014-10-24
> **thiebaude said:**
> All I do is clean installs of Ubuntu every 6 months.:p

I wish I had that much time on my hands.

---

### Post by Mike_Walsh on 2014-10-24
> **speedwell68 said:**
> I wish I had that much time on my hands.

A BIG +1. =d>

Seriously; some of us DO have other things going on in our lives... #-o:roll:

Regards,

Mike.

---

### Post by sffvba[e0rt on 2014-10-24
> **speedwell68 said:**
> I wish I had that much time on my hands.

> **Mike_Walsh said:**
> A BIG +1. =d>

Seriously; some of us DO have other things going on in our lives... #-o:roll:



So I guess my forays into 4 different OS's before lunch some day's explains why I don't ever get anything (else) done :p

---

### Post by vasa1 on 2014-10-24
I'm sure it's not worth pointing out that LTS releases are what they are, in part, because of the feedback provided by users of the intermediate versions.

I can't code.
I won't test daily builds, alphas, betas, or rc.
Least I can do is to use whichever version is released.

---

### Post by Mike_Walsh on 2014-10-25
> **not found said:**
> So I guess my forays into 4 different OS's before lunch some day's explains why I don't ever get anything (else) done :p

Hah! :D

No denigration implied here (and I hope no offence taken!). Seriously, it's taken me the last 6 months or so to get ALL my 'buntus set up JUST how I want them; they're working a treat. I just can't be bothered to update every single one of them again; I only get to play on here for a limited time each day, and I'd much rather just USE Trusty, now I've got all the tweaks installed, and all the work-arounds sorted out...

You NEVER know, though. I intend to stick with Trusty for at LEAST 2 years; and since this is the first LTS to receive 5-year support, I may switch at 16.04, I may leave it till 18.04; whatever I do, it will be carefully planned out and implemented properly..!

I'll see how I feel about it in 18 months time.

Regards,

Mike.

---

### Post by ian-weisser on 2014-10-25
> **Lester_Ingber said:**
> Most of the time upgrades have not at all been smooth.  I was trying to keep up with the latest upgrades, but the real issue for me now is to ensure the smoothest path for future upgrades.

The smoothest path for upgrades, just like the smoothest path to ride a bicycle, is often not about the path at all. It's often about basic maintenance.

If, before you upgrade, you avoid the most common mistakes:
- Uninstall non-Ubuntu software and autoremove non-Ubuntu-provided dependencies
- Reinstall any removed desktop metapackages
- Backup your data, customized settings, and custom scripts/applications

Then most of your upgrades to any future version of Ubuntu (semi-annual or LTS) will be quite dull - just the way you want an upgrade to be.

Basic maintenance does not take long. But it won't do itself.
All but two of my many upgrades (using many different methods) over nine years has been smooth and rock solid. Of the two hiccups, one was a real bug (fixed in about two weeks), and the other was my own fault - didn't prepare the system properly.

---

### Post by craig10x on 2014-10-25
Very good list there, ian-weisser...yeah, i think my "secret" is i just run a "stock ubuntu" (with a number of apps added of course) so there is nothing for me to prepare for a very successful upgrade...other then turning off my google chrome ppa...One time i forgot but the upgrader told me it turned it off for me ;)

I use to do it with the upgrade option on the live iso, but have found that it isn't as good as doing it from the software updater...not all the apps get transferred (though all the data always did and most of the settings)...
I think that is because you are not on your hard drive when doing it with the iso, but when doing it with the updater, you ARE....so, it doesn't have to transfer that stuff over, just add and remove packages...

---

### Post by mikodo on 2014-10-25
> **ian-weisser said:**
> The smoothest path for upgrades, just like the smoothest path to ride a bicycle, is often not about the path at all. It's often about basic maintenance.

If, before you upgrade, you avoid the most common mistakes:
- Uninstall non-Ubuntu software and autoremove non-Ubuntu-provided dependencies
- Reinstall any removed desktop metapackages
- [B]Backup your data, customized settings, and custom scripts/applications
[/B]
Then most of your upgrades to any future version of Ubuntu (semi-annual or LTS) will be quite dull - just the way you want an upgrade to be.

Basic maintenance does not take long. But it won't do itself.
All but two of my many upgrades (using many different methods) over nine years has been smooth and rock solid. Of the two hiccups, one was a real bug (fixed in about two weeks), and the other was my own fault - didn't prepare the system properly.

How does one backup customized settings (??? the desktop).

---

### Post by ian-weisser on 2014-10-25
> **mikodo said:**
> How does one backup customized settings (??? the desktop).

If it's a config file, back up the file.
If it's a Dconf/Gsetting or other database, make notes (text file) so you can recreate when you someday must reinstall. Backup your notes.

---

### Post by vasa1 on 2014-10-25
> **ian-weisser said:**
> ...
If, before you upgrade, you avoid the most common mistakes:
...
- Reinstall any removed desktop metapackages
...
...
I knew about that ^^^ but forgot to do it. Still things went fine. This was on Lubuntu.

---

### Post by mikodo on 2014-10-25
> **ian-weisser said:**
> If it's a config file, back up the file.
If it's a Dconf/Gsetting or other database, make notes (text file) so you can recreate when you someday must reinstall. Backup your notes.

Thank you.

---

### Post by /ADM on 2014-10-27
I also hardly touch anything and pretty much leave it stock.  I just add apps from the Software Center or apt-get them and that is about it.  Since Unity is not really able to be modified I just stick with what is given, don't know about flavours though.

Updates have always been hassle-free.  I am just thankful we are not in the update (wait 2 hours), restart, configure, update (wait another 2 hours), restart, configure, DESKTOP scenario.

---

### Post by SurfaceUnits on 2014-10-29
> **not found said:**
> So I guess my forays into 4 different OS's before lunch some day's explains why I don't ever get anything (else) done :p

I used to do that; test out every new release of every distro. I even have the Darwin iso somewhere. Then I got to where all I wanted was something stable. 
The only thing I'm looking forward to playing with now is LXQT.

---

### Post by sports fan Matt on 2014-10-30
Honestly, I have never had any problems after 5 years of upgrading.  Back in the Lucid days, I made a commitment to myself to only use LTS releases because I did not know when, but I knew at some point my life would get crazy busy and I would no longer have the time to beta test or upgrade every six months.

---

