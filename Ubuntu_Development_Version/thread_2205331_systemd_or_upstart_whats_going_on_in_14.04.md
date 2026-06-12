---
title: "systemd or upstart? whats going on in 14.04?"
date: 2014-02-13
forum: Ubuntu Development Version
---

### Post by sam-c on 2014-02-13
systemd or upstart? whats going on in 14.04?
Uncle Sam
Thanx

---

### Post by grahammechanical on 2014-02-13
Why should anything be going on? Upstart was originally developed for Ubuntu and at first it was used by Fedora which then switched to SystemD when it became available under the GPL.

Read the history

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

[http://0pointer.de/blog/projects/systemd.html](http://0pointer.de/blog/projects/systemd.html)

There is an important point about the word "Free" as in 'Free and Open Source Software' and the point is that developers are free to use whatever open source code they chose to use. So, why should anything be going on? Why should one group of developers be denied the freedom to use their choice of open source code. And that is what these types of question are trying to do: take away freedom.

There are, in fact, systemD libraries in Trusty Tahr. I guess they are there for compatibility reasons. In actuality, Upstart is being used in the Ubuntu phone platform to reduce the resource footprint of Ubuntu phone/tablet platform. Services are being identified which can be switched off by Upstart after the system has loaded because they are no longer needed. Or switched off and then on when needed. All this work for the mobile platform will benefit the desktop under the convergence strategy. How much of it will get into 14.04 is any body's guess. My guess would be to say, "very little," as convergence with the desktop is aimed not at 14.04 but 14.10 or even 15.04.

There is already a thread here for this question.

[http://ubuntuforums.org/showthread.php?t=2200186](http://ubuntuforums.org/showthread.php?t=2200186)

Regards.

---

### Post by grahammechanical on 2014-02-14
Latest decision on this subject. But if I read this correctly, nothing will change for a long time.

[http://www.markshuttleworth.com/archives/1316](http://www.markshuttleworth.com/archives/1316)

Regards.

---

### Post by philinux on 2014-02-21
Looks like 14.10
[http://www.techdrivein.com/2014/02/ubuntu-leaving-upstart-for-systemd.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+techdrivein+(Tech+Drive-in)&m=1](http://www.techdrivein.com/2014/02/ubuntu-leaving-upstart-for-systemd.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+techdrivein+(Tech+Drive-in)&m=1)

---

### Post by grahammechanical on 2014-02-21
14.10 development branch more likely. I hope that this decision does not detract from convergence. Upstart is on the phone/tablet. Convergence would not be so converged if the phone had upstart and the desktop had systemd. So, in my ignorant opinion I cannot see this change happening any time soon. I wait to see what comes out at the next 2 or 3 UDS.

I think that 16.04 LTS should be the target release. Get Ubuntu phone + tablet + superphone + desktop convergence, get market share and then see about being more Debian than Ubuntu already is. After all, how far along is Debian in changing from Upstart to SystemD?

Regards.

---

### Post by rrnbtter on 2014-02-21
Greetings,
I don't have an iron in this fire but I do get the OP. All articles aside, there has been heavy updates for Upstart since early January, a few for Systemd. So "whats going on" does seem like the appropriate question. Come to think of it I do remember asking myself that same question. In light of the heavy Upstart updates I'm not satisfied with the informatin in the Shuttleworth article. At the same time I also projected that I would be using Mir with 14.04. Our current problem must be a "dual personality disorder". All that being said I am absolutely delighted with what I have. Can't wait for the LTS. I think I will leave my wife on it even if I move on to 14.10.

---

### Post by henning3 on 2014-04-17
My nose was pushed on this after nm-applet was not working anymore in 14.04 today. The problem was a missing pam-module
systemd_pam.so in the /etc/pam.d/ files (lxdm for me) [1]. Adding 
session optional pam_systemd.so
[FONT=arial]
resolved it and made me google, why ubuntu now seems to use systemd (at least partly). I like systemd, but they should introduce it transparently...
[/FONT][FONT=arial][1] [https://bbs.archlinux.org/viewtopic.php?pid=1149490#p1149490](https://bbs.archlinux.org/viewtopic.php?pid=1149490#p1149490)[/FONT]

---

### Post by grahammechanical on 2014-04-17
> [COLOR=#000000][FONT=arial]they should introduce it transparently...[/FONT][/COLOR]

What does that mean? Shuttleworth said that Ubuntu would use SystemD and that users would not notice any difference. Window pane glass is transparent. I see through it and often without noticing it is there. So, a change over from Upstart to SystemD without my noticing it is transparent as far as I understand the meaning of transparent.

And yes, I have been noticing the SystemD libraries being introduced during daily 14.04 updates. I see nothing sneaky or underhanded about any of this.

Edit: The 14.04 release notes show that Upstart is still being used.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

---

