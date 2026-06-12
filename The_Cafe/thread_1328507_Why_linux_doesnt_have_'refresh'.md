---
title: "Why linux doesnt have 'refresh'?"
date: 2009-11-16
forum: The Cafe
---

### Post by emigrant on 2009-11-16
Hi,
What is the technical reason behind linux doesnt have 'refresh'. Yes i mean what u do right clicking on MS desktops.
Some new people to linux whom i helpd to instal linux think this is a set back in linux making them unable to refresh the system. Though i know this is a silly thought i donno how to clarify to them.
Any explanation would be greatly appreciated.

Thank you very much for your time.

---

### Post by Twitch6000 on 2009-11-16
It does have a refresh..

You just pres cntrl and f5.

---

### Post by philinux on 2009-11-16
Mouse click anywhere on Desktop and just click F5. Same in any folder.

---

### Post by emigrant on 2009-11-16
Guys, i mean does linux realy need that feature? Why hvnt the devs explcitly include that? I remember somebody told me linux is multiproces and thus need not refreshing, is that true? If so whys that cntr plus f5 thing?

---

### Post by ArinSky on 2009-11-16
> **emigrant said:**
> Guys, i mean does linux realy need that feature? Why hvnt the devs explcitly include that? I remember somebody told me linux is multiproces and thus need not refreshing, is that true? If so whys that cntr plus f5 thing?

the kernel is separate from the processes if that what you mean... most of the time when you change something you won't need to refresh unless you change something in the kernel or something goes weird. Also the reason you don't have to restart after every update like you had to with windows.

---

### Post by Locke_99GS on 2009-11-16
For the most part you shouldn't ever need to "refresh" the file manager in Linux. In my case, I didn't even know you could on Linux, because in the few years I've been using it as my primary (and sole, on other desktops and my laptop) operating system I have never needed to.

It detects changes and refreshes itself on the fly.

---

### Post by scorp123 on 2009-11-16
> **emigrant said:**
>  What is the technical reason behind linux doesnt have 'refresh'.
 It has. But you rarely ever need it. Linux's desktops should auto-refresh if they need to do so.

> **emigrant said:**
>   Yes i mean what u do right clicking on MS desktops. That's a useless function in Windows because Windows doesn't get it when it needs to refresh or not. So sometimes when you add or remove icons from a Windows desktop, move a lot of program windows around, it could happen that parts of the screen get incorrectly re-drawn and you end up having graphical garbage on the screen. That's what this "refresh" function is for, because Windows is designed in such stupid ways.

> **emigrant said:**
>  Some new people to linux whom i helpd to instal linux think this is a set back in linux making them unable to refresh the system. "Refresh the system" is wrong anyway. You don't refresh the system, you just tell the desktop part to repaint the icons and the wallpaper. That's it. It doesn't do anything for the rest.

 And it's a superstition if anything. It doesn't help at anything. It does not prevent programs from misbehaving on Windows. And on Linux you won't even need this function too often because Linux desktops environments such as GNOME and KDE should notice it themselves if their desktop needs to be refreshed or not.

> **emigrant said:**
>  Though i know this is a silly thought Tell them Linux is so great that it happens automatically whenever it needs to happen. Best of all: this explanation is true and correct.

---

### Post by lovinglinux on 2009-11-17
KDE desktop has a "Refresh Desktop" menu option, which is essentially the F5 shortcut already mentioned.

I usually don't use it, but today I did. I was programming a Firefox extension that creates some desktop folders when installed, but due to some reason, the newly created folders didn't appear on the desktop until I clicked the "Refresh Desktop".

---

### Post by scorp123 on 2009-11-17
> **lovinglinux said:**
>  the newly created folders didn't appear on the desktop until I clicked the "Refresh Desktop". Sometimes newly created icons might be outside of your visible area. Happened to me. So when I looked on the desktop: No icon. When I checked via **"ls -al ~/Desktop"** my newly created icon was clearly listed. So I had to click something like "sort Icons by name" or something like that to get the icon back into the visible area ...

Maybe it was something like this in your case?

---

### Post by lovinglinux on 2009-11-17
> **scorp123 said:**
> Sometimes newly created icons might be outside of your visible area. Happened to me. So when I looked on the desktop: No icon. When I checked via **"ls -al ~/Desktop"** my newly created icon was clearly listed. So I had to click something like "sort Icons by name" or something like that to get the icon back into the visible area ...

Maybe it was something like this in your case?

Nope, they were in place, just not visible.

---

### Post by NightwishFan on 2009-11-17
It would only be needed if somehow an icon was not updated to be visible yet. As was said before it is not a system wide feature. The nautilus file manager draws the desktop.

---

### Post by suitedaces on 2009-11-17
[http://ubuntuforums.org/showthread.php?t=1163398](http://ubuntuforums.org/showthread.php?t=1163398)

---

### Post by RiceMonster on 2009-11-17
I guess it's assumed that you'll have fam or gamin running so you won't need it. Still, you'd then have to know about F5 if it's not running or it crashes or something.

---

### Post by scorp123 on 2009-11-17
> **suitedaces said:**
> [http://ubuntuforums.org/showthread.php?t=1163398](http://ubuntuforums.org/showthread.php?t=1163398)

Yes, I knew that. When I worked for Hewlett-Packard I have met plenty of people from all over the world ... and some really had strange habits, at least from an European point of view. I guess the same might also be true vice versa :D

---

