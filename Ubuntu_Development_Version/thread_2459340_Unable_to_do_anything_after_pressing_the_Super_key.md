---
title: "Unable to do anything after pressing the Super key"
date: 2021-03-16
forum: Ubuntu Development Version
---

### Post by t9yz3w4ogbvn7w on 2021-03-16
I'm not sure of the terminology, but when pressing the super key, the various workspace windows spread out in front of me and I can mouse over them and get the little X to close icon popup on each, etc, but I can't actually focus on any of the windows. 

Pressing the windows key again doesn't do it, clicking on a window with the mouse doesn't do it, etc. It's stuck in the "spread" view and I am unable to exit out of it.

This persisted after 2 reinstalls. Is there a secret to exiting out of it, or is this a bug?

---

### Post by corradoventu on 2021-03-18
Testing your problem i was able to reproduce it just once, will retry..
filed a bug: [https://bugs.launchpad.net/ubuntu/+bug/1920121](https://bugs.launchpad.net/ubuntu/+bug/1920121) if you have the same problem and an account on launchpad please subscribe.

---

### Post by t9yz3w4ogbvn7w on 2021-03-19
This happens 100% of the time for me. So if I accidentally press super, I can't use the system at all anymore aside from messing around in the spread out view. I noticed there is a bug tracked where open windows overlap over the finder search results. Maybe once they fix that, it will fix this issue.

---

### Post by corradoventu on 2021-03-19
They are few bugs about display:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1920121](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1920121)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1917939](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1917939)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1919476](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1919476)
[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1918874](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1918874)
but if you report the problem here and not on launchpad your comments are useless.

---

### Post by funicorn on 2021-03-27
I think similar thing happened in several cases when I pressed the super key and typed in the dash box too quickly, after which the window previews stayed there like for ever until I restarted the gnome-terminal.. 

In fact I noticed the dash box didn't apepar immediately as expected in those cases - not sure if that's the reason though. 

I'm using fcitx instead of ibus IM.

The problem began to show since I upgraded to Ubunt 21.04 [dev version].

> **t9yz3w4ogbvn7w said:**
> I'm not sure of the terminology, but when pressing the super key, the various workspace windows spread out in front of me and I can mouse over them and get the little X to close icon popup on each, etc, but I can't actually focus on any of the windows. 

Pressing the windows key again doesn't do it, clicking on a window with the mouse doesn't do it, etc. It's stuck in the "spread" view and I am unable to exit out of it.

This persisted after 2 reinstalls. Is there a secret to exiting out of it, or is this a bug?

---

### Post by Bukunut on 2021-04-07
I am probably stating the obvious here, but I am having the same problem 100% in Wayland login but logging into X display server the problem is not there at all (not so far anyhow)

---

