---
title: "Mubuntu - MATE is in the 14.04 repos"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by oldrocker99 on 2014-03-29
I started with Hardy Heron (8.04) and soon grew to love the GNOME 2.3 desktop. 

Then things started to go south. Unity replaced GNOME, GNOME 3.x replaced GNOME 2.3. When I first heard about MATE, I installed the Mint version with MATE and was a happy camper.

However, as irritating as some of the aspects of using *buntu may be, I found Mint to be more annoying, so I went back to Kubuntu with MATE (from a PPA).

Just installed Kubuntu 14.04, and (to my delight) MATE is in the repos!

I'm an even happier camper.

---

### Post by kansasnoob on 2014-03-29
> **oldrocker99 said:**
> I started with Hardy Heron (8.04) and soon grew to love the GNOME 2.3 desktop. 

Then things started to go south. Unity replaced GNOME, GNOME 3.x replaced GNOME 2.3. When I first hard about MATE, I installed the Mint version with MATE and was a happy camper.

However, as irritating as some of the aspects of using *buntu may be, I found Mint to be more annoying, so I went back to Kubuntu with MATE (from a PPA).

Just installed Kubuntu 14.04, and (to my delight) MATE is in the repos!

I'm an even happier camper.

Have you actually tried installing Mate from the repos?

About one week ago it was still broken.

---

### Post by oldrocker99 on 2014-03-29
In fact, it was broken. It wasn't available from the display manager as a session. I ended up installing MATE 1.8 from the matedesktop.org repos, which has Trusty versions. All is well.

---

### Post by QDR06VV9 on 2014-03-30
Yes in deed works a treat, Been using it for a couple of weeks now.
just a few minor glitch's with compiz tossing the window decoration from time to time.
Other than that nothing to report bad. Oh  don't forget to have caja as the default file-manger
For those interested in trying it out. Taken Off webup8.
To add the MATE 1.8 repository and install MATE Desktop 1.8 in Ubuntu 14.04 Trusty Tahr or 13.10 Saucy Salamander, use the following commands:
```
echo "deb http://repo.mate-desktop.org/archive/1.8/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/mate-desktop.list
wget -qO - http://mirror1.mate-desktop.org/debian/mate-archive-keyring.gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get install mate-core mate-desktop-environment mate-notification-daemon
```

After it installs run dist-upgrade. Then I rebooted, on login window I of course choose the mate session.
And Then if you want to un-install mate
```
sudo apt-get remove atril atril-common caja caja-common engrampa engrampa-common eom eom-common gir1.2-mate-panel libatril libcaja-extension1 
libmarco-private0 libmate-desktop-2-17 libmate-menu2 libmate-panel-applet4-1 libmatekbd-common libmatekbd4 libmateweather-common libmateweather1 
marco marco-common mate-applets mate-applets-common mate-backgrounds mate-calc mate-calc-common mate-control-center mate-core mate-desktop
 mate-desktop-common mate-desktop-environment mate-dialogs mate-dialogs-common mate-icon-theme mate-media mate-media-common
 mate-media-gstreamer mate-menus mate-notification-daemon mate-panel mate-panel-common mate-polkit mate-polkit-common mate-power-manager
mate-power-manager-common mate-screensaver mate-screensaver-common mate-session-manager mate-settings-daemon mate-settings-daemon-common
 mate-settings-daemon-gstreamer mate-system-monitor mate-terminal mate-terminal-common mate-themes mate-utils mate-utils-common pluma pluma-common
```

Then to remove  the PPA

```
sudo rm /etc/apt/sources.list.d/mate-desktop.list
```

Enjoy Mate 1.8;)

---

### Post by buzzingrobot on 2014-03-30
The 1.8 in that directory is an unofficial build by the devs. It was OK here, but I imagine there are reasons it is not yet available in the official Mate repos.

---

