---
title: "How to uninstall a program under wine"
date: 2010-11-10
forum: Wine
---

### Post by jhunternissen on 2010-11-10
I need to uninstall and re install my trading platform, FXCM MT4 which operates in wine.  I went to Accessories, terminal, etc.  entered, "wine uninstall" and its rejected.  Yesterday I entered the same routine, it displayed the program and a uninstall box and froze...  what is going on, please?  Jerry

---

### Post by sikander3786 on 2010-11-10
Go to Applications > Wine > Uninstall Wine Software. If your program is listed there, you can remove it from easily.

---

### Post by jhunternissen on 2010-11-10
> **sikander3786 said:**
> Go to Applications > Wine > Uninstall Wine Software. If your program is listed there, you can remove it from easily.
will it uninstall wine too?

---

### Post by I'mGeorge on 2010-11-10
in a terminal try wine control and see if a window with an Add/remove programs option pops out

---

### Post by sikander3786 on 2010-11-10
> **jhunternissen said:**
> will it uninstall wine too?
It won't uninstall Wine itself.

If you want to remove Wine as well, go to Software Center, search for wine and click remove.

Or from terminal,

```
sudo apt-get remove wine
```

---

### Post by jhunternissen on 2010-11-10
By jingo, I've tried them all...........  I get that dratted Uninstall box with the kinky arrows up and down... and an opaque box with no command.... Once it showed a "next" which when clicked upon.... did precisely nothing.  I know that I am stupid, but it seems to me that linux and ubuntu should engage Steve Jobs to humanize it.... less "geekology"  Sorry, guys, that's just my take.  For sure Microsoft needs to be taken out!

---

### Post by sikander3786 on 2010-11-10
If you've no other programs installed inside Wine, I would go for a complete removal of wine by

```
sudo apt-get remove --purge wine
```

Then from the /home folder, delete the hidden (press Ctrl + H to see the hidden files) .wine folder and reinstall wine by,

```
sudo apt-get install wine
```

---

### Post by I'mGeorge on 2010-11-10
well you can always go to /home/username/.wine/drive_c/Program\ Files and look for the application you wanna uninstall in there. See if the app has an uninstall and if it does use it, it should work too. Or if it doesn't just delete it, but the command 

```

wine control

```

should had worked

---

### Post by jhunternissen on 2010-11-10
what "should" work, doesnt.  At this very instant, I have the program in the box, clicked on "modify/remove, and nothing happens!  I thought linux was a reliable system.  the uninstall box with the kinky up/down arrows freezes the computer.....

---

### Post by sikander3786 on 2010-11-10
> **jhunternissen said:**
> what "should" work, doesnt.  At this very instant, I have the program in the box, clicked on "modify/remove, and nothing happens!  I thought linux was a reliable system.  the uninstall box with the kinky up/down arrows freezes the computer.....
Linux itself is very stable. Wine is a compatibility layer that allowS you run the programs that are not intended for Linux. With some programs, I got this problem even in a native Windows system, Wine is just a layer. Why not hope the Windows program behave the same or even worse in wine? :-)

---

### Post by jhunternissen on 2010-11-10
> **sikander3786 said:**
> Linux itself is very stable. Wine is a compatibility layer that allowS you run the programs that are not intended for Linux. With some programs, I got this problem even in a native Windows system, Wine is just a layer. Why not hope the Windows program behave the same or even worse in wine? :-)
hey hey...........  :-)

---

### Post by jhunternissen on 2010-11-10
My quandry now is - if I remove wine in order to uninstall MT4, then I will no doubt have great problems reinstalling wine and the MT4.  These are not plug and play deals.  anyway I go I am screwed. :-(

---

### Post by I'mGeorge on 2010-11-10
well I don't know what's MT4 but if you wanna reinstall wine you should consider adding [COLOR="Navy"][[COLOR="DarkRed"]this[/COLOR]]("http://www.winehq.org/download/deb")[/COLOR] to your repositories if you don't have it already so you would have the latest wine version available.

---

