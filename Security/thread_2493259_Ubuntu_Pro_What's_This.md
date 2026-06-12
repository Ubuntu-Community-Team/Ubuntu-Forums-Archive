---
title: "Ubuntu Pro? What's This?"
date: 2023-12-08
forum: Security
---

### Post by Daveski17 on 2023-12-08
[IMG]https://i.imgur.com/yc6R9AU.jpg[/IMG]

Do I need this, or is it unnecessary?

[IMG]https://i.imgur.com/wpiqz8d.jpg[/IMG]

I'm just a bloke with a laptop running Ubuntu. I'm not Mark Shuttleworth or any sort of computing boffin. So, do I need this level of protection?

<snip>

---

### Post by Dennis N on 2023-12-08
If you would like to run the same version of Ubuntu LTS for 10 years total (5 years regular support + 5 years extended security support), this is for you. I use the service. No charge for up to 5 active machines. 

This is where you subscribe.
[https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe)

---

### Post by Daveski17 on 2023-12-08
> **Dennis N said:**
> If you would like to run the same version of Ubuntu LTS for 10 years total (5 years regular support + 5 years extended security support), this is for you. I use the service. No charge for up to 5 active machines. 

This is where you subscribe.
[https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe)

OK, thanks. So it's just an option then?

---

### Post by TheFu on 2023-12-08
> **Daveski17 said:**
> OK, thanks. So it's just an option then?

Yep.  They use a bit of fear trying to get you into their tracking system.  No need, provided you migrate to supported releases after the next LTS release happens (every 2 yrs, in April).  Just plan to move to a new LTS every June (give the release a few months for early issues to be resolved) of even number years  2022, 2024, 2026 ... those are LTS releases.  Odd years and all October releases are NOT LTS.

And plan to wipe the system and start over every other upgrade (4 yrs).  Basically, do 1 upgrade, no more, to avoid cruft in the system.

---

### Post by Daveski17 on 2023-12-08
> **TheFu said:**
> Yep.  They use a bit of fear trying to get you into their tracking system.  No need, provided you migrate to supported releases after the next LTS release happens (every 2 yrs, in April).  Just plan to move to a new LTS every June (give the release a few months for early issues to be resolved) of even number years  2022, 2024, 2026 ... those are LTS releases.  Odd years and all October releases are NOT LTS.

And plan to wipe the system and start over every other upgrade (4 yrs).  Basically, do 1 upgrade, no more, to avoid cruft in the system.

OK thanks Fu. I normally upgrade to LTS releases a short while after they're released anyway.

---

### Post by guiverc on 2023-12-09
As already covered, Ubuntu Pro ***primarily  ***extends *standard support*.

Ubuntu's default security applies only to packages in the 'main' or 'multiverse' repository; this has not changed; with those packages still maintained for 5 years (*extended with Ubuntu Pro* *to 10 years*).

Ubuntu has **never** provided security for packages from 'universe'; ie. community supported packages; and those have never had any guarantee of support beyond the 9 months for all, or 3 years for those provided supported by Ubuntu flavor teams (*included on their installation media*). Despite this *limit* or guarantee of support; the 'universe' repository is still open for any community member to backport or make security patches anytime during the initial five years; so technically 5 years applies here too (*thus my mention of guarantee*).

[B]Ubuntu Pro includes security for packages from 'universe'

