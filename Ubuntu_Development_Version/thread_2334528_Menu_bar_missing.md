---
title: "Menu bar missing"
date: 2016-08-20
forum: Ubuntu Development Version
---

### Post by Cerveira on 2016-08-20
Hi,

I'm testing Ubuntu Yakkety Yak (I now that is not a final release) and since the last upgrade, when I login in Xubuntu menu bar is missing. Searched in a few foruns and the tip was to right click anywhere in the desktop to see menu. But even that doesn't work.

I've temporarily solved it by changing the session from "Xubuntu" to "XFCE4" in the login menu. Doing that I have all the menu's in my account back. Before that I login in a terminal (with ctrl+alt+1) and reinstalled xubuntu-desktop and xubuntu-default-settings but did not worked.

Any suggestions?

---

### Post by howefield on 2016-08-20
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by ventrical on 2016-08-20
> **Cerveira said:**
> Hi,

I'm testing Ubuntu Yakkety Yak (I now that is not a final release) and since the last upgrade, when I login in Xubuntu menu bar is missing. Searched in a few foruns and the tip was to right click anywhere in the desktop to see menu. But even that doesn't work.

I've temporarily solved it by changing the session from "Xubuntu" to "XFCE4" in the login menu. Doing that I have all the menu's in my account back. Before that I login in a terminal (with ctrl+alt+1) and reinstalled xubuntu-desktop and xubuntu-default-settings but did not worked.

Any suggestions?

Do you have proposed repo enabled ?

---

### Post by Cerveira on 2016-08-21
> **ventrical said:**
> Do you have proposed repo enabled ?

I don't. Should I?

---

### Post by mc4man on 2016-08-21
Maybe this - 
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615341](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615341)
if so then systemd (231-4ubuntu1) should fix

---

### Post by Cerveira on 2016-08-23
> **ventrical said:**
> Do you have proposed repo enabled ?

Should I have proposed rep enable?

> **mc4man said:**
> Maybe this - 
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615341](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1615341)
if so then systemd (231-4ubuntu1) should fix

Solved with last update!
Tks everyone!

---

### Post by jbicha on 2016-08-24
> **Cerveira said:**
> Should I have proposed rep enable?


[No]("http://askubuntu.com/q/785414/1579")

---

