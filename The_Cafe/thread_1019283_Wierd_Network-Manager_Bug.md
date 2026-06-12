---
title: "Wierd Network-Manager Bug?"
date: 2008-12-23
forum: The Cafe
---

### Post by kevin11951 on 2008-12-23
Ever seen this before? :confused:

---

### Post by smartboyathome on 2008-12-23
I have. Happens to me after I ctrl+alt+backspace x or log out/log in.

---

### Post by kevin11951 on 2008-12-23
> **smartboyathome said:**
> I have. Happens to me after I ctrl+alt+backspace x or log out/log in.

has it been reported yet?

---

### Post by smartboyathome on 2008-12-23
> **kevin11951 said:**
> has it been reported yet?

I dunno, I abandoned NetworkManager for WICD because my wireless card has a better connection with it, and didn't look into it.

---

### Post by FuturePilot on 2008-12-23
Yep, I've seen that before too. Usually happens after recompiling the Virtualbox kernel module. The script seems to do a udev restart and it causes duplicate entries in network-manager.

---

### Post by doorknob60 on 2008-12-23
Never seen it, iwconfig+dhclient FTW.

---

### Post by Polygon on 2008-12-23
ive also gotten that as well. it usually happens when network manager gets updated while its in use (read: all the time) and then after the upgrade ubuntu tells me to restart anyway and it gets fixed.

either that or 'killall nm-applet' and then restarting it again fixes it

---

### Post by klange on 2008-12-23
> **smartboyathome said:**
> I dunno, I abandoned NetworkManager for WICD because my wireless card has a better connection with it, and didn't look into it.

I'm not sure how that's possible considering what NM does with most wireless cards... Meh.

I used to get this in the early days of NM 0.7 testing.

Can't say I know anything about fixing it, though.

(Real men just use [FONT="monospace"]iwconfig[/FONT] and [FONT="monospace"]route[/FONT] manually, and further, they *guess* at the network names)

---

