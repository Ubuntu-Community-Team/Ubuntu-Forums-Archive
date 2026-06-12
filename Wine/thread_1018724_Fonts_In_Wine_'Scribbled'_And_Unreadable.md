---
title: "Fonts In Wine 'Scribbled' And Unreadable"
date: 2008-12-22
forum: Wine
---

### Post by be_placid on 2008-12-22
Hi all,

I'm by no means a Linux newbie, but I'm stumped at this one.

I've recently done a fresh install of Xubuntu 8.10 and installed wine via apt-get. Unfortunately I'm getting the following issue with fonts when running *anything* in Wine - from custom apps to installers;

[IMG]http://beplacid.net/images/misc/wine-bad-fonts.png[/IMG]

I've installed the following Windows fonts in "~/.wine/drive_c/windows/Fonts/":
[LIST]
[*]Arialbd.TTF
[*]AriBlk.TTF
[*]courbi.ttf
[*]Arialbi.TTF
[*]Comicbd.TTF
[*]couri.ttf
[*]Timesbi.TTF
[*]trebucit.ttf
[*]Verdana.TTF
[*]Ariali.TTF
[*]Comic.TTF
[*]cour.ttf
[*]Georgiaz.TTF
[*]Timesi.TTF
[*]trebuc.ttf
[*]Verdanaz.TTF
[*]Arial.TTF
[*]courbd.ttf
[*]Georgiab.TTF
[*]Impact.TTF
[*]Times.TTF
[*]Verdanab.TTF
[*]Webdings.TTF
[/LIST]

and I've also tried the same applications with a fresh ~/.wine directory. Unfortunately, nothing's helped.

Further system specs:
`uname -a`: Linux fatcat 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
`cat /etc/debian_version`: lenny/sid (strange this, considering I'm running Xubuntu 8.10...)

Anyone have any ideas?

Cheers!

---

### Post by OrbJinzo on 2008-12-22
heh ubuntu is a debian fork...

and try installing the core fonts package

---

### Post by be_placid on 2008-12-23
> **OrbJinzo said:**
> heh ubuntu is a debian fork...

and try installing the core fonts package

Yeah I'm aware it's a fork of Debian, but other Ubuntus have had that file set specifically.

I installed mstcorefonts from apt, but that hasn't made one bit of difference. Any further ideas?

---

### Post by vpappas on 2008-12-23
Same problem here when using the official NVidia driver (ver 96.43.09-0ubuntu1). (I don't know if that is the case with you .. :) )

Anyway, you can try a workaround found here [https://bugs.launchpad.net/bugs/300476]("https://bugs.launchpad.net/bugs/300476")

Create a file named 'settings.txt' with the following contents :

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

and then run 'regedit settings.txt'.

I hope it helps.

---

### Post by macson_g on 2008-12-29
Yup, it helps. Thanks!

---

### Post by be_placid on 2008-12-29
> **vpappas said:**
> Same problem here when using the official NVidia driver (ver 96.43.09-0ubuntu1). (I don't know if that is the case with you .. :) )

Anyway, you can try a workaround found here [https://bugs.launchpad.net/bugs/300476]("https://bugs.launchpad.net/bugs/300476")

Create a file named 'settings.txt' with the following contents :

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

and then run 'regedit settings.txt'.

I hope it helps.

That worked, thanks!

---

