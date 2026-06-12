---
title: "releasing Asterisk 1.8 to 10.04"
date: 2010-10-25
forum: Server Platforms
---

### Post by zanophol on 2010-10-25
Does anyone have any plans on releasing Asterisk 1.8 into 10.04 via either the backports repo or through their own ppa?

I see someone started one on launchpad on 10/22/10, but it never finished.

---

### Post by dajhorn on 2010-11-08
I've built all of Asterisk 1.4, Asterisk 1.6, and Asterisk 1.8 for Lucid and Maverick in this PPA:

  [https://launchpad.net/~dajhorn/+archive/pkg-voip](https://launchpad.net/~dajhorn/+archive/pkg-voip)

This is another PPA with Asterisk 1.8:

  [https://launchpad.net/~jmdault/+archive/asterisk-testing](https://launchpad.net/~jmdault/+archive/asterisk-testing)

---

### Post by zaber on 2011-04-18
I know this thread is a little old, but 10.04 is still the current LTS version.  There are external repositories run by Digium listed in the Asterisk WIKI with the latest versions. [https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages](https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages)

---

### Post by kevpatts on 2012-07-12
Just thought I'd update this with my experience doing this.

I've just updated lucid using the official repos for this here: [https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages](https://wiki.asterisk.org/wiki/display/AST/Asterisk+Packages). I did this because Festival is broken in the lucid version.

I had no issues with my dialplan. Everything working fine.

Festival is now nearly working (it's cutting off the start of the sentance). I think that's cause the CPU on the VM can't handle it though.

---