[/B]This is a new service which is only available with PRO *enabled*. These are security fixes from the [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Official%20Support") that go beyond anything provided in 'universe' by the Ubuntu community. You'll note these packages appearing in your update messages as having (*optionally** available*) security fixes only if Ubuntu Pro is enabled. Not enabling it will keep you at the same *security level* you were before Ubuntu Pro existed.

---

### Post by Daveski17 on 2023-12-09
> **guiverc said:**
> As already covered, Ubuntu Pro ***primarily  ***extends *standard support*.

Ubuntu's default security applies only to packages in the 'main' or 'multiverse' repository; this has not changed; with those packages still maintained for 5 years (*extended with Ubuntu Pro* *to 10 years*).

Ubuntu has **never** provided security for packages from 'universe'; ie. community supported packages; and those have never had any guarantee of support beyond the 9 months for all, or 3 years for those provided supported by Ubuntu flavor teams (*included on their installation media*). Despite this *limit* or guarantee of support; the 'universe' repository is still open for any community member to backport or make security patches anytime during the initial five years; so technically 5 years applies here too (*thus my mention of guarantee*).

[B]Ubuntu Pro includes security for packages from 'universe'

[/B]This is a new service which is only available with PRO *enabled*. These are security fixes from the [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Official%20Support") that go beyond anything provided in 'universe' by the Ubuntu community. You'll note these packages appearing in your update messages as having (*optionally** available*) security fixes only if Ubuntu Pro is enabled. Not enabling it will keep you at the same *security level* you were before Ubuntu Pro existed.

Thanks for the info. I appreciate the options, but as I am careful where I surf (no social media), I reckon bog-standard security should be fine.  As I am not employed by MI6 or GCHQ (or am I? lol) I doubt I need Q-Department levels of security. Well, not in my universe anyway.

---

### Post by TheFu on 2023-12-09
> **Daveski17 said:**
> Thanks for the info. I appreciate the options, but as I am careful where I surf (no social media), I reckon bog-standard security should be fine.  As I am not employed by MI6 or GCHQ (or am I? lol) I doubt I need Q-Department levels of security. Well, not in my universe anyway.

Being patched is important.  

Just a few days ago, a state actor was discovered, hacking Linux systems the last 2 yrs, in mostly 1 country, but all countries had instances of the multiple rootkits installed.
[https://arstechnica.com/security/2023/12/stealthy-linux-rootkit-found-in-the-wild-after-going-undetected-for-2-years/](https://arstechnica.com/security/2023/12/stealthy-linux-rootkit-found-in-the-wild-after-going-undetected-for-2-years/)

Plus, if you have enabled Bluetooth in your BIOS, assume you can be hacked. Earlier this week, yet another BT bug was found that had been there for a very long time.  Sadly, most vendors have the fix, but choose NOT to enable it. Only ChromeOS has the fix enabled.  [https://www.theregister.com/2023/12/06/bluetooth_bug_apple_linux/](https://www.theregister.com/2023/12/06/bluetooth_bug_apple_linux/)

You may not think you are a target, but your computers ARE.  Linux systems make excellent command and control nodes, even if your family video and photo collection isn't sensitive.
[https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/)  They want the computing power, a little storage and your network connection.  Anything beyond that is gravy.

The idea that your computer isn't important enough to be used by someone else is like the "nothing to hide" argument. [https://en.wikipedia.org/wiki/Nothing_to_hide_argument](https://en.wikipedia.org/wiki/Nothing_to_hide_argument)

We all are in this together.  Staying patched isn't hard. Mitigation of these things can be easy or impossible. Thankfully, most of the time, once they are know, a fix is created and silently pushed to all of us, though normal updates.

I know you probably do stay patched based on the question. Don't downplay the good that does, not just for you, but for the rest of the connected world. We all need to stay patched if our computers are on a network.

---

### Post by Daveski17 on 2023-12-09
> **TheFu said:**
> Being patched is important.  

Just a few days ago, a state actor was discovered, hacking Linux systems the last 2 yrs, in mostly 1 country, but all countries had instances of the multiple rootkits installed.
[https://arstechnica.com/security/2023/12/stealthy-linux-rootkit-found-in-the-wild-after-going-undetected-for-2-years/](https://arstechnica.com/security/2023/12/stealthy-linux-rootkit-found-in-the-wild-after-going-undetected-for-2-years/)

Plus, if you have enabled Bluetooth in your BIOS, assume you can be hacked. Earlier this week, yet another BT bug was found that had been there for a very long time.  Sadly, most vendors have the fix, but choose NOT to enable it. Only ChromeOS has the fix enabled.  [https://www.theregister.com/2023/12/06/bluetooth_bug_apple_linux/](https://www.theregister.com/2023/12/06/bluetooth_bug_apple_linux/)

You may not think you are a target, but your computers ARE.  Linux systems make excellent command and control nodes, even if your family video and photo collection isn't sensitive.
[https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/)  They want the computing power, a little storage and your network connection.  Anything beyond that is gravy.

The idea that your computer isn't important enough to be used by someone else is like the "nothing to hide" argument. [https://en.wikipedia.org/wiki/Nothing_to_hide_argument](https://en.wikipedia.org/wiki/Nothing_to_hide_argument)

We all are in this together.  Staying patched isn't hard. Mitigation of these things can be easy or impossible. Thankfully, most of the time, once they are know, a fix is created and silently pushed to all of us, though normal updates.

I know you probably do stay patched based on the question. Don't downplay the good that does, not just for you, but for the rest of the connected world. We all need to stay patched if our computers are on a network.

I don't disagree Fu, and I take as many precautions as I can (within reason). I'm usually patched and up to date (on Mac as well). I originally switched to Linux to avoid Windows and its dodgy security issues. I know Ubuntu isn't bulletproof, but I'm pretty sure I'm not compromised. I will probably never know for sure of course, unless I go off-grid and move into Faraday Cage. I am tempted sometimes ... lol.

---

### Post by ian-weisser on 2023-12-09
> **Daveski17 said:**
> I'm just a bloke with a laptop running Ubuntu. I'm not Mark Shuttleworth or any sort of computing boffin. So, do I need this level of protection?

If you use LTS releases AND lots of Universe software, then you might indeed have lots of attack surface for a long period of time. Those are the potential consequences for the choices you have made. You just didn't know about those vulnerabilities before.

Canonical has never promised to provide security patches for Universe packages. That is a community responsibility, and the community hasn't been much doing it. 

So Canonical is offering an optional service that provides that missing coverage. And they structured it so that enterprise users pay for it to subsidize individuals getting it free. Some folks can suggest a sinister purpose, but to me it looks like an honest attempt to address a real problem. The previous community-upload avenue is still open and available; the community is welcome to take up the slack anytime and render Pro moot.

Do you need this level of protection? Well, that's up to you. I prefer my CVEs to be mitigated, especially if I'll be sitting on that version for many years.

---

### Post by TheFu on 2023-12-09
> **Daveski17 said:**
> I don't disagree Fu, and I take as many precautions as I can (within reason). I'm usually patched and up to date (on Mac as well). I originally switched to Linux to avoid Windows and its dodgy security issues. I know Ubuntu isn't bulletproof, but I'm pretty sure I'm not compromised. I will probably never know for sure of course, unless I go off-grid and move into Faraday Cage. I am tempted sometimes ... lol.

I'm the same.  I patch weekly and disable things I don't use.  Once I forgot to disable Bluetooth after doing a fresh install, fully updated, and headed to a conference.  At the conference, my laptop was never out of my hands or on any wifi network there.  However, someone dropped a file on my desktop "I hacked this PC" - for fun.  When I saw that, I reloaded that evening in the hotel the entire OS and disabled bluetooth and wifi, then returned to the conference for the next few days.

Certain hardware solutions are just bad ideas, yet the world continues to use them for "convenience."  

BTW, I have a Faraday bag for my cell phone and use it far too often to be convenient for other people.  Being available 24/7 isn't my need. Once a day contact is sufficient, most of the time.

If I have any idea that something is wrong, I have no problem wiping the system and reloading.  My backup restore process is able to restore data from the last 90 days (pick a day) on most of my systems.  Some systems have a year of versioned backups. This means I can look for when any corruption may have happened, provided they didn't get the backup server.

---

### Post by Daveski17 on 2023-12-09
Luckily I don't use many universe packages.

---

### Post by Daveski17 on 2023-12-09
> **TheFu said:**
> I'm the same.  I patch weekly and disable things I don't use.  Once I forgot to disable Bluetooth after doing a fresh install, fully updated, and headed to a conference.  At the conference, my laptop was never out of my hands or on any wifi network there.  However, someone dropped a file on my desktop "I hacked this PC" - for fun.  When I saw that, I reloaded that evening in the hotel the entire OS and disabled bluetooth and wifi, then returned to the conference for the next few days.

Certain hardware solutions are just bad ideas, yet the world continues to use them for "convenience."  

BTW, I have a Faraday bag for my cell phone and use it far too often to be convenient for other people.  Being available 24/7 isn't my need. Once a day contact is sufficient, most of the time.

If I have any idea that something is wrong, I have no problem wiping the system and reloading.  My backup restore process is able to restore data from the last 90 days (pick a day) on most of my systems.  Some systems have a year of versioned backups. This means I can look for when any corruption may have happened, provided they didn't get the backup server.

Most of my important files (I mean music videos lol) are backed up on air-gapped drives. I think I'll be OK with bog-standard Ubuntu LTS update patches. I have more than one computer and OS anyway. They're all as secure as I can make them without getting too paranoid.

---

### Post by davedoxey on 2024-01-16
How do I stop Software Updater from asking me to install Ubuntu Pro every time?

I want to continue without Pro and not be bothered every time I run updater.

---

### Post by Frogs Hair on 2024-01-16
> **davedoxey said:**
> How do I stop Software Updater from asking me to install Ubuntu Pro every time?

I want to continue without Pro and not be bothered every time I run updater.

Try the following command.

```
sudo pro config set apt_news=false 
```

---

### Post by davedoxey on 2024-01-17
Did not work.  Software Updater still shows pro updates and suggests signing up for pro.

---

### Post by ian-weisser on 2024-01-17
Uninstall the vulnerable applications.

Or release-upgrade your system so you are running newer versions that aren't vulnerable.

You are complaining that you are being told that your roof leaks. Nobody likes that news, but it's still important to know. How you fix your roof is up to you.

---

### Post by davedoxey on 2024-01-18
No.  I am being bugged to install Ubuntu Pro.   My system and applications are kept up to date.  Software updater installs updates, but then invites me to subscribe to Ubuntu Pro, which I do not intend to do.  I want to stop updater from asking me every time I run it.

---

