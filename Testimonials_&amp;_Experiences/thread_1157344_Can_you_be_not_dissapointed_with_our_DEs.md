---
title: "Can you be not dissapointed with our DEs?"
date: 2009-05-12
forum: Testimonials &amp; Experiences
---

### Post by cguy on 2009-05-12
Let me begin this by saying that I am an Ubuntu enthusiast and Linux supporter. I made the full switch almost 2 years ago and never missed Windows.
This is not a trolling / "Linux sux" attempt!


I use the Jaunty and it honestly is the best OS I ever had on my computer.
Today, however, I stumbled across some bugs which shouldn't be part of a "desktop ready" wannabe OS.

The first one is related to the stock Date-Time-Weather applet. While at first it showed the proper data (hot, no winds), slowly but surely it showed clouds, then added strong winds and ended up reporting thunderstorms and heavy winds. You guessed it: not much changed outside.

The second one is part of the same applet: appointments and alarms. Evolution has some bugs a first time user can't avoid meeting but I won't get into them here. Besides the fact that you must set an e-mail account in order to use alarms, deleting that account leaves the alarms showing under the calendar and there's no way to delete them but creating a new, 'fake' account in Evolution and deleting them from there.

Third: the session saving feature. I saved my session yesterday hoping it would properly restore today. Didn't happen but that didn't bother me much. What made me mad was the fact that the last, faulty saved session kept on being restored despite the fact that I disabled the restoration. Luckily, I am a bit experienced and manually deleted the proper files. 
One year ago (YES, this bug is at least one year old) this kind of thing made me format and reinstall. I didn't have the know-how or the base of knowledge to do a useful google search.


Forth: the stupid, annoying, retarded and so on and on and on, THREE YEARS OLD BUG (at least) keyring manager. Mail Notification, Evolution, proper Network Configuration and possibly many others are unusable because of the password requesting Keyring Manager when autologin is enabled. (actually, they are usable, but extremely annoying!)
You either have to disable autologin (won't happen) or use a null keyring password (won't happen) to avoid the bug.
I'll just skip some of these programs, as I did in the last 2 years, and hope the bug will be fixed before I die. And I'm a young fella. :)


So I thought: why not try KDE4? It's 1 and a half years old and has been updated. Big mistake!!!
You can't move a launcher from one panel to another, you can't add a launcher unless you have a Kickoff menu on the specific panel you want to add the launcher to, you don't have the availability of basic widgets (but you have Comic Strip and Bball), you can't switch too much between Kickoff and Classic menu before switching stops working and blank spaces appear on the panel and you can't install new widgets from the dialog the KDE team provides (but they do show up borked and undeletable in the list).
And mounting partitions doesn't work and Google doesn't provide meaningful results (I'll file a bug)
L.E: +desktop effects can't be controlled with mouse+keyboard. How stupid is that?
It's 1 and a half years old, for crying our loud!!!

But it looks great! (no sarcasm here. I like the looks of KDE)



All these happened today.

Do you still think these DEs are ready for average Joe?
Well, at least Gnome is... until you want more than the basics.

---

Disclaimer: I will file bugs and ideas at Brainstorm for most of these problems by the end of the week.

---

### Post by 3rdalbum on 2009-05-12
1. The date/time/weather applet relies on information provided by your local weather service. If they feed wrong information to the applet, then the applet will still display it.

2. File a bug report; I don't know if any developers or testers would have thought of deleting an e-mail account that already has a populated calendar. I don't think many people would come across that one.

3. I thought they'd removed the session saving?

4. It's not a bug, it's by design.

No desktop is perfect. I recently had the privilege of trying out Mac OS X again. My WEP passphrase wouldn't work, and I was getting "connection timeout" as the error message. I had to put in the WEP key instead. There was also no apparent way of accessing my hidden Samba share. Oh, and every single time I tried connecting to my wireless network it insisted that it wanted to "Add it to keychain" or "Remember password", even if I unticked those options in the control panels.

---

### Post by cguy on 2009-05-13
> **3rdalbum said:**
> 1. The date/time/weather applet relies on information provided by your local weather service. If they feed wrong information to the applet, then the applet will still display it.
[B]I thought the same, but upon reboot it showed the right data. Maybe it was a coincidence and the weather station upgraded the conditions in those few minutes. :)
I'll research some more on this.[/B]

