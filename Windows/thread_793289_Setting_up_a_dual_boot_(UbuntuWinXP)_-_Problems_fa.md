---
title: "Setting up a dual boot (Ubuntu/WinXP) - Problems faced"
date: 2008-05-13
forum: Windows
---

### Post by shinka on 2008-05-13
Hi there.

Basically, I left XP, came across to Ubuntu, and now need to get XP back so I can run MMORPGs.

A few problems though:
1) I repartitioned the drive using Gpart, then used my XP install disc, installed it on the partition I had made for it. However, XP then wouldn't let me boot up ubuntu, which annoyed me no end. It seemed to have hidden the ubuntu partition.
2) When I got onto XP, I realized that my wireless card was not recognized. On ubuntu, it automatically works. On XP, it doesn't...
So is there a way I can find out what wireless card model I have (its a laptop and the card is embedded) using the terminal? This way, I could probably download the drivers for XP for that card and install the card.


Really though, the dual booting is the most important bit to me. Worst comes to the worst, I can plug into the router, but that means being downstairs which I don't like, because the aircon is broken :p

Thank you loads for the help!

Using an IBM thinkpad. -_-

---

### Post by LaRoza on 2008-05-13
> **shinka said:**
> Hi there.

Basically, I left XP, came across to Ubuntu, and now need to get XP back so I can run MMORPGs.

A few problems though:
1) I repartitioned the drive using Gpart, then used my XP install disc, installed it on the partition I had made for it. However, XP then wouldn't let me boot up ubuntu, which annoyed me no end. It seemed to have hidden the ubuntu partition.
2) When I got onto XP, I realized that my wireless card was not recognized. On ubuntu, it automatically works. On XP, it doesn't...
So is there a way I can find out what wireless card model I have (its a laptop and the card is embedded) using the terminal? This way, I could probably download the drivers for XP for that card and install the card.

Using an IBM thinkpad. -_-

What Thinkpad do you have? You can look up the specs and find the driver for it.

---

### Post by shinka on 2008-05-13
Hi again.

I checked up before. However, this is a refurbed laptop, so it might be wrong. I *think* it is an intel one, but I don't know which. I only need the XP drivers though, because ubuntu handles it automatically.

When I got the laptop, the wireless icon was in the systray, but obviously it has to be enabled by a driver or program, which isn't enabled or installed by xp. (Another problem may be that it is an IBM thinkpad, but I'm using a compaq disk to install XP, because I never got a cd with the laptop. Damn XP just is full of trouble lol). Due to this its gunna be manual work to get the wireless working again.

Anyway... In other news, I found a great tutorial to dual boot, which I'm using right now, so sorry if I'm a bit slow in replying :p


Thanks for the help!

Joe

---

### Post by smoker on 2008-05-13
enter the laptop product number in the link below, or use the select your product menu and you should be taken to the download site for your wireless drivers:
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=HOME-LENOVO#rdt](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=HOME-LENOVO#rdt)

---

### Post by Living2007 on 2008-05-13
Regarding your "dual boot" problem. Windows has taken over the start-up, so Grub can't load.

What I would do is back-up my Ubuntu data onto the Windows Partion, reinstall Ubuntu, then the card (unless it has already been picked up), and collect your data.

---

### Post by shinka on 2008-05-14
Hi there again.

OK, now I followed a tutorial for dual booting XP.
Everything went fine, until I got to the part of loading the windows partition from grub (pressing esc when grub loads). I then chose Windows XP from the list, and it decided to error on me, telling me it doesn't understand the command.

Could this be the problem? I put it into /boot/grub/menu.lst or something similar.
```

Title   Windows XP
root    (hd0,1)
makeactive
chainloader +1
```

So, yeah, it basically won't boot windows. The ubuntu patition runs just dandy though.

Thanks for the tip about the driver download, that part worked :) Cheers.

---

### Post by Living2007 on 2008-05-14
It maybe well the problem, if Ubuntu loads well, then the Grub Menu list needs to be edited

---

### Post by shinka on 2008-05-14
This is the /boot/grub/menu.lst file isn't it?

I think it said Error 11 on the grub load when I tried to boot windows.

When I get home I will post it in this thread (about 2 hours from now).

A thought I had is this:
I have all my files backed up, so would it be easier for me to reformat the disk and install XP, then install ubuntu afterwards?
I've heard it is easier to set up a dual-boot from starting on XP.

Thanks for the help!

---

### Post by smoker on 2008-05-14
hi, i don't dual boot anymore, so not so bright on grub issues, though when i did i used this to sort out issues. very handy to have close by:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

best of luck

---

### Post by meierfra. on 2008-05-14
try

[COLOR="Red"]t[/COLOR]itle   Windows XP
root    (hd0,1)
makeactive
chainloader +1



If that does not work, post the output of

```
sudo fdisk -l
```
( l is a lower case L)

---

### Post by Jiraya on 2008-05-17
> **meierfra. said:**
> try

[COLOR="Red"]t[/COLOR]itle   Windows XP
root    (hd0,1)
makeactive
chainloader +1



If that does not work, post the output of

```
sudo fdisk -l
```
( l is a lower case L)

Very smart to say that. Many people type -1, instead. Then try -l when they get the error.

[Linux Archive]("http://www.linux-archive.org")

---

