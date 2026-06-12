---
title: "upgrade from unity changed notification themes"
date: 2012-05-22
forum: Ubuntu Studio
---

### Post by kvfjbb on 2012-05-22
so i recently upgraded my standard ubuntu 12.04 LTS to ubuntu studio. i installed the ubuntu studio desktop as well as the audio and audio plugins packages and since then my brightness and volume indicators have changed to large, intrusive images in the centre of my screen, as opposed to their usual place in the top right-hand corner. in addition, my regular notification bubbles have changed, the background is now white instead of black. 

the weird thing is that none of this occurs in the ubuntu studio DE, only in unity. i tried deleting xfce4notifyd via synaptic but it made no difference. 

does anyone else have this issue? any ideas?
(i have screenshots of the changed notifications if anyone is interested in them)

cheers,
toby.

---

### Post by kvfjbb on 2012-05-29
bump. anybody have the same issue?

---

### Post by kvfjbb on 2012-06-06
found a new solution, albeit a tad stop-gap...

on a fresh install and new notebook i installed the ubuntustudio-desktop, audio and audio-plugins metapackages. this time when i tried to remove xfce4notifyd, synaptic warned me that it would also remove the ubuntutudio-desktop. i removed both packages but retained the config files.

now my notifications in unity are back to normal and i still have full access to the ubuntustudio de. i just have to make sure to briefly install the aforementioned packages before performing anything like sudo apt-get autoremove && sudo apt-get autoclean.

but this is a fairly inelegant solution, does anyone else have a better idea?

---

### Post by kvfjbb on 2012-06-07
ok, found a decent workaround, i concluded that the only major difference between the studio desktop and the xfce desktop was the applications menu. so i first backed up both application menus then ran :

```
gksudo gedit /etc/xdg/menus/xfce-applications.menu
```then i copied in the text from the studio menu config file ( /etc/xdg/xdg-ubuntustudio/xfce-applications.menu).

after completely removing the ubuntustudio-desktop and xfce4-notifyd packages and rebooting my unity is left as standard and the xfce DE seems to work fine with notifyosd.

the only step left was to remove the ubuntu studio DE from my login screen:

```
cd /usr/share/xsessions
ls
sudo rm *ubuntustudio.desktop_or_what_ever_it_is
```and solved! i hope this can help someone else who has a similar problem.

---

