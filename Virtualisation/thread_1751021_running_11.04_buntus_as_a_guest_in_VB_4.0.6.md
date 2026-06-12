---
title: "running 11.04 *buntus as a guest in VB 4.0.6"
date: 2011-05-06
forum: Virtualisation
---

### Post by loukingjr on 2011-05-06
I am trying to run Ubuntu, Xubuntu and Lubuntu 11.04 as guests in VirtualBox 4.0.6 as guests on an iMac host running 10.6.7 with varying degrees of success.

First, Lubuntu seems to work fine.

Second, Xubuntu works except for some reason I have to run "**xfwm4 --replace**" every time I boot or reboot in order to get the correct xcursor to show up.

Now, the main problem. I can't get Ubuntu to run correctly for the life of me. Once I install it to a .vdi I have a number of problems. In all sessions; classic (no effects), classic, Ubuntu etc, the screen draws everything correctly but after several seconds the theme switches to the default root theme. I have to run "**killall -9 gnome-settings-daemon && gnome-settings-daemon**" every time I boot or reboot in order to get the correct theme to display. nautilus however still is using the root theme so then I have to run "**killall nautilus && nautilus**" to get that to use the correct theme. That doesn't help 100% with Unity however becuase when I mouse over the left panel icons the popup tooltips just draw garbage snd the icons in the top panel appear and disappear in a loop.

What I don't understand is I get none of the theme problems when running the .iso as a live CD although I can't run Unity due to the lack of 3D without the guest additions installed.

For the heck of it I downloaded a recent amd64+mac daily build of Ubuntu 11.04, burned it to a CD and lo and behold it booted my iMac without a problem and Unity et al ran just fine.

I'm not understanding why Ubuntu 11.04 runs just fine on my hardware, the .iso runs fine as a live cd in VB, but once installed to a .vdi there are so many issues. If anyone has any insight I would appreciate it.

thanks ahead of time.

p.s. I also tried installing iQuinix which runs 11.04 without Unity or Gnome 3 etc pre-installed and once again, runs fine from the .iso but has the above theming issues once installed as a guest.

---

