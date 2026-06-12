---
title: "How to make Windows 7 more like Ubuntu"
date: 2010-01-11
forum: The Cafe
---

### Post by elmago79 on 2010-01-11
Maybe this is not the right place to ask this, but I guess since this is is a Windows question, this might be the better fit.

Long story short, I'm dual booting Windows 7 and Ubuntu because I need to use some Adobe proprietary software that works only on Windows. And I can't stand the way Windows 7 work. I specially miss multiple desktops, but I miss everything about Gnome.

So, I wondered if anyone has found a good tutorial or comment on how to make Windows 7 more like Ubuntu. Google has failed, since it insists I am looking for the opposite (Make Ubuntu work like Windows), and I have no interest in that.

---

### Post by TenPlus1 on 2010-01-11
Silly question but have you tried installing WINE and running your adobe software through that on your ubuntu setup...  Might just save you using Win7 altogether...

---

### Post by pwnst*r on 2010-01-11
Virtualbox + seamless mode.

---

### Post by alphaniner on 2010-01-11
Found [this old thread]("http://ubuntuforums.org/archive/index.php/t-157766.html"), looks like there may be some useful stuff there.

---

### Post by Shpongle on 2010-01-11
it can be done iv seen ubuntu themes done for windows around the net, but you have to hack the hell out of windows, in most cases you need to patch dll files , maybe try xp in virtual box as itll be lighter on resources , i also duel boot with win 7 and hate using it aswell , i know Tipped Out here on the forums can make  windows look pretty good,  (i said look ;-))maybe pm him

---

### Post by starcannon on 2010-01-11
> **pwnst*r said:**
> Virtualbox + seamless mode.
+1
This is a good option, put Windows on its own desktop on your Ubuntu install, need a windows app? just switch over to your windows desktop; all done doing that? go back to your ubuntu desktop with the flick of a mouse.

GL and HF

---

### Post by Falc7 on 2010-01-11
> **pwnst*r said:**
> Virtualbox + seamless mode.

This

---

### Post by elmago79 on 2010-01-12
Alphaniner, thanks for the link. KDE on Win seems like it will be a good choice in the future. There are a couple of things I might try (and made me realize I will miss some more things I take for granted).

To all of you that suggested Virtualbox + seamless mode, could you please enilghten me a bit more about that. I'm sort of afraid of Virtualbox, but it might just be what I need.

---

### Post by siimo on 2010-01-12
Does seamless mode support Aero Glass?

---

### Post by pwnst*r on 2010-01-12
> **elmago79 said:**
> Alphaniner, thanks for the link. KDE on Win seems like it will be a good choice in the future. There are a couple of things I might try (and made me realize I will miss some more things I take for granted).

To all of you that suggested Virtualbox + seamless mode, could you please enilghten me a bit more about that. I'm sort of afraid of Virtualbox, but it might just be what I need.

How much RAM do you have?  Vbox is pretty simple to implement.

> **siimo said:**
> Does seamless mode support Aero Glass?


With Vista or 7 as host, yes, but not sure with *nix being host.

---

### Post by k64 on 2010-01-12
> **siimo said:**
> Does seamless mode support Aero Glass?

Apparently not. I tried running Windows 7 in VirtualBox, to no avail with Aero. And Aero is more important in Windows 7 than ever, thanks to key Taskbar components requiring Aero to run (such as visual Taskbar previews).

---

### Post by Pasdar on 2010-01-12
> **elmago79 said:**
> Maybe this is not the right place to ask this, but I guess since this is is a Windows question, this might be the better fit.

Long story short, I'm dual booting Windows 7 and Ubuntu because I need to use some Adobe proprietary software that works only on Windows. And I can't stand the way Windows 7 work. I specially miss multiple desktops, but I miss everything about Gnome.

So, I wondered if anyone has found a good tutorial or comment on how to make Windows 7 more like Ubuntu. Google has failed, since it insists I am looking for the opposite (Make Ubuntu work like Windows), and I have no interest in that.
You could install KDE for windows: [http://windows.kde.org/](http://windows.kde.org/)

Or your could install virtualbox and use seamless mode, just install it from Ubuntu repository... in the virtualbox program install windows... you'll then be running windows on your linux machine.

Also many adobe programs work with use of the program wine.

---

### Post by elmago79 on 2010-01-13
Thanks for all your kind suggestions.

I have 3GB of RAM.

It seems that mounting my windows partition in virtualbox exceed my technical capabilites by far. Maybe it's time to look for a local IT guy. (Wine can't give me the programs I need, sadly, and since I use them for a living, I can't risk malfunctions.)

KDE for Win specifically states that it lacks many of the capabilities I would actually need, so I'll check back next year :)

---

### Post by k64 on 2010-01-13
> **elmago79 said:**
> Thanks for all your kind suggestions.

I have 3GB of RAM.

It seems that mounting my windows partition in virtualbox exceed my technical capabilites by far. Maybe it's time to look for a local IT guy. (Wine can't give me the programs I need, sadly, and since I use them for a living, I can't risk malfunctions.)

KDE for Win specifically states that it lacks many of the capabilities I would actually need, so I'll check back next year :)

VirtualBox runs Windows 7 from a loop device (drive image file), no mounting of partitions required.

---

### Post by Uncle Spellbinder on 2010-01-13
> **pwnst*r said:**
> Virtualbox + seamless mode.

+1

Wine has never worked as I'd like it to. sluggish, if it works at all. Virtualbox + seamless mode is the way to go.

---

### Post by nerdy_kid on 2010-01-13
> **DillByrne said:**
> it can be done iv seen ubuntu themes done for windows around the net, but you have to hack the hell out of windows, in most cases you need to patch dll files , maybe try xp in virtual box as itll be lighter on resources , i also duel boot with win 7 and hate using it aswell , i know Tipped Out here on the forums can make  windows look pretty good,  (i said look ;-))maybe pm him

i hacked win Vista themes quite easily.  Google "custom windows 7 themes" and you will get something.  You just have to replace 3 dlls and thats it.  I think it mightve caused a few BSOD in Vista, but then Vista gave me BSODs all the time so that it was hard to tell which ones were caused by "normal" operation or by the hack :D

---

