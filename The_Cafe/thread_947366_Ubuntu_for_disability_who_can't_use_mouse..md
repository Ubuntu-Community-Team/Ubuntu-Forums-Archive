---
title: "Ubuntu for disability who can't use mouse."
date: 2008-10-14
forum: The Cafe
---

### Post by Masoris on 2008-10-14
Original post (Korean language): [http://www.ubuntu.or.kr/viewtopic.php?f=4&t=1872](http://www.ubuntu.or.kr/viewtopic.php?f=4&t=1872)

A disability person asked to korean ubuntu forum. He said he can't use both two hands, and one foot. So he use computer to use only one foot. He has hardness to click mouse, so he is using computer with 'mouse key' function of Windows.

What he said is:
> Hi I'm a handicapped person who cannot use mouse at all. Ubuntu looks nice, but it's a useless OS for person like me . I can't do nothing without help of others. I think Ubuntu should ask if user has disability when Ubuntu start to install. I coundn't use Ubuntu with only 'Tab key'. (Comment: He said he could select 'start menu' by tab key on Windows, but he coundn't on Ubuntu) So.. I hope that someone who can speak English well, mail to Canonical about this.

So, What should I do? I don't know how to answer him.

---

### Post by pp. on 2008-10-14
There's a whole subforum dedicated to such issues: It is called ***Assistive Technology & Accessibility***

[http://ubuntuforums.org/forumdisplay.php?f=145](http://ubuntuforums.org/forumdisplay.php?f=145)

There also are quite a few settings in the systems as it comes 'out of the box'. Sorry, I can not go and look at the moment what these settings are not called as I am not near an Ubuntu computer right now.

---

### Post by Mr. Picklesworth on 2008-10-14
[Dasher]("http://www.inference.phy.cam.ac.uk/dasher/") - which is available in the Ubuntu repositories - could be of interest to the guy. It requires a mouse, but he has one working foot, right? It is a very good text input system that requires no clicking; just move the mouse over the letters as they come. Hard to describe it, really, but even I use it sometimes and I'm not disabled :)

There is mouse key functionality in System -> Preferences -> Keyboard. If clicking is the problem with mice, there is a feature called Dwell Click in System -> Preferences -> Mouse -> Accessibility.

The GTK interface toolkit (used by most applications included in Ubuntu) is designed to handle tabbing and whatnot on its own, without needing extra explicit assistance from the application generating an interface. As a result, just about everything supports it smoothly.
For reference, Ctrl + Alt + Tab switches focus to panel and desktop windows so you can tab between applets on those (which is important for one who can't use a mouse).

GNOME does a good job of having functionality accessible via a window menu. As usual, Alt + the underlined letter in a menu title will open it. If there is more than one thing underlined, (for example both a button somewhere and a menu with "e" underlined) you can press the same combination to toggle between each one.

Menu accellerators (shortcut keys) can be customized. Just select the item in the menu and press a key combination or a special key like one of the Function keys. That may have to be turned on in System -> Preferences -> Appearance -> Interface.

---

### Post by hessiess on 2008-10-14
he would probably be better off with a tiling WM and a bunch of XTerms, no mouse needed for that;)

---

### Post by Masoris on 2008-10-14
> **Mr. Picklesworth said:**
> [Dasher]("http://www.inference.phy.cam.ac.uk/dasher/") - which is available in the Ubuntu repositories - could be of interest to the guy. It requires a mouse, but he has one working foot, right? It is a very good text input system that requires no clicking; just move the mouse over the letters as they come. Hard to describe it, really, but even I use it sometimes and I'm not disabled :)
Dasher looks nice :) But he don't need it, because he looks type well with one foot. The problem is he cannot grip mouse by foot, so he use only keyboard for computer.

> **Mr. Picklesworth said:**
> There is mouse key functionality in System -> Preferences -> Keyboard. If clicking is the problem with mice, there is a feature called Dwell Click in System -> Preferences -> Mouse -> Accessibility.
That looks very nice. I'll write this on Korean forum.

> **Mr. Picklesworth said:**
> The GTK interface toolkit (used by most applications included in Ubuntu) is designed to handle tabbing and whatnot on its own, without needing extra explicit assistance from the application generating an interface. As a result, just about everything supports it smoothly.
For reference, Ctrl + Alt + Tab switches focus to panel and desktop windows so you can tab between applets on those (which is important for one who can't use a mouse).

GNOME does a good job of having functionality accessible via a window menu. As usual, Alt + the underlined letter in a menu title will open it. If there is more than one thing underlined, (for example both a button somewhere and a menu with "e" underlined) you can press the same combination to toggle between each one.

Menu accellerators (shortcut keys) can be customized. Just select the item in the menu and press a key combination or a special key like one of the Function keys. That may have to be turned on in System -> Preferences -> Appearance -> Interface.
Thank for your answering. But I'm not sure could key combine keys by one foot.

---

### Post by Masoris on 2008-10-14
> **hessiess said:**
> he would probably be better off with a tiling WM and a bunch of XTerms, no mouse needed for that;)

No~! He is not a geek like YOU;) Was Ubuntu a geek OS?

---

### Post by pp. on 2008-10-14
> **Masoris said:**
> That looks very nice. I'll write this on Korean forum.

Yes, please do that. I think it very important that there are people who can act as interpreters between the different forums.

> **Masoris said:**
> I'm not sure could key combine keys by one foot.

As far as I can remember you can configure the keyboard such that you can press the alt key and a letter after each other instead of at the same time.

---

### Post by hessiess on 2008-10-14
> **Masoris said:**
> No~! He is not a geek like YOU;) Was Ubuntu a geek OS?

