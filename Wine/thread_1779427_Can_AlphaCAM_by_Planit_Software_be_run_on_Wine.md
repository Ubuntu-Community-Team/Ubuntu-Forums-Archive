---
title: "Can AlphaCAM by Planit Software be run on Wine?"
date: 2011-06-10
forum: Wine
---

### Post by Cooper_81 on 2011-06-10
First off, hello all!  This is my first post, and I'm very new to the idea of running Wine and even Ubuntu, so be gentle.

I'm trying to figure out if I can run a program I use for work on Ubuntu/Wine called AlphaCAM made by Planit Software.
[http://www.alphacam.com/](http://www.alphacam.com/)
I'm running AlphaCAM Version 8 on Windows XP and Windows 7 if it matters.

I did do several searches (Google & Wine Application Database) on this topic and didn't find anything relevant.  Just a link to a similarly named webcam...
[http://ubuntuforums.org/showthread.php?t=1667770](http://ubuntuforums.org/showthread.php?t=1667770)

I don't have a preference on which versions of Ubuntu/Linux or Wine would be needed, I just want to get away from Windows completely if I can.

Thanks in advance, and I'm sure you'll all let me know if you need more information from me.

Cooper

---

### Post by bobwyajnr on 2011-06-12
Looking the through the applications system requirements, the phrase:
> USB 1.1 or 2.0 port for single user security key support
does not inspire confidence!

Wine will not even begin to support USB device pass-through till Wine 1.4.x (the next official stable branch).

Bob

---

### Post by Cooper_81 on 2011-06-12
Bob,

Thanks for looking into it.  If it helps, we have two licenses, one USB and one network.  I use the USB at home or when I travel, and the network key at work for convenience (it's nerve-wracking to always wonder where I put that over-priced USB key).  Here is a link I just found describing how to use a network key in Windows if it helps...  [http://www.alphacam.com/tips/updatenetwork](http://www.alphacam.com/tips/updatenetwork)

Any chance that would improve my odds of getting it to work?

Thanks,
Cooper

---

### Post by bobwyajnr on 2011-06-12
> **Cooper_81 said:**
> Bob,

Thanks for looking into it.  If it helps, we have two licenses, one USB and one network.  I use the USB at home or when I travel, and the network key at work for convenience (it's nerve-wracking to always wonder where I put that over-priced USB key).  Here is a link I just found describing how to use a network key in Windows if it helps...  [http://www.alphacam.com/tips/updatenetwork](http://www.alphacam.com/tips/updatenetwork)

Any chance that would improve my odds of getting it to work?

Thanks,
Cooper

Reading through that guide was giving me a headache! Perhaps they could follow a simpler authentication model!!

I would recommend initially trying the latest release Wine 1.3.21 (well it's actually Wine 1.3.22 - but it's not in the Ubuntu PPA yet). It is a officially it is a 'Beta' release - but you are probably going to be asked to try it (by the Wine developers) over at [WineHQ]("http://forum.winehq.org/") anyway!

[So pull Wine 1.3.21 (or 1.3.22 if available) from the LaunchPad PPA]("https://launchpad.net/~ubuntu-wine/+archive/ppa").

It's best to use the commandline for launching Wine applications. This is not to get your 'Geek On' - but simply because Wine prints debugging information to *stderr*/*stdout* streams (console output).

It would helpful to know what form the installer takes (i.e. download executable or CD/DVD)?

Assuming an downloaded executable installer...

Typically you would need to fire up Gnome terminal (/Konsole)
**cd** (change directory) to the path of the installer (e.g.):
```
cd ~/Downloads/
```
(that is your user account's Home/ Downloads folder. You will need to replace this if the installer is stored somewhere else)

[I]
Moving your terminal's current working directory to the installer directory ensures that any other executables/.dll's in that folder will be in the 'path' for the installer (i.e. so the Alphacam installer can 'see' them).[/I]

Then execute the installer using the Wine wrapper:
```
wine Setup.exe
```
(replacing the executable with the name of the actual name of the installer)

I am assuming that the installer will not work (optimistic :popcorn:) so when it doesn't could you post the console output here with <CODE> tags!!

Bob

---

### Post by Cooper_81 on 2011-06-12
Alright, something to try!  Unfortunately AlphaCAM installs via a DVD, and it's in my office, which I won't get to until Wednesday, and I'll be slammed seeing as I'll have missed Mon & Tue due to business travel.  Not to mention I'm replacing my HDD with a SSD Wed, but I'll do my best to give this a shot Wed.

If I can't get to it, can I test any of this on my laptop (USB key) even tho I won't have a network key unless I'm at work?  I'm familiar with the errors it gives me when I don't have the proper license referenced.  If I get that far I should know that it's likely to work with a network key, right?

Thanks again Bob!  I'll let you know if (when) I get confused on the Ubuntu/Wine side of things, and post back with my results.

---

### Post by bobwyajnr on 2011-06-12
> **Cooper_81 said:**
> Alright, something to try!  Unfortunately AlphaCAM installs via a DVD, and it's in my office, which I won't get to until Wednesday, and I'll be slammed seeing as I'll have missed Mon & Tue due to business travel.  Not to mention I'm replacing my HDD with a SSD Wed, but I'll do my best to give this a shot Wed.

If I can't get to it, can I test any of this on my laptop (USB key) even tho I won't have a network key unless I'm at work?  I'm familiar with the errors it gives me when I don't have the proper license referenced.  If I get that far I should know that it's likely to work with a network key, right?

Thanks again Bob!  I'll let you know if (when) I get confused on the Ubuntu/Wine side of things, and post back with my results.

The DVD installer shouldn't be an issue (theoretically). Hopefully there isn't any copy protection used on this...

The lack of a USB driver will give you the normal Windows errors - yes. Whether or not it works with the network key is anyones guess. You have to appreciate that Wine implements **part** of the Windows API. It doesn't do applications/code based on .Net well for example.

Happy travelling :popcorn:

Bob

---

