---
title: "log out using terminal ?"
date: 2013-03-10
forum: Ubuntu Development Version
---

### Post by ronacc on 2013-03-10
how do I log out of the desktop using the terminal ? I logged out of gnome-shell and into unity but unity is crippled on my sys and I have no top bar and can't get to the launcher or logout ,restart etc with the mouse , I can get to a terminal an launch things that way .

---

### Post by steeldriver on 2013-03-10
you could restart the display manager - should return you to the greeter screen where you can select gnome-shell again

```
sudo service lightdm restart
```

---

### Post by sudodus on 2013-03-10
I don't know the logout command in Unity (I use Lubuntu and LXDE most of the time), but I know these self-explaining commands, that work in all Ubuntu flavours

```
sudo reboot
```
```
sudo poweroff
```

They perform actions of the same quality as the corresponding graphical actions.

---

### Post by mc4man on 2013-03-10
May not help because requires accepting 
```
/usr/lib/indicator-session/gtk-logout-helper --logout
```

---

### Post by ronacc on 2013-03-10
thanks all,  I used  mc4man's suggestion and that got me back to the login screen so I could get back into gnome-shell . ( I was able to "accept "  the logout , everything worked except the top panel and launcher) .

---

### Post by serdotlinecho on 2013-03-11
```
~&#10095; ps -ef | grep gnome-session
1000      1601  1461  0 14:34 ?        00:00:00 gnome-session --session=ubuntu
1000      1647  1601  0 14:34 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=ubuntu
1000      1650     1  0 14:34 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=ubuntu
1000      1668     1  0 14:34 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
1000      2284  2188  0 14:36 pts/1    00:00:00 grep --color=auto gnome-session
~&#10095; kill -15 1601
```

---

