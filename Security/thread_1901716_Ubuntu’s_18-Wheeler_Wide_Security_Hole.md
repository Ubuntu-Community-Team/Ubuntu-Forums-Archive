---
title: "Ubuntu’s 18-Wheeler Wide Security Hole"
date: 2011-12-29
forum: Security
---

### Post by newbie2 on 2011-12-29
[QUOTE="Roland Hughes"]Quite some time ago I filed bug 731504 with the launchpad system for Ubuntu (a registered trademark of Canonical Ltd.).  Ordinarily, this wouldn’t be something worthy of blogging about on the Fool, but this particular bug impacts every Fortune 1000 company that considers using their server software and it definitely impacts their many partners including IBM (NYSE: IBM) and Dell (NASDAQ: DELL).

This bug stems from a viciously short sighted marketing policy that will basically cause this famous Linux distribution to fade into the ether like hundreds of other Linux/Unix distributions most of us don’t remember. The marketing decision of trying to make “a distribution” fit on a single “live CD” instead of a “live DVD” might have gotten a lot of early adopters with old equipment, but it sent development on a downward spiral.

At the crux of this issue are the sins we commit in order to save space. The sin committed here was forcing everything developed with Nokia’s (NYSE: NOK) phenomenal Qt application development framework to use database plug-ins instead of statically compiled and linked connection code. This is a mortal sin no holy book on the planet can ever forgive. I pointed this out in a lengthy discussion and was actually told in an email by someone with an actual ubuntu.com email address:[/QUOTE]
[http://beta.fool.com/seasonedgeek/2011/12/28/ubuntus-18-wheeler-wide-security-hole/?source=eogyholnk0000001](http://beta.fool.com/seasonedgeek/2011/12/28/ubuntus-18-wheeler-wide-security-hole/?source=eogyholnk0000001)
:rolleyes:

---

### Post by SeijiSensei on 2011-12-29
It's open-sourced.  If you think you need statically-linked binaries to replace the ones from the distro, you can compile them yourself.

As for servers, most of us run them without GUIs, so I fail to see how Qt plays a role.

---

### Post by d3v1150m471c on 2011-12-29
I think the 18 wheeler wide security hole exists somewhere between the computer and the chair.

---

### Post by CharlesA on 2011-12-29
> **SeijiSensei said:**
> It's open-sourced.  If you think you need statically-linked binaries to replace the ones from the distro, you can compile them yourself.

As for servers, most of us run them without GUIs, so I fail to see how Qt plays a role.

This. I know my server doesn't run a GUI and I'm sure that more than 90% of them are run headless, where it would be pointless to run a GUI.

> **d3v1150m471c said:**
> I think the 18 wheeler wide security hole exists somewhere between the computer and the chair.

I lol'd. Thank you.

---

### Post by spynappels on 2011-12-30
> **d3v1150m471c said:**
> I think the 18 wheeler wide security hole exists somewhere between the computer and the chair.

Comment of the day for me!

Just the usual FUD.

---

### Post by uRock on 2011-12-30
Bug report says invalid. [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/731504](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/731504) Thread Closed.

---

