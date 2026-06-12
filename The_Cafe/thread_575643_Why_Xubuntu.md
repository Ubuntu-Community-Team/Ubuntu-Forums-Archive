---
title: "Why Xubuntu?"
date: 2007-10-14
forum: The Cafe
---

### Post by SuperMike on 2007-10-14
You know, the new Xubuntu sure does look nice, and it does look enticing, but why do people go with it? I mean, the moment you open your first GNOME app in this Xubuntu environment, that's the moment that the GNOME shared object libraries get loaded into memory. Not everything is made to be optimized just for Xubuntu yet, so you have higher odds of GNOME being loaded into RAM eventually.

I mean, here's my output on Feisty from all things GNOME loaded in my memory on my system:

```
 5197 ?        S      0:39    172  1222 121845 29656  5.7 nautilus --no-default-window --sm-client-id default2
 4509 ?        Ssl    0:00      1   274 12053  1964  0.3 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 4544 ?        Ss     0:00      0    13  3046  1268  0.2 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 4590 ?        Ss     0:00      0   267 11952  1456  0.2 /usr/sbin/gdm
 4593 ?        S      0:00      1   267 12312  2388  0.4 /usr/sbin/gdm
 5173 ?        S      0:00      0    19  2640   628  0.1 /usr/bin/dbus-launch --exit-with-session x-session-manager
 5176 ?        S      0:01      2    47  6632  4200  0.8 /usr/lib/libgconf2-4/gconfd-2 6
 5179 ?        S      0:00      0    84  2671  1000  0.1 /usr/bin/gnome-keyring-daemon
 5181 ?        Sl     0:14     27   156 29555 10132  1.9 /usr/lib/control-center/gnome-settings-daemon
 5196 ?        S      0:54     79   478 58197 21680  4.2 gnome-panel --sm-client-id default1
 5207 ?        Ss     0:00      0    49 19618  5776  1.1 gnome-volume-manager --sm-client-id default4
 5212 ?        S      0:00      2    82  8377  3436  0.6 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5246 ?        S      0:00      8    22 39985  8164  1.5 gnome-cups-icon --sm-client-id default3
 5250 ?        Ss     0:01      1   252 34187  6628  1.2 gnome-power-manager
 5262 ?        S      0:00      1    34 65253  9644  1.8 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
 5264 ?        S      0:02      7    37 36070 13528  2.6 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=27
 5266 ?        S      0:00      1    22  2437   884  0.1 /usr/lib/nautilus-cd-burner/mapping-daemon
 5326 ?        Ss     0:44      0   123 15940  4492  0.8 gnome-screensaver
22921 ?        Sl     0:00     17   279 57860 16664  3.2 gnome-terminal
22923 ?        S      0:00      1     7  2452   732  0.1 gnome-pty-helper
```



It uses 26.9MB. Is that really such a big deal? If I load Xubuntu will I really save that much more memory? And, again, I just don't see why to go with Xubuntu when the moment I load my first GNOME app all these shared objects start loading into RAM again, and there are not enough made-for-XFCE apps yet.

---

### Post by Mazza558 on 2007-10-14
I use Xfce because I'm a minimalist at heart. It still seems faster than Gnome, even with Exaile and such open, as well as Compiz Fusion.


[[IMG]http://img98.imageshack.us/img98/3792/desktophp6.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=desktophp6.jpg)

[[IMG]http://img152.imageshack.us/img152/9804/desktop2py8.th.jpg[/IMG]](http://img152.imageshack.us/my.php?image=desktop2py8.jpg)

---

### Post by tdrusk on 2007-10-14
> **SuperMike said:**
> You know, the new Xubuntu sure does look nice, and it does look enticing, but why do people go with it? I mean, the moment you open your first GNOME app in this Xubuntu environment, that's the moment that the GNOME shared object libraries get loaded into memory. Not everything is made to be optimized just for Xubuntu yet, so you have higher odds of GNOME being loaded into RAM eventually.

I mean, here's my output on Feisty from all things GNOME loaded in my memory on my system:

```
 5197 ?        S      0:39    172  1222 121845 29656  5.7 nautilus --no-default-window --sm-client-id default2
 4509 ?        Ssl    0:00      1   274 12053  1964  0.3 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 4544 ?        Ss     0:00      0    13  3046  1268  0.2 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 4590 ?        Ss     0:00      0   267 11952  1456  0.2 /usr/sbin/gdm
 4593 ?        S      0:00      1   267 12312  2388  0.4 /usr/sbin/gdm
 5173 ?        S      0:00      0    19  2640   628  0.1 /usr/bin/dbus-launch --exit-with-session x-session-manager
 5176 ?        S      0:01      2    47  6632  4200  0.8 /usr/lib/libgconf2-4/gconfd-2 6
 5179 ?        S      0:00      0    84  2671  1000  0.1 /usr/bin/gnome-keyring-daemon
 5181 ?        Sl     0:14     27   156 29555 10132  1.9 /usr/lib/control-center/gnome-settings-daemon
 5196 ?        S      0:54     79   478 58197 21680  4.2 gnome-panel --sm-client-id default1
 5207 ?        Ss     0:00      0    49 19618  5776  1.1 gnome-volume-manager --sm-client-id default4
 5212 ?        S      0:00      2    82  8377  3436  0.6 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 5246 ?        S      0:00      8    22 39985  8164  1.5 gnome-cups-icon --sm-client-id default3
 5250 ?        Ss     0:01      1   252 34187  6628  1.2 gnome-power-manager
 5262 ?        S      0:00      1    34 65253  9644  1.8 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
 5264 ?        S      0:02      7    37 36070 13528  2.6 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=27
 5266 ?        S      0:00      1    22  2437   884  0.1 /usr/lib/nautilus-cd-burner/mapping-daemon
 5326 ?        Ss     0:44      0   123 15940  4492  0.8 gnome-screensaver
22921 ?        Sl     0:00     17   279 57860 16664  3.2 gnome-terminal
22923 ?        S      0:00      1     7  2452   732  0.1 gnome-pty-helper
```



It uses 26.9MB. Is that really such a big deal? If I load Xubuntu will I really save that much more memory? And, again, I just don't see why to go with Xubuntu when the moment I load my first GNOME app all these shared objects start loading into RAM again, and there are not enough made-for-XFCE apps yet.

xfce environment is lighter than gnomes. when you load a gnome program you don't load every gnome library. If you load every gnome app it would be stupid, but for just one or 2 xfce is good.

---

### Post by mrbungle on 2007-10-14
just love how much faster it is.

---

