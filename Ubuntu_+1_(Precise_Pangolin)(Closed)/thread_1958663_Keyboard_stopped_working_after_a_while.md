---
title: "Keyboard stopped working after a while"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by odd on 2012-04-14
It occures randomly once in a few days (I suspend my laptop most of the time when I go to sleep). I type something in firefox and suddenly keyboard stops working:

# env/hw:
- Lenovo X200t TabletPC
- Ubuntu 12.04b2 updated regurarly
- Gnome-shell

# What's going on when this bug/event occurs:
- no letters are typed,
- no xev output during the event
- I hear {doing}sound (same as you can hear when hitting backspace in terminal when there's nothing delete:)) on every keypress
- syslog, xorg.log don't say anything during the event
! mouse/touchscreen is working so I manage

# solution/workaround:
- I click on a on-screen-keyboard CTL, ALT and F1 to go to console#1, where keyboard works
- I go back to X (CTL+ALT+F7) and keyboard works fine again.
(still no clue in syslog or xorg log)
(side-bug, touchscreen going back to relative mode while cycling from CTL+ALT+F1 back to X server, which is wrong but probably unrelated)

Anyone has this issue? 

P.S.
I'm kind'a new on bug reporting - is there a way to submit a bug report withhout knowing the package responsible/involved in the bug?

---

### Post by isene on 2012-04-24
I Googled this to see if anyone had the same issue (as I was suspecting my hardware was failing), but: 

I have the same issue on my Lenovo X200 after upgrading to 12.04. It is random and not reproducible AFAIK. It so happens that the keyboard does register the keys if I press them very hard (a seriously weird issue this is). If I kill X (or reboot) and login again, then all is fine.

Also; When pressing the keys real hard to get out of X and into console mode, the keys work just fine. Back into X they are all screwy again.

UPDATE: Tried some more debugging - issue remains (randomly - not able to produce it at will). It seems that the initial keypress is disregarded, but key registers after the repeat-interval and then repeats as usual - i.e. I press a key and wait and the key registers and repeats just as it would before the bug appears except the first keypress is not registered.

---