actually I was being serious, you DON'T need a mouse to use the command line.

---

### Post by Masoris on 2008-10-14
> **pp. said:**
> As far as I can remember you can configure the keyboard such that you can press the alt key and a letter after each other instead of at the same time.
I found it. "Sticky keys" function on Keyboard preference. :)

---

### Post by Mr. Picklesworth on 2008-10-14
I, too, am a fan of the command line in terms of accessibility. Bash, for example, offers a great interface with autocomplete (tab key hints) for *everything*. For example, one could run a terminal inside a GNOME environment so that he gets the accessibility features but also has the ability to really rapidly input information with an environment that fits his specific capabilities like a glove.
GUIs always have little things (like drag and drop) that are next to impossible for the disabled. The CLI requires no particularly physical aptitude whatsoever; all it cares about is keyboard input, which can be done any way the user wants (including Dasher with eye tracking).

Of course I'm not physically disabled so I won't be touting that thought religiously as if I understand the situation, but it really is worth a try, even with the terminal just as a shell that launches GUI applications like Epiphany and the chosen word processor. It'll make way more sense for file management, and it is nothing like the infamous DOS. The interface is a tad confusing at first, but totally awesome after some fiddling.

Sticky keys you'll want. You can configure all the various window switching key combinations under System -> Preferences -> Keyboard Shortcuts.
Another tip: Disable Compiz. If having pretty windows is really necessary, try enabling compositing with Metacity under gconf-edit: go to /apps/metacity/general, then activate the key called "compositing_manager" (set it to 1, or check the box). Metacity follows the window manager rule book a lot better than Compiz does, and while not as glamourous it is extremely functional and has some solid accessibility.
(What a window manager is meant to do, it does well. What a window manager is not meant to do, it does not do. It is the opposite of Compiz).
Metacity is the window manager GNOME is designed with and what Ubuntu used to have by default. For some reason Compiz was adopted as default a few releases ago, although you may be using Metacity already depending on the computer's graphics capability. Check System -> Preferences -> Appearance -> Visual Effects and turn them off.

---

### Post by noctis_vulpes on 2008-10-14
A little update on this subject... Looks like his problem was the fact that

1. He can't use a mouse
2. He (probably) has difficulty using keyboard shortcuts involving multiple keys.

So his main valid complaint was that the gnome menu was not accessible if you are more or less limited to one key. Because in order to set anything up, one would have to use that at least once (unless he skips GUI altogether and uses CLI - but he's not used to that kind of computing), so this means that in cases like this person, they would require another person's assistance at least once during the installation.

---

### Post by zmjjmz on 2008-10-14
A bit of a hijack, but how am I to use the mouse keys?
I checked the box but I'm not sure what keys to press...
> 
So his main valid complaint was that the gnome menu was not accessible if you are more or less limited to one key. Because in order to set anything up, one would have to use that at least once (unless he skips GUI altogether and uses CLI - but he's not used to that kind of computing), so this means that in cases like this person, they would require another person's assistance at least once during the installation.
System > Preferences > Keyboard Shortcuts
Set panel menu to Super L or something. Now he probably would need someone to help him with the installation, as he probably would need help in the first place putting the CD in.
Oh and he could use Vimperator for Firefox to make his life easier when browsing.

---

### Post by klange on 2008-10-14
Sounds like the guy should get a touchpad for his foot if he has the control to use it. Would definitely open up some possibilities.
@zmjjmz: Sp+L? L is on the opposite side of the keyboard than Super, that would be really hard to use. Alt and F1 are a lot closer.

---

### Post by zmjjmz on 2008-10-14
> **WindowsSucks said:**
> 
@zmjjmz: Sp+L? L is on the opposite side of the keyboard than Super, that would be really hard to use. Alt and F1 are a lot closer.

Super L means left Super; i.e. the Super on the left.
Hey, it's the keyboard preference's notation, not mine.

---

