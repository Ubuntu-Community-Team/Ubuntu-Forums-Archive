---
title: "unknown cause of GUI issues"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by coller_girl on 2012-09-21
GUI issues:

[IMG]http://bayimg.com/MAcdoaAeM[/IMG]

as you can see from this image the menu bar and the "grabby bar" (technical term... meaning that bar you click onto and control the window with, including the close, minimise, and open functions)  are not loading in ubuntu 12.10.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054144](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054144)

Is that bug report ok?

---

### Post by ranger1021994 on 2012-09-21
Sorry but i cannot see image, can u please upload it again ?

---

### Post by grahammechanical on 2012-09-21
The three images that are attached to the bug report do not show a default 12.10 + Unity or + Gnome 3 Shell. Do they?

You should state what modifications you have made to the desktop. It could be the package that you are using to get the Gnome 2 classic look that is causing a conflict with Unity and Gnome 3 shell in 12.10.

I remember reading on the Gnome web site back when Gnome 3 was being brought in that compatibility with Gnome 2 libraries would continue for a while but would eventually be removed as everything about Gnome was migrated to Gnome 3.

Regards.

---

### Post by mc4man on 2012-09-21
Install compizconfig-settings-manager, open it up, (ccsm) & make sure the Window Decoration plugin is enabled

---

### Post by coller_girl on 2012-09-21
I updated two packages as i was requested to do so 

"The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

libgl1-mesa-glx, libglapi-mesa "


 we can see what's happening after a reboot

---

### Post by jbicha on 2012-09-21
Are you using GNOME Classic or GNOME Classic (without effects)?
Are you using Ubuntu or the Ubuntu GNOME Remix?
Did you take any steps to uninstall Unity or Compiz?
Do you understand what partial upgrades are and how to safely upgrade during development releases?
Is ubuntu-desktop installed?

---

