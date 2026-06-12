---
title: "tor browser in noble  repo is broken - keyboard is not functioning"
date: 2024-03-06
forum: Ubuntu Development Version
---

### Post by luckyknight on 2024-03-06
With the provided tor browser in the noble repo, keyboard does not function for some odd reason.

Downloading instead the latest official release from the tor project website works however you cannot proceed as the tab immediately crashes. This is the same result when trying the alpha version.

Lastly, if I use the official deb repos to download tor instead ([https://deb.torproject.org/torproject.org/dists/](https://deb.torproject.org/torproject.org/dists/)) it does not yet contain a version for noble. If I use mantic, keyboard is not functioning still.

I am using default ubuntu wayland session.

---

### Post by guiverc on 2024-03-06
You could file a bug report...   

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I'm not having crashes with the tor browser on *noble*, but I have had issues with it last two weeks (I use it ~weekly), but I'm yet to explore further on another box which I like doing before I a file bug report.  My issue maybe what you describe as "*keyboard is not functioning still*", ie. I can use the browser, but typing in details using keyboard is *problematic*.

I'm using Lubuntu, thus LXQt & Xorg, but there are no known reported issues for Ubuntu *mantic* (23.10) that I'm aware of.

---

### Post by luckyknight on 2024-03-08
[https://bugs.launchpad.net/ubuntu/+source/torbrowser-launcher/+bug/2056578](https://bugs.launchpad.net/ubuntu/+source/torbrowser-launcher/+bug/2056578)

---

### Post by guiverc on 2024-03-08
The issue is not with the torbrowser-installer package though.

After my last comment, I grabbed the current Lubuntu *daily* for *noble* and booted it on a box, installed and ran the torbrowser-installer package, and the when ran installed torbrowser on the machine and it worked perfectly. 

The keyboard was working.. and I was able to use the torbrowser to search various web sites as a normal browser.

The issue with torbrowser on your setup & my own is somewhere else (I believe).. there are loads of issues appearing due to apparmor changes (*dec-2023 but fixes slowly flowing thru for reported issues last few weeks*) that actually does impact firefox when its installed as *deb* package.. but I don't understand the stack well enough to see a connection.

The tab immediately crashing no doubt is the apparmor issue I mentioned.. but that's not what is happening with the torbrowser when installed using the package in our repositories that Thomas maintains.

*I'll add the apprmor bug link in case helpful - *[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844) which shows a number of reported bugs for various programs that crash, and required rule change

---

### Post by luckyknight on 2024-03-09
Perhaps it is related to the default ubuntu desktop and not lubuntu? My system would not boot at all yesterday presumably due to an update.

So I downloaded yesterday current ISO, formatted, reinstalled, then installed torbrowser-launcher from noble repo and the issue with the keyboard still occurs.

I will try the tor provided version again as soon as the apparmor issue is fixed, do they also need to apply the fix to tor?

---

### Post by guiverc on 2024-03-09
> **luckyknight said:**
> Perhaps it is related to the default ubuntu desktop and not lubuntu? My system would not boot at all yesterday presumably due to an update.

So I downloaded yesterday current ISO, formatted, reinstalled, then installed torbrowser-launcher from noble repo and the issue with the keyboard still occurs.

I will try the tor provided version again as soon as the apparmor issue is fixed, do they also need to apply the fix to tor?

I used torbrowser on my *installed* Lubuntu system (*using mouse & clicking links, given no keyboard entry is possible here*), and was watching for clues as to why.. alas saw nothing.

Your results however are interesting to me.. If it worked with Lubuntu (*for me*) but not Ubuntu Desktop, I'd like to try a Xubuntu ISO as another comparison..  alas I'll not likely have time for a couple of days.  Maybe is the result of package difference.. that is a HUGE clue as to cause & also fix.

FYI:  This installed Lubuntu system was installed with Xubuntu media; includes Ubuntu Desktop, Xubuntu Desktop, let alone Lubuntu Desktop I'm actually using & more.. ie. it's a *bloated* system that is far from default packages.

*I've booted a Xubuntu noble ISO I had (2024-03-08 so not that old)* [I]and I'll try that if I can, though if I run out of time it maybe a few days before I can try again.

FYI:
-  Xubuntu daily (yesterday's) booted... 
-`sudo apt update` to update software lists
- apt install torbrowser-launcher
- torbrowser-launcher (run)
- started; connected; went to google.com & entered a search
- went to fridge.ubuntu.com 

... [/I]**works on Xubuntu too, just like Lubuntu.**

---

