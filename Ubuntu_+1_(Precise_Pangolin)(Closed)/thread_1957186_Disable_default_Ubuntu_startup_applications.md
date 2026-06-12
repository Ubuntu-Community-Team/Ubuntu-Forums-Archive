---
title: "Disable default Ubuntu startup applications"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by drumour on 2012-04-12
Trying to streamline my setup across all my systems. To this end I am interested in stopping some default startup stuff becuase I have my own ways of doing things or I dont require the services e.g deja-dup, update notifier and ubuntuone. According to this webpage - [http://www.upubuntu.com/2011_10_01_archive.html](http://www.upubuntu.com/2011_10_01_archive.html) in 11.10, it is possible by:
going into the following directory - cd /etc/xdg/autostart/
listing whats there - ls 
then using the following command to stop something from autostarting, in this example deja-dup -
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' deja-dup-monitor.desktop

I've tried this on 12.04 but on reboot, processes in system monitor still shows them as running...

---

### Post by dino99 on 2012-04-12
if the ubuntu-desktop metapackage is removed, then you can uninstall what you does not need, like ubuntuone, etc

---

### Post by zika on 2012-04-12
> **drumour said:**
> Trying to streamline my setup across all my systems. To this end I am interested in stopping some default startup stuff becuase I have my own ways of doing things or I dont require the services e.g deja-dup, update notifier and ubuntuone. According to this webpage - [http://www.upubuntu.com/2011_10_01_archive.html](http://www.upubuntu.com/2011_10_01_archive.html) in 11.10, it is possible by:
going into the following directory - cd /etc/xdg/autostart/
listing whats there - ls 
then using the following command to stop something from autostarting, in this example deja-dup -
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' deja-dup-monitor.desktop

I've tried this on 12.04 but on reboot, processes in system monitor still shows them as running...For deja-dup I did ```
#X-GNOME-Autostart-Delay=120
X-GNOME-Autostart-enabled=false

```in /etc/xdg/autostart/deja-dup-monitor.desktop ...

You do not have to reboot, simple restart of X is sufficient...

---

### Post by xyzzyman on 2012-04-12
At a cli

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Then disable everything you want in 'startup applications' on the menu in the far upper right, the gear icon one.

---

### Post by shadowfirebird on 2012-04-12
> **xyzzyman said:**
> At a cli

```
cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

Then disable everything you want in 'startup applications' on the menu in the far upper right, the gear icon one.

yesyesyesyes.  Thank you!  ):P

---

### Post by drumour on 2012-04-12
Yes, thanks too xyzzyman

---

