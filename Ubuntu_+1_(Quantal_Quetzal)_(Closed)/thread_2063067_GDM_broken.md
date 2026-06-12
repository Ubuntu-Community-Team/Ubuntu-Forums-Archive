---
title: "GDM broken?"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sgage on 2012-09-26
I rebooted after this morning's updates, and after the Ubuntu logo, the screen turns black, and I get the little "wait for it" orb... and it doesn't proceed past that point. The orb just sits there forever.

---

### Post by Bucky Ball on 2012-09-26
Try choosing the Recovery Kernel (second on the list) at boot. When you get to the options 'Fix broken packages' then 'Resume normal boot'. If it takes you to a cursor, try typing in:

```
startx
```Failing all that, boot to Recovery again, options, 'Drop to root shell with networking' then these two commands:

```
apt-get install update
apt-get install upgrade
```

* Just noted Ubuntu +1 forum. None of this may work. Keep updating regularly. ;)

---

### Post by arpanaut on 2012-09-26
Same symptoms here, no cure yet.
Past 24 hrs. though, thank goodness for multi-boot system.

edit:
@ BB tried all that no go

---

### Post by Harry33 on 2012-09-26
Please let us all know the version of the Gdm you are experiencing issues with.

You see I use only Gnome-shell and its fallback Gnome Classic in my QQ.
There the Gdm version 3.5.92.1 works just fine.
However, the latest version 3.6.0 is really broken and it hangs.
Downgrading to 3.5.92.1. solves the issue.

---

### Post by arpanaut on 2012-09-26
gdm:i386 (3.5.92.1-0ubuntu1, 3.6.0-0ubuntu1) Is what I have here, 
Pure Gnome-remix install. was working fine until updates yesterday AM.  
dist-upgraded through recovery just now, still hangs at logo/blinking dots
with spinner cursor. Resume booting from recovery mode just goes to black screen with 
cursor, keyboard dysfunctional, hard power shutdown only way out.
Ain't this fun!

---

### Post by sgage on 2012-09-26
> **Harry33 said:**
> Please let us all know the version of the Gdm you are experiencing issues with.

You see I use only Gnome-shell and its fallback Gnome Classic in my QQ.
There the Gdm version 3.5.92.1 works just fine.
However, the latest version 3.6.0 is really broken and it hangs.
Downgrading to 3.5.92.1. solves the issue.

I just updated a few hours ago, and it brought in 3.6.0

I'm heading out for a couple of days, and will be away from station, so I can't really work this problem now (in fact, I gotta hit the road in 15 minutes).

I'm sure it will be fixed by the time I get back :KS

---

### Post by funicorn on 2012-09-26
same here. New version of gnome display manager is released as purely crap. what a joke.

---

### Post by mpmistr on 2012-09-26
> **sgage said:**
> I rebooted after this morning's updates, and after the Ubuntu logo, the screen turns black, and I get the little "wait for it" orb... and it doesn't proceed past that point. The orb just sits there forever.

I am in the same boat. In fact running sudo apt-get update & upgrade broke my system (it REMOVED Gnome Shell and when I tried to reinstall it stated broken dependencies with libmutter0). I had to reinstall again from USB.. GDM 3.6 now produces a black screen and busy cursor.

Googling around in the past it's been an issue with pam.d but I tried those fixes and no such luck. I'm just going to wait for a fix I guess.. dropping to a terminal with CTRL+ALT+F2 while GDM is 'stuck' and doing startx will get you into your desktop as a work around for now..

For the record I was am also using the Gnome 3 PPA, not sure if that matters though.

---

### Post by zika on 2012-09-26
Revert back to LightDM?
```
sudo dpkg-reconfigure gdm
```...

---

### Post by jbicha on 2012-09-26
Hi, all.

I apologize for not having tested gdm thoroughly enough yesterday. It's been a bit crazy with trying to finish up the documentation, which has really reduced my time available for the GNOME Remix the past few days.

I opened a [bug]("http://pad.lv/1056936") and I identified that we need gnome-session 3.6 (which we didn't have already since we're in hard freeze). Fixing this is a high priority for me and is being worked on today. Meanwhile, you could use the previous gdm release:

32 bit version:
[https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796976/+files/gdm_3.5.92.1-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796976/+files/gdm_3.5.92.1-0ubuntu1_i386.deb)

Or 64-bit version:
[https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796973/+files/gdm_3.5.92.1-0ubuntu1_amd64.deb](https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796973/+files/gdm_3.5.92.1-0ubuntu1_amd64.deb)

---

### Post by bmbaker on 2012-09-26
what i did was stopped gdm strg+alt+F1
```
sudo service gdm stop
sudo service lightdm start
```

then
```
cd /var/cache/apt/archives
sudo dpkg -i gdm_3.5.92.1-0ubuntu1_amd64.deb -f
sudo reboot
```
everything now wks again :-)

until the next breakage of course :-) :-)

---

### Post by Harry33 on 2012-09-26
> **jbicha said:**
> Hi, all.

I apologize for not having tested gdm thoroughly enough yesterday. It's been a bit crazy with trying to finish up the documentation, which has really reduced my time available for the GNOME Remix the past few days.

