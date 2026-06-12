---
title: "Random, or maybe not random, crashes"
date: 2011-04-03
forum: System76 Support
---

### Post by azion1995 on 2011-04-03
Every few days, my Ratel Ultra running 64 bit Ubuntu 10.10 will suffer what appears to be a video crash. At seemingly random times, both when I'm perhaps stressing the CPU by running multiple apps, and sometimes even when I walk away leaving nothing running, everything will suddenly stop running, and after a second, I'll find myself back at the login screen. I've checked by logging in using another account, and my personal account has been completely logged out in the crash.

This isn't entirely catastrophic, or at least hasn't been yet, but it is rather frustrating. It happens whether I use Compiz, Metacity, or Openbox as my window manager. Were this a Windows system, my first thought would be that it's a video driver issue, but System76 support maintains that the bundled drivers are the best available for the system.

Any thoughts?

-Z

---

### Post by Ranko Kohime on 2011-04-04
> **azion1995 said:**
> Every few days, my Ratel Ultra running 64 bit Ubuntu 10.10 will suffer what appears to be a video crash. At seemingly random times, both when I'm perhaps stressing the CPU by running multiple apps, and sometimes even when I walk away leaving nothing running, everything will suddenly stop running, and after a second, I'll find myself back at the login screen. I've checked by logging in using another account, and my personal account has been completely logged out in the crash.

This isn't entirely catastrophic, or at least hasn't been yet, but it is rather frustrating. It happens whether I use Compiz, Metacity, or Openbox as my window manager. Were this a Windows system, my first thought would be that it's a video driver issue, but System76 support maintains that the bundled drivers are the best available for the system.

Any thoughts?

-Z
I am experiencing the same issue, though it takes much longer to get back to the login prompt for me, probably due to my slower system, and I'm not using a Sytem 76 unit.  I've got an EeePC 701SD, and it has on a few occasions done the exact same thing, though only more recently, and on 10.04.  (Desktop, not Netbook edition).

I have not experienced it in Openbox, only Gnome, though I haven't used Openbox extensively yet.

---

### Post by isantop on 2011-04-04
If it happens regardless of your DE, try running MemTest86 for a few passes to see if it's returning any memory errors.

---

### Post by azion1995 on 2011-04-11
> **isantop said:**
> If it happens regardless of your DE, try running MemTest86 for a few passes to see if it's returning any memory errors.

Nope, no memory errors. 

-Z

---

### Post by isantop on 2011-04-12
Is it possible to try running the system from a Live Disk?

---

### Post by azion1995 on 2011-04-15
> **isantop said:**
> Is it possible to try running the system from a Live Disk?

I imagine so, but what would be the goal? To see whether a plain-vanilla version of Ubuntu has fewer problems? The problem w/this approach is that these crashes are intermittent; just because one doesn't happen doesn't mean that we've solved the problem, as it could simply be being intermittent again.

Yes, of course, if I ran it as a LiveCD for a week or so, that would help considerably to determine if the crashes are due to something odd in my config. But that would mean that my PC would be crippled for a week, more crippled than by the occasional kick-off error. Hence, I'd prefer to find another approach.

-Z

---

### Post by Ranko Kohime on 2011-04-17
I'm doing some more troubleshooting on my crashes, and I just had a thought: fonts.

I have/had about 150 fonts in ~/.fonts, do you have any yourself?  If so, would you provide a directory list?

I haven't confirmed anything yet, but my laptop did not have these problems prior to loading my ~/.fonts folder from my collection.

---

### Post by azion1995 on 2011-04-23
> **Ranko Kohime said:**
> I'm doing some more troubleshooting on my crashes, and I just had a thought: fonts.

I have/had about 150 fonts in ~/.fonts, do you have any yourself?  If so, would you provide a directory list?

I haven't confirmed anything yet, but my laptop did not have these problems prior to loading my ~/.fonts folder from my collection.

Not many fonts at all- 

[FONT=Courier New]adam@calvin:~$ ls .fonts
andalemo.ttf                   comic.ttf               tahomabd.ttf
AppleGaramond-BoldItalic.ttf   courbd.ttf              tahoma.ttf
AppleGaramond-Bold.ttf         courbi.ttf              timesbd.ttf
AppleGaramond-Italic.ttf       couri.ttf               timesbi.ttf
AppleGaramond-LightItalic.ttf  cour.ttf                timesi.ttf
AppleGaramond-Light.ttf        georgiab.ttf            times.ttf
AppleGaramond.ttf              georgiai.ttf            trebucbd.ttf
Aquabase-spanish-support.ttf   georgia.ttf             trebucbi.ttf
Aquabase.ttf                   georgiaz.ttf            trebucit.ttf
arialbd.ttf                    HardGothicNormal.ttf    trebuc.ttf
arialbi.ttf                    impact.ttf              verdanab.ttf
ariali.ttf                     LITHOGRL.TTF            verdanai.ttf
arial.ttf                      Lucida Grande Bold.ttf  verdana.ttf
ariblk.ttf                     Lucida Grande.ttf       verdanaz.ttf
comicbd.ttf                    lucon.ttf
[/FONT]
Doesn't look all that horrid.

-Z

---

### Post by Ranko Kohime on 2011-04-27
You don't have any of the same fonts that I do, so that rules that out a particular font.

During all this I switched to using Openbox on my desktop, and it only crashed when I did one particular thing: Hit save in the menu config program.

Still haven't figured it out, although my laptop has been rock solid for over 3 weeks (not moving around right now, so it has been a temporary 2nd desktop)

---

### Post by cespinal on 2011-05-02
Bump because this is appearing all over the place. 

Any suggestions yet? I experiencing my crashes when I start using the system heavily... Screen crashes but I keep to move the mouse....

---

### Post by isantop on 2011-05-02
This sounds like it could be a problem with the hard disk drive, but there really is no way to tell for sure without running it from a LiveCD. Does the disk come back healthy in disk utility?

---

### Post by cespinal on 2011-05-03
Disk is ok and recognised as healthy.... 
It dual boot with Windows 7 and havent had any problems so far...

---

### Post by isantop on 2011-05-05
Do these issues happen on all of a system's user accounts, or just one?

---

### Post by azion1995 on 2011-05-06
Oddly, I don't recall having any similar crashes since upgrading to Natty.

-Z

---

### Post by isantop on 2011-05-06
I'd keep an eye on it, but for now, I think we can call this fixed in natty.

---

