---
title: "My wallpaper won't change"
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by cis190 on 2013-04-19
After updating to 13.04 my wallpaper will not change, I have noticed that when I change themes the background will change with the theme color scheme.... But if I change the wallpaper itself it doesn't do anything, how do I fix this???

---

### Post by Adelard on 2013-04-19
Same here with Gnome fallback or Unity.

---

### Post by Adelard on 2013-04-19
Ok, with Gnome tweak and not letting the managing desktop option on, I get my desktop back.[IMG]http://ompldr.org/vaTVrNw/Capture%20du%202013-04-19%2020:36:19.png[/IMG]

---

### Post by cis190 on 2013-04-19
It did not work, I turned it on and off and I still couldn't get my desktop back, is there anyway that I could reinstall some package, im stumped on how to fix it

---

### Post by serdotlinecho on 2013-04-20
Install trash-cli(much safer than rm command) and delete this folder:

```
sudo apt-get install trash-cli
trash-put $HOME/.cache/wallpaper
```

And restart lightdm service:

```
sudo service lightdm restart
```

---

### Post by PJs Ronin on 2013-04-20
> **serdotlinecho said:**
> And restart lightdm service:

```
sudo service lightdm restart
```

That command crashed my system... had to come back via recovery.... just a fyi.

---

### Post by ernestj on 2013-04-20
this may not have anything to do with your problem. but, it you go to your pictures folder and allow the permissions to "access files" for group and others. that could help.

Ernie

---

### Post by Frogs Hair on 2013-04-20
If the let file manager handle desktop function is disabled so is the desktop context menu (change background) and ability to drag files on the desktop.

---

### Post by serdotlinecho on 2013-04-21
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```
[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

```
gnome-session-properties
```

[IMG]http://i.imgur.com/5lxdBle.png[/IMG]

---

### Post by cis190 on 2013-04-21
sadly none of the fixes worked for me.... I think there is something corrupt or something just plain broken in it, so I'm going to reinstall the system, oh well I hoped this help others at least :p

---