4. It's not a bug, it's by design.
**Well, it is really stupid.**

.

---

### Post by SunnyRabbiera on 2009-05-13
Well for KDE4, its still very experimental.
As for your other issues I am unsure, the weather applet bug we cant help out with as its not an official part of the desktop, I would send the bug to its developers.
Same with the other bugs, Ubuntu does not make the apps you see as they are developed on their own,

---

### Post by 3rdalbum on 2009-05-13
> **cguy said:**
> 4. It's not a bug, it's by design.
**Well, it is really stupid.**

Obviously enough Gnome developers think it's a good idea; I'd tend to agree with them. Thieves who steal computers tend to just be regular thieves, not uber hackers who can discover your password or even install an operating system. After a couple of days, it will take you about 2-3 seconds to type your password; does this delay matter?

You can always set a null password for your keyring, which means it will be unlocked even on autologin. Or, you can disable automatic login and your password-protected keyring will be unlocked on login. I don't see why you want your keyring to be unlocked on login without you specifying a password, but you don't want to have no password on your keyring - it's virtually the same thing!

---

### Post by Methuselah on 2009-05-13
> 
I don't see why you want your keyring to be unlocked on login without you specifying a password, but you don't want to have no password on your keyring - it's virtually the same thing!


Good, I'm not the only person who didn't understand this part.

---

### Post by Bios Element on 2009-05-13
As for the weather applet, I imagine it caches the data feed and updates every xyz minutes. So when you rebooted it checked and cached an updated feed.

---

### Post by ashmew2 on 2009-05-13
Why dont you try Fluxbox or others ? Im sure if you try you can find the perfect DE for yourself..Linux is all about choice remember ? :D

---

### Post by 3rdalbum on 2009-05-14
There are a lot more than Gnome and KDE; you might find LXDE more to your liking?

---

### Post by cariboo on 2009-05-14
I have no idea where you live, but around here we say if you don't like the weather where your at, just drive down the road 10km or keep driving until you find something you like. I live 20km by road from the airport, but it is only 10km away as the crow files, I can see the weather over the airport from my office window, and more often then not it is different, then it is right here.

---

### Post by lisati on 2009-05-14
> **3rdalbum said:**
>  I don't see why you want your keyring to be unlocked on login without you specifying a password, but you don't want to have no password on your keyring - it's virtually the same thing!

Ditto!

Although I'm the only person likely to use my gear, there's always some kind of security. About the only exceptions to this is the XP install on one of my machine (and a casual user would have to figure out accessing the grub menu to boot XP) and my old Win98 machine (nothing sensitive stored on that machine)

---

### Post by XubuRoxMySox on 2009-05-15
> **3rdalbum said:**
> There are a lot more than Gnome and KDE; you might find LXDE more to your liking?

I'm using [LXDE]("http://lxde.org") for two reasons:

1.) - It is very lightweight, fast, and fully customisable, and

2.) - It's super-simple newbie friendly, especially when you let PCMan (file manager) manage the desktop. Mine looks and feels like WinXP (which is all I've known until Ubuntu, a little less than two months ago).

The next attempt at making a true "Ubuntu Lite" is going to have LXDE as its default because of it's speed, simplicity, and very minimal appetite for resources. Thus the name, "Lubuntu."

It works well installed on top of [Crunchbang]("http://crunchbanglinux.org"), a very minimal Ubuntu installation designed to work on older hardware - again, let PCMan manage the desktop to avoid bugs.

-Robin

---

