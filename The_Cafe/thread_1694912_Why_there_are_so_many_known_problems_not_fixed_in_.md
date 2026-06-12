---
title: "Why there are so many known problems not fixed in Ubuntu?"
date: 2011-02-25
forum: The Cafe
---

### Post by grandixximo on 2011-02-25
I was just wondering, i got Ubuntu last week, first installed the 10.10 for netbook, uninstalled after 2 days because i couldn't delete files from the default file browser, and because it took away too much space on my small screen even tough when i downloaded it it days that the interface was i quote "Designed specifically for the smaller screen", and most of all the interface had little customization.
Then i went on 10.10 for desktop, i finally could customize everything that i wanted, but boy was it a pain in the ***, first of all why the hell evolution does not minimize like empathy does in the wonderful applet for communication that has a mail icon, i have fix this, took me a week since i'm a noob but i did it using the instruction in this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475703](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475703)

Then i started playing my favorite TV shows with Totem and i didn't have sound and countless error message where displayed this is a known bug, and can be fixed if you uninstall gstreamer 0.10, did it and it's working.

Other issue white tray icon background, another known issue that is being around for years as i have read, there is a nice fix with modified system files, i'll do it this evening following the instruction here

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1427968&page=5](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1427968&page=5)

Other issue QQ in empathy maybe many of you do not know this nice messanger, well it looks like it's not working with empathy even tough you can add a QQ account it will never login, at least remove it so that people won't try to get connected for nothing...

Just wondering why so many known bugs and no fixes???

---

### Post by zenwalker on 2011-02-25
Thats why there is an update manager which runs right? I belive its due to the short release span of 6 months.

---

### Post by grandixximo on 2011-02-25
i'm saying that some of this are bugs known since version 7, we are version 10 why they are still around?

If you are saying that i should wait for a bug fix with an update, for issue that have been around for years, if they have not been fixed by now i could wait for a very loooong time...

I have fix the issue myself, and i actually love to do this things, but someone else may give up, what i have read most of the time on this bug fixes thread is "this are the little things that made me use other OS" or lines like that, i really don't understand why on a system that run so smooth and fast, they have to get lost on this small issues that make people go crazy and decide to move on other OS...

---

### Post by Lucradia on 2011-02-25
You need to get the bug fix approved for implementation first. If it's denied, it may not show up on the bug reports, or threads linked to them.

Have you seen these issues on the brainstorm site? Also note that Linux itself is not a profit organization; nor, do I believe, is Canonical. They may make profits on some things though.

However, Epiphany, being part of the GNOME Project, is handled by the gnome project. If you wish to report something gnome-specific, straight to the people who own the software, or made the code, you must go to the gnome bugzilla; not ubuntu's forums, or ubuntu's launchpad, but gnome's bugzilla. Yes, there is one; GNOME doesn't track bugs via Launchpad (Nor does XFCE for that matter, nor Midori (twotoasts.de))

It's because of this, that the bugs may not be resolved. People think they have to report it here, not there.

---

### Post by zenwalker on 2011-02-25
Chance are that those bugs reported may not be reproducible every where by every one to gets fixed or it may be that it cant be fixed at all.

---

### Post by Lucradia on 2011-02-25
> **zenwalker said:**
> Chance are that those bugs reported may not be reproducible every where by every one to gets fixed or it may be that it cant be fixed at all.

GNOME 2 Panel background issues are reproducable always. (this depends on the program that's sending the icon to gnome panel though. IE: Pidgin has issues keeping transparency on GNOME Panel.)

Epiphany > Tray is an enhancement / trivial.

Adding QQ is an enhancement, not a bug.

^ Also what I said above; it's not reported in the right place.

---

### Post by grandixximo on 2011-02-25
i have seen that bugs have already been reported, if i have time i'll try to report them too in the right place.

---

### Post by Lucradia on 2011-02-25
> **grandixximo said:**
> i have seen that bugs have already been reported, if i have time i'll try to report them too in the right place.

I know GNOME's bugzilla already has both as bug reports, both enhancements (for their gnome messenger.)

Sorry if I said epiphany before, the messenger and browser both start with E.

---

### Post by YesWeCan on 2011-02-25
It strikes me as odd that fedora comes with a bug report application in its pull down menu but Ubuntu does not. Ubuntu used to but Canonical removed it.
I tried to report a bug and it isn't exactly easy.

---

### Post by Lucradia on 2011-02-25
> **YesWeCan said:**
> It strikes me as odd that fedora comes with a bug report application in its pull down menu but Ubuntu does not. Ubuntu used to but Canonical removed it.
I tried to report a bug and it isn't exactly easy.

It's still there, but you have to initiate it via terminal iirc, and install it if it isn't there, you also must have a launchpad account, you also must know the package's name.

---

### Post by YesWeCan on 2011-02-25
I guess there are enough to be getting on with...

---

