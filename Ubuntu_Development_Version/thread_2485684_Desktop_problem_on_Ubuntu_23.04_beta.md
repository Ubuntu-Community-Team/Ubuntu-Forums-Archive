---
title: "Desktop problem on Ubuntu 23.04 beta"
date: 2023-04-05
forum: Ubuntu Development Version
---

### Post by mcellius on 2023-04-05
I installed Ubuntu 23.04 on two different computers, one with an Intel CPU and the other with an AMD CPU.  Both were upgradess from Ubuntu 22.10 (Kinetic) by running do-release-upgrade -d so they weren't fresh installs.  Both have Nvidia graphics, and both run xorg rather than Wayland.  One is a laptop and the other a desktop computer, and they're having the same two problems:

1.  I have Gnome Tweaks installed and have used it to switch the windows control buttons to the left side of windows.  This works for Gnome applications, but for third-party applications - Firefox, Solitaire, Eddie (VPN software for AirVPN), etc. - the buttons remain on the right.  I have found a way around this: if I reload the desktop by running alt-F2-r, the refreshed desktop then moves the buttons to the left.

2.  Not related to problem 1, after either computer runs for a few hours, the Show Apps window shows no apps at all.  It's empty.  If I run alt-F2-r to restart the desktop, however, after I open Show Apps everything is there.  This happens every few hours: I haven't noticed any particular time period, or if it is related only to running certain apps.  (This was a problem I noticed on Kinetic, also.)  This happens when running Wayland, too, although I can't restart the desktop with alt-F2-r on Wayland; I have to reboot.

Any ideas?

mcellius

---

### Post by Hreinsi on 2023-04-06
Have that same issue marked 2 after suspend no dash no apps

---

### Post by jbicha on 2023-04-06
There was a [mutter]("https://launchpad.net/ubuntu/+source/mutter/44.0-2ubuntu3") fix yesterday that I think would fix your first issue. Install all updates then log out and log back in.

I always use Wayland and I have never noticed the second issue. It's worth reporting a bug for it. Also, do you use GNOME Shell extensions? If you have any extensions besides the extensions Ubuntu enables by default, try disabling those and see if that issue still happens.

---

### Post by Hreinsi on 2023-04-07
> **jbicha said:**
> There was a [mutter]("https://launchpad.net/ubuntu/+source/mutter/44.0-2ubuntu3") fix yesterday that I think would fix your first issue. Install all updates then log out and log back in.

I always use Wayland and I have never noticed the second issue. It's worth reporting a bug for it. Also, do you use GNOME Shell extensions? If you have any extensions besides the extensions Ubuntu enables by default, try disabling those and see if that issue still happens.

Jebb  here it was Dash to Dock so now all good :)

---

### Post by den_ on 2023-04-07
Sorry for jumping in with the off topic question, but I noticed you mentioning xorg. I haven't used a linux desktop distro in years. I will try finding time to install the beta (Or a daily build might make more sense?) these days. My machine has an older intel CPU and 970 GTX Nvidia card. Are there still reasons to avoid Wayland and go with xorg?

---

### Post by mcellius on 2023-04-07
That Mutter fix may have fixed the first problem for me: the buttons are now all on the left upon booting so I don't have to hit alt-F2-r after booting.  (At least for today.)

---

### Post by mcellius on 2023-04-07
The only reason I've been avoiding Wayland has been because of the second problem I listed: if I need to restart the desktop to get applications to show in the Show Apps window, Wayland won't let me run alt-F2-r.  The only way to restore it is to reboot, and I don't want to have to do that every few hours.

---

### Post by den_ on 2023-04-07
> **mcellius said:**
> The only reason I've been avoiding Wayland has been because of the second problem I listed: if I need to restart the desktop to get applications to show in the Show Apps window, Wayland won't let me run alt-F2-r.  The only way to restore it is to reboot, and I don't want to have to do that every few hours.

Thanks. You don't really have to reboot, but you may need to perform a hard restart (kill the process). Screen lock (super + L) seems to work for some people. There's also "Gnome Shell Extension Reloader" but it's not maintained any more.

---

### Post by mcellius on 2023-04-09
I don't know what update did it, but problem 2 now seems to be solved!  When I hit "Show Apps" now, even after the computer has been running for hours or days, it functions as it should.  The 23.04 beta now seems to run perfectly - if that can ever be said - on both of my computers.  Woo hoo!!!!

As well, a Bluetooth problem I had been having with Kinetic has now been fixed, too.  Great job, developers!

---

