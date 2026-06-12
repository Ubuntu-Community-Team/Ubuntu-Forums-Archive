---
title: "Assuming it is Safe to Upgrade"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teejay17 on 2012-04-25
I'm assuming it's pretty safe to run the update (Alt+F2 and type in **update-manager -d) **at this point without too much to worry about[B]...
[/B]

---

### Post by MARP1961 on 2012-04-25
I would have thought so. I did it a couple of days ago and it's running fine. If you want a fresh install just grab the latest daily build:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
By applying regular updates you will have the same version as everyone else after release day. Beat the rush and download now!

---

### Post by TBABill on 2012-04-25
If you are itching to upgrade, now is better than later. The servers will be slammed for a while when the official release hits.

---

### Post by teejay17 on 2012-04-25
> **TBABill said:**
> If you are itching to upgrade, now is better than later. The servers will be slammed for a while when the official release hits.
Yes, that is a great point. I was thinking along those lines.

---

### Post by grahammechanical on 2012-04-25
I have been testing the upgrade path and I have been following this test case:

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade")

Notice that the suggested command is

```
update-manager -d -c
```

-d = Check if upgrading to the latest development release is possible.

-c = if a new distribution release is available.

Using that command I had no problems upgrading a default 11.10 or a default 10.04 to 12.04

It loads Update Manager with a button advising you that a new distribution release is available.

Regards.

---

### Post by Splashmania on 2012-04-25
Yes is safe to upgrade, but you probably need reconfigurate your grub2.
have any live-cd near and you'll be safe.

