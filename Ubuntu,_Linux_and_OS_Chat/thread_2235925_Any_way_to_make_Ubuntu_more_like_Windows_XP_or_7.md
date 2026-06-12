---
title: "Any way to make Ubuntu more like Windows XP or 7?"
date: 2014-07-23
forum: Ubuntu, Linux and OS Chat
---

### Post by etep513 on 2014-07-23
I have been using Windows XP and 7 for years.  In the past few days, I have installed 14.04 on my desktop and started experimenting with it.  My honest impressions are that it's too mac-like for me.  Is there any way that I can change the settings so that it is more like windows (with a task bar and desktop icons)?

---

### Post by Jerry N on 2014-07-23
Install the Mate desktop or replace Ubuntu 10.04 with Linux Mint 17 with the Mate desktop.

Jerry

---

### Post by slooksterpsv on 2014-07-23
You could also switch to Kubuntu, Xubuntu or Lubuntu. Here's a screenshot of my Xubuntu desktop:
[ATTACH=CONFIG]254960[/ATTACH][ATTACH=CONFIG]254961[/ATTACH]

---

### Post by whitesmith on 2014-07-23
You could also use a different desktop environment. Linux (unlike Windows) supports many of them, each with a different look and feel. Try Gnome. You can download it from the Software Center. It has a much more Windows-like appearance than Unity (what you get out of the box). Be sure to read the first reference in my signature line before jumping in (or out!).

---

### Post by Mike_McHrl on 2014-07-23
Switching to Kubuntu is fairly easy and good choice.

---

### Post by Bucky Ball on 2014-07-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. ;)

We get this question often. Do not be surprised if another staff member moves this thread to ***Recurring Discussions***.

Xubuntu (or Xfce4) could probably be made to look like Windows fairly easily.

---

### Post by buzzingrobot on 2014-07-23
> **whitesmith said:**
> You could also use a different desktop environment. Linux (unlike Windows) supports many of them, each with a different look and feel. Try Gnome

Hmmm?  If anything, Gnome looks more like OS X than Unity.

Anyway, Win XP and Win 7 use a panel-and-menu interface. Other than Unity and Gnome, all the major interfaces available for Ubuntu are panel-and-menu based. 

These interfaces can be added to an existing Unity installation. But, due to their size and complexity, they can be rather difficult to uninstall cleanly.

So, my recommendation to someone very new to Ubuntu and Linux is to try the Ubuntu "flavors" that use panel-and-menu interfaces and see if you like them.  You do not need to install them for this.  You can try them via the "Try..." option you saw when you installed Ubuntu Unity. (They all use essentially the same installer.)

The KDE interface is used by Kubuntu. 
The LXDE interface is used by Lubuntu. (Especially targets older and less powerful hardware)
The XFCE interface is used by Xubuntu.

Google for those names and the distribution's home page should be the first result returned.

You should also check out the Linux Mint distributions. (Linuxmint.com)  Linux Mint is based on Ubuntu -- meaning it is built on Ubuntu and its users access software on Ubuntu repositories, and uses the Ubuntu installer. Linux Mint targets new users.

Mint has releases that use KDE and XFCE.  They also have a release using the Mate interface and another using the Cinnamon interface, both panel-and-menu based. You should investigate all their releases before making a final choice. (Their install images all boot automatically into "try" mode.)

(Oops, forgot: There's an entire Ubuntu-based distribution dedicated to looking and feeling familiar to Windows users: Zorin OS.)

---

### Post by kc1di on 2014-07-23
you may want to try [Zorin ]("http://zorin-os.com/")- it's based on Ubuntu but can be taylored to look and feel almost exactly like windows 7 /xp  Happy hunting.
I personally would recomend Xubuntu to you.

---

### Post by mooreted on 2014-07-23
I have Xubuntu setup with Docky in panel mode. It looks pretty much like Windows 7. Of course, Linux will never be Windows, thank the gods.

---

### Post by etep513 on 2014-07-23
I read over all of the responses just now and I'm making a condensed list of all of them:

-Xubuntu, Kubuntu, Lubuntu
-Zorin
-Linux Mint

Someone mentioned Gnome but another person said that it is basically like Mac OSX, so I will keep it off the list for now.  Do all of the options listed above look like windows right at the moment of installation?  Or do I need to install extra packages to make them look more like Windows?

---

### Post by monkeybrain20122 on 2014-07-24
The person was talking about gnome flashback session. gnome shell is very much like Unity. To get it just 
```
sudo apt-get install gnome-session-flashback
```
Then log into it at the login screen and that's it.

I have no idea why you want you want your desktop to be ugly like XP. :)

---

### Post by Bucky Ball on 2014-07-24
Best to download the ISOs, burn them and try them out. Or you can run them as virtual machines in your current install. You can keep asking one way or the other, but you're never really going to know what suits until you try it yourself ...

A live boot will not change your setup in anyway. Start trying some ISOs/distros.

---

### Post by slooksterpsv on 2014-07-24
Xubuntu has 2 panels initially - one with shortcuts at the bottom, and the other with the Whisker Menu, notiification area, and open window lists. I just removed panel 2 and moved panel 1 to the bottom.
Kubuntu out of the box is similar to Windows
Lubuntu out of the box is similar to Windows
Zorin uses a package to make the menu for the start button look almost exactly like Windows 7's start menu
Linux Mint out of the box is similar to Windows

---

### Post by mastablasta on 2014-07-24
Kubuntu if you right click on K and select "classic menu" it is pretty much just like WinXP (the look&feel I mean). my 2 year old didn't have any issues switching between the desktops. Similarly Xubuntu and Lubuntu. Only Xubuntu in my opinion is easier to modify. the above mentioned panel is very easy to move, remove and change to your liking. everything is basically done with right clicking it and selecting properties. KDE has something similar but it's done in a bit different pehaps slightly unintuitive way for a windows user. they do have widgets and you can make it look really nice very fast. it's general look and feel is perhaps closer to Windows 7.

BOtxh Xubuntu and Kubuntu have plenty of different themes available... And Kubuntu (or rather it's KDE) is known to offer many options and have many things available via GUI.

---

### Post by Warren Hill on 2014-07-24
Most of the more popular Linux distributions can be tried without installing from a live USB or CD/DVD.

Certainly all the *buntu flavours and Mint

I suggest you try a few without installing first to see which you like once you have chosen a favourite install it for real.

I'd suggest Kubuntu with the "Classic" menu but see for yourself.  Only you can decide which is best for you.

---

### Post by buzzingrobot on 2014-07-24
The similarity to Windows is in their use of a panel and a menu and something analagous to a "start button" that displays the menu. Panels can be at the top, or bottom, or both. Theming will differ btween distributions and users. 

All work fine out of the box. Ability to alter the default look and feel varies, with KDE usually considered to have both the most configuration options and the most complex configuration options.  All are more configurable than Windows.

---

### Post by PondPuppy on 2014-07-24
I don't remember if this has already been mentioned --

Different windowing managers / desktops will place different demands on your hardware. If you have a modern processor with more than 1 GB of memory, the differences probably won't be noticeable. But if you run a netbook or an older computer with a relatively slow processor and less than 1 GB of memory, then be aware that the KDE and Unity desktops may feel a little laggy, and you'll have snappier performance from XFCE or LXDE. 

In other words, for a slower/older computer, choose Xubuntu or Lubuntu. Or Linux Mint. 

Zorin appears (from some sources) to take a bit more RAM than the above systems, though not as much as the heavyweight desktops.

But as I said, with any decent box or laptop you should be OK with any of the systems mentioned.

---