I opened a [bug]("http://pad.lv/1056936") and I identified that we need gnome-session 3.6 (which we didn't have already since we're in hard freeze). Fixing this is a high priority for me and is being worked on today. Meanwhile, you could use the previous gdm release:

32 bit version:
[https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796976/+files/gdm_3.5.92.1-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796976/+files/gdm_3.5.92.1-0ubuntu1_i386.deb)

Or 64-bit version:
[https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796973/+files/gdm_3.5.92.1-0ubuntu1_amd64.deb](https://launchpad.net/ubuntu/+source/gdm/3.5.92.1-0ubuntu1/+build/3796973/+files/gdm_3.5.92.1-0ubuntu1_amd64.deb)

You could upload the gnome-session_3.6.0 to Gnome3 PPA perhaps?

---

### Post by ricotz on 2012-09-26
> **Harry33 said:**
> You could upload the gnome-session_3.6.0 to Gnome3 PPA perhaps?

The gnome-session 3.6.0 package will be there shortly.

---

### Post by Stinger on 2012-09-26
@ricotz
Thank you very much, appreciated. :D
I have just re-installed Gnome Remix alpha2 and held back gdm.
Have added Gnome3 PPA again and will do another update as soon as gnome-session 3.6.0 arrives, thanks again.

I have added myself to [bug#1056936]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1056936") and would recommend anyone else affected to do so too.

---

### Post by jbicha on 2012-09-26
The new gnome-session (3.6.0-0ubuntu1) has been accepted into quantal.

---

### Post by Wise Ferret on 2012-09-26
Can you please make the new ibus packages go into quantal as well? The keyboard layout indicator used in gnome-shell is broken without them, and this can be very problematic on multi-lingual systems (especially with passwords, where you cannot see what you type).
See this bug for reference:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914)

---

### Post by jbicha on 2012-09-26
I already commented on that bug. ibus 1.6 is a major upgrade with a whole lot of changes since 1.4. The Ubuntu developers are very unlikely to switch a critical component like that out at this point.

GNOME did a risky overhaul of their input method handling and it wasn't clear at the beginning of the cycle whether the work would be complete and not cause regressions for input method users. Ubuntu will follow for 13.04 but with more time to assess and fix any issues.

---

### Post by mpmistr on 2012-09-26
> **Wise Ferret said:**
> Can you please make the new ibus packages go into quantal as well? The keyboard layout indicator used in gnome-shell is broken without them, and this can be very problematic on multi-lingual systems (especially with passwords, where you cannot see what you type).
See this bug for reference:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914)

Is this why GDM will not accept my password now but tty will?

---

### Post by jbicha on 2012-09-26
It's probably using en_US as the keyboard layout. Have you taken steps to change your system keyboard layout?

Unfortunately, without the newer ibus, there isn't a keyboard layout or switcher on the login screen which is pretty bad. I'd like to at least backport the newer ibus to the GNOME3 PPA but once again, I don't have an estimate on when that will be.

---

### Post by arpanaut on 2012-09-27
> **jbicha said:**
> The new gnome-session (3.6.0-0ubuntu1) has been accepted into quantal.

Got that w/ today's updates but still having same issue with hang and spinning cursor when gdm should take me to login screen. ctrl+alt+F2 then login > startx take me to a fallback session, logout takes me back to virt. terminal.

So something is still not right with the gnome-remix install?

p.s. gnome-shell-extentions is a broken package... conflicting dependencies.

---

### Post by Stinger on 2012-09-27
Borked my install twice trying to fix the gdm issue :rolleyes:
Have done a full update just now, everything is working again :D
I just have the [ppa:gnome3-team/gnome3]("https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal") enabled, no other Gnome3 ppa is needed to make gnome 3.6 complete.

@jbicha
Thanks for solving this quickly, "errare humanum est" ;)

---

### Post by arpanaut on 2012-09-27
I am testing the Gnome Remix "as is"... i.e.  jbicha's release.
I'm not interested in work arounds or adding PPA's.
I'm concerned with what is provided by the normal release cycle.

No offence intended, just stating my perspective.

---

### Post by mpmistr on 2012-09-27
My GDM not accept password issue was my own fault from trying to tinker a work around from when I was getting a black screen / cursor.. restoring old file located in my pam.d directory fixed it.

Working now..

---

### Post by Stinger on 2012-09-27
> **arpanaut said:**
> I am testing the Gnome Remix "as is"... i.e.  jbicha's release.
I'm not interested in work arounds or adding PPA's.
I'm concerned with what is provided by the normal release cycle.

No offence intended, just stating my perspective.
None taken.
I want to have my Gnome3.6 as complete as possible, that means I have to use the Gnome3 ppa (else I'll miss out on Nautilus, Totem and others).
BTW there is no workarounds included.

---

### Post by funicorn on 2012-09-27
It's working now, but very slow. I say lightdm is light.

---

### Post by celluloid on 2012-09-28
> **funicorn said:**
> It's working now, but very slow. I say lightdm is light.

Yeah, working here too, but is noticeably slower than lightdm. :(

---

