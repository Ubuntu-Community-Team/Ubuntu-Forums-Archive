---
title: "Ubuntu time server?"
date: 2005-01-09
forum: The Cafe
---

### Post by mark on 2005-01-09
Anybody else having problems connecting to the Ubuntu time server [ntp.ubuntulinux.org](ntp.ubuntulinux.org) ?  I've been doing a lot of rebooting (new router) and I keep getting FAILED when the system tries to sync with this server...

---

### Post by Arbite on 2005-01-09
Nope sorry,, works great here,

What port does ntp operate on?

Have u giveing acces to that port in your router/firewall

---

### Post by tiiim on 2005-01-09
[QUOTE=Arbite]Nope sorry,, works great here,

What port does ntp operate on?

Have u giveing acces to that port in your router/firewall[/QUOTE]
 for me sometimes it work sometimes it fails. Home network it fails, uni its fine but then today it fail. It will be a network problem deff.

---

### Post by hashimoto on 2005-01-09
After updating to Hoary it has failed every time for me to.

Hashimoto

---

### Post by Quest-Master on 2005-01-09
Stopped working for me yesterday. :\

---

### Post by jeremy on 2005-01-10
works fine for me, Warty, router (no special port opened).

---

### Post by zenwhen on 2005-01-10
Stopped working for me a couple days ago. I am using Warty.

---

### Post by rbrimhall on 2005-01-10
has never worked for me... always fails...

---

### Post by jdodson on 2005-01-10
works fine for me.

---

### Post by Cygnia on 2005-01-10
I rebooted last night after the latest kernel update and the time server connection failed. It was about 1 AM Pacific.

---

### Post by wallijonn on 2005-01-10
I just disabled it from the boot process. It was always failing for me. 

[http://www.ubuntuforums.org/showthread.php?t=1028&highlight=ntp.ubuntulinux.org](http://www.ubuntuforums.org/showthread.php?t=1028&highlight=ntp.ubuntulinux.org)

---

### Post by wallijonn on 2005-01-21
How does one install ntp support? Because I use Windows. also, whenever I boot into Ubuntu the time changes to UTC even though I have it set to local time. I have since re-enabled ntp but now want to select a different internet time server. how?

---

### Post by mark on 2005-01-21
[QUOTE=wallijonn]How does one install ntp support? Because I use Windows. also, whenever I boot into Ubuntu the time changes to UTC even though I have it set to local time. I have since re-enabled ntp but now want to select a different internet time server. how?[/QUOTE]
Either through *apt* or *synaptic*, install *ntp-server* and/or *ntp-simple*  (I can't remember the order I did it in, but I think one requires the other).  Then invoke *Time and Date*, check *Synchronize clock with Internet servers:* and select your server from the drop-down.

---

