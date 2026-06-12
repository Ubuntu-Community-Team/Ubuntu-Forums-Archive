---
title: "Unity Home Launcher Misbehavior"
date: 2011-11-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-01
My Home launcher is working differently since last updates. It works for one time and stops working. 

First time I left-click it, it will open a Nautilus at $HOME normally. If I close this Nautilus window and left-click the launcher again, nothing happens. Middle Clicking works always.

The quicklist items under this launcher work OK thou. Other launchers seem to work fine.

Anyone confirms?

Effenberg

---

### Post by ventrical on 2011-11-01
Works normal here effen but I remember during alpha testing(of Oneiric) . It happened a lot.

---

### Post by effenberg0x0 on 2011-11-02
Fixed by commenting out the "OnlyShowIn=GNOME;Unity;" line. Now it does launch a Nautilus Window every time I press it. It is a known bug to which there are reports.

---

### Post by mc4man on 2011-11-02
> **effenberg0x0 said:**
> Fixed by commenting out the "OnlyShowIn=GNOME;Unity;" line. Now it does launch a Nautilus Window every time I press it. It is a known bug to which there are reports.
That line, when in a custom .desktop, will also have the effect of having a 2nd icon open on the launcher that is the 'controlling' icon
(affects more than just nautilus

Typically this would happen when people copy a .desktop from /usr to ~/ for the purposes of modding (adding quicklists

So highly recommend to always remove from any custom .desktop
(causes me no issue when in the orig. installed .desktop in /usr

---

### Post by effenberg0x0 on 2011-11-02
> **mc4man said:**
> That line, when in a custom .desktop, will also have the effect of having a 2nd icon open on the launcher that is the 'controlling' icon
(affects more than just nautilus

Typically this would happen when people copy a .desktop from /usr to ~/ for the purposes of modding (adding quicklists

So highly recommend to always remove from any custom .desktop
(causes me no issue when in the orig. installed .desktop in /usr

Ah, I see, I probably caused it when I was working on the nautilus quicklist, which has more than 20 options. I've played with for a long while and probably copied it from /usr/share/apps to ~/.local/... at some point. It's clear now. Thanks for the excellent info.

---

