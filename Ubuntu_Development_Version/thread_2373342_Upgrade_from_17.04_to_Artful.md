---
title: "Upgrade from 17.04 to Artful"
date: 2017-10-05
forum: Ubuntu Development Version
---

### Post by P-I H on 2017-10-05
I have made two upgrades.

One from a new install of Ubuntu 17.04. The upgrade worked OK. The two extensions Ubuntu Dock and Ubuntu appindicators worked fine. Both the Dropbox indicator and the Psensor indicator were shown.

One from a used installation. The upgrade worked OK, but after restart Ubuntu Dock didn't show and I was asked to report a gnome-shell bug.
The installation had these gnome extensions installed, Better volume indicator, Dash to Dock, OpenWeather, No Topleft Hot Corner and TopIcons Plus.
Indicators for Dropbox and Psensor worked both before and after removal of TopIcons Plus

The folder etc/var/crash included a gnome-shell crash and I suppose that triggered the bug report.

I have tried to get Ubuntu dock to work without success. 
- Removed the extensions Dash to Dock, No Topleft Hot Corner and TopIcons Plus
- Reinstalled Ubuntu dock with Synaptic (after xhost +si:localuser:root)
- Tried with both the ubuntu and ubuntu on xorg  login

---

### Post by dino99 on 2017-10-05
you might have some old settings/packages disturbing the wayland session (now default). So clean the system using gtkorphan & bleachbit (as root)

---

### Post by dino99 on 2017-10-05
you might have some old settings/packages disturbing the wayland session (now default). So clean the system using gtkorpgan & bleachbit (as root)
Also note that the Artful archive have some gnome-shell-extension-* packages which set entry into the /usr/ dir. Take care of the idem dupe(s) into .local (installed from from the url)

---

### Post by jbicha on 2017-10-05
Try

```

gsettings get org.gnome.shell enabled-extensions
gsettings reset org.gnome.shell enabled-extensions

```

Then log out and log back in.

---

### Post by P-I H on 2017-10-06
That worked.
The command "gsettings reset org.gnome.shell enabled-extensions" logged me out and at log in Ubuntu dock was back.

I will check how a new installation with the gnome desktop will behave.

---

### Post by P-I H on 2017-10-06
Installed 17.04 and Gnome desktop with "sudo apt-get install gnome-shell ubuntu-gnome-desktop".
Restarted and signed in with Gnome. Upgraded to Artful with "sudo do-release-upgrade -d".
The upgrade work as expected and took about 15 minutes.

---

