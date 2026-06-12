---
title: "What's required to boot 17.10 on Wayland?"
date: 2017-08-31
forum: Ubuntu Development Version
---

### Post by Roasted on 2017-08-31
Hi friends. I'm tinkering with 17.10 and trying to get a feel for everything in development. I spun up 17.10 in VirtualBox and was surprised to see "Ubuntu" (suggesting Wayland, as the other option is Ubuntu on Xorg) was defaulted and already selected. But after I log in and run loginctl show-session 2 -p Type, it shows X11.

No big deal, it's VirtualBox anyway, maybe it's a fault with Wayland on VirtualBox. Okay fine, so I spun up a native 17.10 install on a spare laptop -- but the same thing happens.

The laptop in question is a 2nd gen i5 laptop. No Nvidia or anything else, all Intel.

Is anybody else seeing this? Basically, Ubuntu (Wayland) selected, I log in, things seem fine, but here I'm just on X11 the entire time. Is this option not actually enabled yet or is something else backfiring?

Thanks for any insight!

---

### Post by mc4man on 2017-09-01
Your being affected by 2 parts of a longstanding & current[ bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157").
1. All fresh boots will show "Ubuntu"
2. The 1st. log in from a new install will be xorg

So boot up > at login switch from ubuntu to the xorg one, then back to ubuntu. You'll log into wayland
(- if you then log out the login screen would be accurate. On a reboot it will say ubuntu (1), your session should be whatever it was when you shutdown.

Also to note: atm live sessions are always xorg

---

### Post by mc4man on 2017-09-06
> **mc4man said:**
> Your being affected by 2 parts of a longstanding & current[ bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157").
1. All fresh boots will show "Ubuntu"
2. The 1st. log in from a new install will be xorg

So boot up > at login switch from ubuntu to the xorg one, then back to ubuntu. You'll log into wayland
(- if you then log out the login screen would be accurate. On a reboot it will say ubuntu (1), your session should be whatever it was when you shutdown.

Also to note: atm live sessions are always xorg

As of todays image there is one slight change to above - 
The login greeter will always say "ubuntu" no matter what. This extends to log out/ins now as well.

---

### Post by lammert-nijhof on 2017-09-11
By default Ubuntu 17.10 selected to log-in with Wayland. If I have 3D enabled in Virtualbox, the system directly returns to the login screen. If I want to use Wayland I have to disable the 3D acceleration for the Ubuntu 17.10 virtual machine. 
If I select the Ubuntu X-org option it works fine and 3D works really good even with the firefox beta 56.0b3 and its 3D acceleration support. It easily beats my Ubuntu 16.04 VM, that rewrites my typing after half a second for the second time to the screen, while I try to type the next word. I consider to use Ubuntu 17.10 Xorg as my main VM for banking etc. after October till the next 18.04 LTS.

---

### Post by mc4man on 2017-09-11
> **lammert-nijhof said:**
> By default Ubuntu 17.10 selected to log-in with Wayland.
Are you stating that _1st. login after install _gave you a wayland session or that it showed you 1st. session of "ubuntu" (wayland
Can be confirmed by results of 
```
echo $DESKTOP_SESSION
```
```
env |grep xorg
```

---

