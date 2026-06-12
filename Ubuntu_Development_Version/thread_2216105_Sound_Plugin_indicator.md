---
title: "Sound Plugin indicator?"
date: 2014-04-10
forum: Ubuntu Development Version
---

### Post by frank18 on 2014-04-10
Hi guys ? this is frustating after i reinstall Xubuntu 14.04 i got sound plugin volume indicator now when i Updated i lost iy again.
please someone tell me what's going on.

---

### Post by Elfy on 2014-04-10
at a guess it's not set in settings manager properly 

settings - session - autostart - make sure that sound indicator is enabled in there

---

### Post by frank18 on 2014-04-10
> **Elfy said:**
> at a guess it's not set in settings manager properly 

settings - session - autostart - make sure that sound indicator is enabled in there

Thanks Elfy: i went to autostart and the sound indicator is activated all the time,ive never untick it,this must be a big bug that seems nobody can fix,i'll not update no more till it's fixed if not i have to go with other desktop or distro,wish my oll Dell P4 with only 1G ran would take Ubuntu but it doesn't.

---

### Post by Elfy on 2014-04-10
Do you happen to have the the old gtk2 one installed as well? 

```
dpkg -l indicator-*
```

Also it's possible that you still need the enviroment workaround, edit /etc/environment

```
sudo nano /etc/environment
```

Add 

INDICATOR_ALLOW_NO_WATCHERS=yes

save and reboot

[https://bugs.launchpad.net/indicator-network/+bug/1185565](https://bugs.launchpad.net/indicator-network/+bug/1185565)
[https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators)

---

### Post by frank18 on 2014-04-10
> **Elfy said:**
> Do you happen to have the the old gtk2 one installed as well? 

```
dpkg -l indicator-*
```

Also it's possible that you still need the enviroment workaround, edit /etc/environment

```
sudo nano /etc/environment
```

Add 

INDICATOR_ALLOW_NO_WATCHERS=yes

save and reboot

[https://bugs.launchpad.net/indicator-network/+bug/1185565](https://bugs.launchpad.net/indicator-network/+bug/1185565)
[https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators)

Thanks again this is what shows
dpkg -l indicator-*

---

### Post by anaconda on 2014-04-10
I use a program called volti
Volti is iin the repos.

Works very well. (I am using alsa sounds.)

---

### Post by pqwoerituytrueiwoq on 2014-04-10
sound indicator is working as of today, at least on the 64bit version

---

### Post by spsf2 on 2014-04-10
> **pqwoerituytrueiwoq said:**
> sound indicator is working as of today, at least on the 64bit version
As of today (apr/10) live USB 64 Bit sound indicator does NOT show up on initial boot

---

### Post by mc4man on 2014-04-10
> **frank18 said:**
> Thanks again this is what shows
dpkg -l indicator-*
Well it's showing in your screenshot, does it not open when clicked on?

A fresh xubuntu beta 2 install here has a working sound indicator. After updating (333 updates, some new), it's still working.

That's not to say the indicators in the default xubuntu session aren't without issue, just not the sound one.
(- xubuntu ships with unity-settings-daemon/unity-control-center which now dep on several indicators & seem to cause some exta indicators, -  
indicator-bluetooth, indicator-keyboard, & the shown  power  indicator (indicator-power),  is only semi-functional.

Edit: also indicator-date-time is pulled in from unity-control-center.

---

### Post by pqwoerituytrueiwoq on 2014-04-10
> **spsf2 said:**
> As of today (apr/10) live USB 64 Bit sound indicator does NOT show up on initial boot
i installed todays live disk and gave it updates and upon logout/login i had a sound indicator
also installed updates on another system and it got the sound indicator and a second clock

---

### Post by evan8 on 2014-04-10
you sure it's not marked as hidden on the indicator preference?

---

### Post by spsf2 on 2014-04-11
> **pqwoerituytrueiwoq said:**
> i installed todays live disk and gave it updates and upon logout/login i had a sound indicator
also installed updates on another system and it got the sound indicator and a second clock
Just to be clear, I am reporting the LIVE boot, no updates, no installation.
IMHO I believe the live boot must be fully operational, you cant expect someone to like this distro if it happens to be released (again) with a sound/vol indicator defective as it happened to 13.10.

---

### Post by pqwoerituytrueiwoq on 2014-04-11
> **spsf2 said:**
> Just to be clear, I am reporting the LIVE boot, no updates, no installation.
IMHO I believe the live boot must be fully operational, you cant expect someone to like this distro if it happens to be released (again) with a sound/vol indicator defective as it happened to 13.10.
it probably made it into the release candidate

---

### Post by spsf2 on 2014-04-11
> **pqwoerituytrueiwoq said:**
> it probably made it into the release candidate
RC date was supposed to be yesterday (april 10) the same iso I reported the problem, I'll download the latest daily-live and report later.
Let's hope it get fixed

---

### Post by pqwoerituytrueiwoq on 2014-04-11
i don't think the offical rc is that day's daily
i could not find the rc when i needed to do a install s i used the daily iso did updates and there it was, yay fixed

---

### Post by spsf2 on 2014-04-11
Just checked today live iso, working fine! 
I have a new issue with dual bluetooth indicator, just started a new thread:

[http://ubuntuforums.org/showthread.php?t=2216323](http://ubuntuforums.org/showthread.php?t=2216323)

---

### Post by frank18 on 2014-04-11
> **mc4man said:**
> Well it's showing in your screenshot, does it not open when clicked on?

A fresh xubuntu beta 2 install here has a working sound indicator. After updating (333 updates, some new), it's still working.

That's not to say the indicators in the default xubuntu session aren't without issue, just not the sound one.
(- xubuntu ships with unity-settings-daemon/unity-control-center which now dep on several indicators & seem to cause some exta indicators, -  
indicator-bluetooth, indicator-keyboard, & the shown  power  indicator (indicator-power),  is only semi-functional.

Edit: also indicator-date-time is pulled in from unity-control-center.

Thanks mc4man; Yes it shows on the Screen shot cause i took it after i did the fresh Install of Xubuntu 14.04 beta 32bit  and only ticked the 2 boxes upon install with updates,but i did not do any updates ever since, cause the other times once i did more updates after i had the system running then that's  when i lost the sound indicator,i will not do any updates till i'm sure that i will not loose the sound indicator or at least will be a good code to bring it back.

---

### Post by frank18 on 2014-04-12
[QUOTE=Elfy;12983657]Do you happen to have the the old gtk2 one installed as well? 

```
dpkg -l indicator-*
```

Also it's possible that you still need the enviroment workaround, edit /etc/environment

```
sudo nano /etc/environment
```

Add 

INDICATOR_ALLOW_NO_WATCHERS=yes

save and reboot



 Hi Elfy; today i pulled the update manager and installed all available updates for Xubuntu 14.04  and guess what, i did not loose the sound indicator, i had done prior the bellow codes so that probably was the solution! so far so good,before i did the updates i already had done an Iso Image of Ubuntu 13.10 beta2 gnome desktop in case i would loose the sound indicator,but i guess it will be in the back burner for now,hope i don't have to use it cause i realy like Xubuntu. 

sudo nano /etc/environment


INDICATOR_ALLOW_NO_WATCHERS=yes

---

