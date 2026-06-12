---
title: "VLC replacement that dos *NOT* use QT"
date: 2008-10-09
forum: The Cafe
---

### Post by hessiess on 2008-10-09
I use Arch Linux, and try to keep it as minimal as possible, however with VLC switching from WX to QT, the QT libs were installed. I don't want QT installed for the sake of one program, so are there any alternatives that use GTK and can 'play anything'(including DVD's), like VLC can.

thanks.

---

### Post by voteforpedro36 on 2008-10-09
MPlayer?

---

### Post by bash on 2008-10-09
And you could even use GNOME Mplayer if you want a GTK frontend for Mplayer ...

---

### Post by steeleyuk on 2008-10-09
Totem for me plays pretty much anything. Any specific file types that you're planning on using?

---

### Post by RiceMonster on 2008-10-09
> **bash said:**
> And you could even use GNOME Mplayer if you want a GTK frontend for Mplayer ...

This. I much prefer GNOME-Mplayer (or even just mplayer, but not gmplayer) to VLC. Don't be fooled either, it's just a very nice GTK frontend; it doesn't pull in tons of GNOME deps.

---

### Post by TravisNewman on 2008-10-09
I think the OP wants something that you don't have to fuss over codecs for. 

I know of nothing like VLC that has everything necessary in a nice, neat package. It's truly amazing.

---

### Post by yabbadabbadont on 2008-10-09
No one has mentioned xine yet.

---

### Post by bash on 2008-10-09
> **panickedthumb said:**
> I think the OP wants something that you don't have to fuss over codecs for. 

I know of nothing like VLC that has everything necessary in a nice, neat package. It's truly amazing.

mplayer plays basically everything. I thought both mplayer and vlc use ffmeg.

---

### Post by koenn on 2008-10-09
vlc-nox
it's all the functionality of vlc, without the GUI.

---

### Post by hessiess on 2008-10-09
> **steeleyuk said:**
> Totem for me plays pretty much anything. Any specific file types that you're planning on using?

no formats specificly, just whatever I come across on the web, which can be practically anything.

GNOME-mplayer seams to be adequate, only time will tell if it has the 'play anything' capability that VLC comes with.

---

### Post by myusername on 2008-10-09
totem-xine is great

---

### Post by billgoldberg on 2008-10-09
> **hessiess said:**
> I use Arch Linux, and try to keep it as minimal as possible, however with VLC switching from WX to QT, the QT libs were installed. I don't want QT installed for the sake of one program, so are there any alternatives that use GTK and can 'play anything'(including DVD's), like VLC can.

thanks.

Totem.

It plays everything for me.

---

### Post by ice60 on 2008-10-09
i've used gnome-mplayer as my only player for at least a year and it works almost perfectly, i sometimes use mplayer when the audio and picture are out of sync to re-sync them; to do that i run mplayer from the cli i.e. -
**mplayer video.avi**
(it doesn't seem to work if you launch mplayer, then open the video) then to sync the video you use shift-+ and -

edit: actually with an avi file you might need the -idx option, it tells you that in the terminal if you forget.

---

### Post by Trail on 2008-10-10
MPlayer > VLC

I use SMplayer, but you don't want that, so I can't recommend to you a good front-end. I'm sure there must be one for GNOME though.

---

### Post by samjh on 2008-10-10
> **hessiess said:**
> are there any alternatives that use GTK and can 'play anything'(including DVD's), like VLC can.No, there aren't.

In my two years of struggling with codecs and DVDs on Linux, nothing beats VLC.  I've never had problems with any media playback using VLC.  The Mozilla plugin could be better, but that's only a minor niggle.

My second-favourite is MPlayer, but it doesn't do DVD menus properly, and some media files play with out-of-sync audio (no problems with VLC).

As for Totem players, Totem-Gstreamer doesn't track some media files properly, and sometimes has problems selecting the correct locale for DVD playback.  Totem-xine has audio sync issues on some media files.  (Again, no problems with VLC.)

The 10-odd megabytes of files needed for basic Qt runtime libraries is hardly a dint when you consider than most Linux installations weigh at least 1.5 Gigabytes.  Even if you install every Qt runtime file (which is not necessary for most people), it's only around 30 megabytes.

---

### Post by Heinzelotto on 2008-10-10
ok, forget what i was saying...

---

### Post by LaRoza on 2008-10-10
Why not use VLC? Unless you are restricted by hard drive space, or the minor delay in startup is a problem, it is rather silly to be consistant for nothing. "A foolish consistency is the hobgoblin of little minds"

I use xmonad, Opera, VLC, Thunar, and many terminal apps. I use the best of free software, on a minimal setup, without working about being consistant for the sake of it. Yes, I have many libraries installed that I do not use (mostly the GNOME and KDE ones, as I have GNOME and KDE installed for testing, I don't use them much). My hard disk can take it.

---