that guide is in spanish but just works
[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by jackson21 on 2012-04-25
why do you not a fresh install of
Ubuntu 12.04,
you can download the  latest   Ubuntu  Beta2 already.
I know that we always love the current Ubuntu editions 11.10 with all our  beloved downloads and files.
But you can easily transfer  anything  from the previous Ubuntu 
to the new 12.04 LTS  provided you have enough harddisk space available.You can do it in  20 minutes and you have a brand new  12.04 Ubuntu.

So take the jump !!!!

jackson from Austria

---

### Post by dFlyer on 2012-04-25
It's been safe for some time now. Go ahead and upgrade or wait for the rush to hit tomorrow. If you want to do a fresh install just download the daily build, I believe the current is 4/23/2012.

---

### Post by sgage on 2012-04-25
> **dFlyer said:**
> It's been safe for some time now. Go ahead and upgrade or wait for the rush to hit tomorrow. If you want to do a fresh install just download the daily build, I believe the current is 4/23/2012.

Actually, the current is today:

[http://cdimage.ubuntu.com/daily-live/20120425/](http://cdimage.ubuntu.com/daily-live/20120425/)

:KS

---

### Post by soro2005 on 2012-04-25
Be warned that the proprietary nvidia driver is making problems for many in Precise.

---

### Post by teejay17 on 2012-04-25
> **soro2005 said:**
> Be warned that the proprietary nvidia driver is making problems for many in Precise.
Thanks. I have have generic Intel, so it should be okay.

---

### Post by arpanaut on 2012-04-25
> **soro2005 said:**
> Be warned that the proprietary nvidia driver is making problems for many in Precise.
Precisely, I do hope this is emphasized in the release notes.
As it appears that this is not going to be corrected until after release.
I could be wrong, but I am not seeing anything in proposed updates that addresses this issue.

---

### Post by VinDSL on 2012-04-25
> **soro2005 said:**
> Be warned that the proprietary nvidia driver is making problems for many in Precise.

> **arpanaut said:**
> Precisely, I do hope this is emphasized in the release notes.
As it appears that this is not going to be corrected until after release.
I have a *feeling* that a lot of ppl, on vintage hardware (like myself), are going to lose their web connection too, after upgrading.

network-manager refused to connect to the web, on this machine, for a couple of months.  I had to switch to Wicd to get any connection at all.

BTW, earlier releases and older kernels had no problem recognizing my onboard LAN device -- only Ubu 12.04 with >= Linux 3.2 kernel.

The fix, ultimately, was to ditch my pseudo, onboard, southbridge-driven LAN device, and install a real (supported) network card.  After doing this, network-manager started working fine.  However...

I'm NOT convinced that they ever fixed this problem, at a software level.

I *fear* that many ppl will be left in the lurch, once they upgrade, e.g. no video and/or no web connection.

Heh!  Only time will tell...

---

### Post by pqwoerituytrueiwoq on 2012-04-25
> **VinDSL said:**
> I have a *feeling* that a lot of ppl, on vintage hardware (like myself), are going to lose their web connection too, after upgrading.

network-manager refused to connect to the web, on this machine, for a couple of months.  I had to switch to Wicd to get any connection at all.

BTW, earlier releases and older kernels had no problem recognizing my onboard LAN device -- only Ubu 12.04 with >= Linux 3.2 kernel.

The fix, ultimately, was to ditch my pseudo, onboard, southbridge-driven LAN device, and install a real (supported) network card.  After doing this, network-manager started working fine.  However...

I'm NOT convinced that they ever fixed this problem, at a software level.

I *fear* that many ppl will be left in the lurch, once they upgrade, e.g. no video and/or no web connection.

Heh!  Only time will tell...
glad we can use a live cd :)

it is just the beta nvidia driver or is the stable release bugged?
*has not tested on my nvidia chip since the bug appeared*
Would my GTX550 TI or my mom's GT 430 (became hers when i upgraded) be affected?

---

### Post by dFlyer on 2012-04-25
> **sgage said:**
> Actually, the current is today:

[http://cdimage.ubuntu.com/daily-live/20120425/](http://cdimage.ubuntu.com/daily-live/20120425/)

:KS

I stand corrected.

---

### Post by xebian on 2012-04-25
> **dFlyer said:**
> I stand corrected.

Actually you should always use 

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)[COLOR="Red"]current[/COLOR]

instead of [http://cdimage.ubuntu.com/daily-live/20120425/](http://cdimage.ubuntu.com/daily-live/20120425/) because there is a chance of multiple builds for that day (20120425.1 as an example).

current will always point to the most current build for that day.

---

### Post by teejay17 on 2012-04-25
> **VinDSL said:**
> I have a *feeling* that a lot of ppl, on vintage hardware (like myself), are going to lose their web connection too, after upgrading.

network-manager refused to connect to the web, on this machine, for a couple of months.  I had to switch to Wicd to get any connection at all.

BTW, earlier releases and older kernels had no problem recognizing my onboard LAN device -- only Ubu 12.04 with >= Linux 3.2 kernel.

The fix, ultimately, was to ditch my pseudo, onboard, southbridge-driven LAN device, and install a real (supported) network card.  After doing this, network-manager started working fine.  However...

I'm NOT convinced that they ever fixed this problem, at a software level.

I *fear* that many ppl will be left in the lurch, once they upgrade, e.g. no video and/or no web connection.

Heh!  Only time will tell...
Wicd is well, wicked. I can always depend on it when network-manager fails on certain hardware. It will just work.

---

### Post by VinDSL on 2012-04-25
> **teejay17 said:**
> Wicd is well, wicked. I can always depend on it when network-manager fails on certain hardware. It will just work.
I liked "wicked" just fine!  Worked better than NM, IMO.

I would have kept using it, but since network-manager is such an integral part of Ubuntu, I thought I should keep pounding away, until it got sorted.  ;)

---

### Post by VinDSL on 2012-04-25
> **pqwoerituytrueiwoq said:**
> it is just the beta nvidia driver or is the stable release bugged?
*has not tested on my nvidia chip since the bug appeared*
Would my GTX550 TI or my mom's GT 430 (became hers when i upgraded) be affected?
The only problems I was having was with the "stable release(s)"... module not compiling without a bunch of monkeying around, and so forth.

I'm living on the razor's edge right now -- xorg-edgers fresh X crack releases, fresh from git -- Linux 3.4rc4 mainline kernel -- and they all work fine.  

Go figure!  LoL!  :D

---

### Post by sammiev on 2012-04-25
> **VinDSL said:**
> The only problems I was having was with the "stable release(s)"... module not compiling without a bunch of monkeying around, and so forth.

I'm living on the razor's edge right now -- xorg-edgers fresh X crack releases, fresh from git -- Linux 3.4rc4 mainline kernel -- and they all work fine.  

Go figure!  LoL!  :D

When does the fun start then? Maybe 12.10! LOL

---

### Post by teejay17 on 2012-04-26
I upgraded last night, before the official release. Everything went super-awesome. For example, I could actually update Virtualbox without a hitch, unlike the problems I encountered while trying to upgrade it in 11.10 and 11.04.

---

