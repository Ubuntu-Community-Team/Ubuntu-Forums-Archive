---
title: "Unity will not show wallpaper/only when mouse is pressed"
date: 2012-08-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-30
I'm having probs with  and Intel based graphics adapter. Menus will not come up properly and wallpaper will not show unless left-mouse is pressed or unity dash is up. Started happening with 3.5.0-11.. now 3.5.0-13 kernel.no change since update.

```

ventrical@ventrical-Dell-DV051:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```

---

### Post by Bowmore on 2012-08-30
Most likely this mesa bug:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1042211](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1042211)

Try to downgrade mesa to version 8.0.4.
[https://launchpad.net/ubuntu/quantal/+source/mesa/8.0.4-1ubuntu1](https://launchpad.net/ubuntu/quantal/+source/mesa/8.0.4-1ubuntu1)

---

### Post by ventrical on 2012-08-30
Not sure where the .deb file is to install. Downloaded the tar.gz  but no .deb.?

---

### Post by Bowmore on 2012-08-30
You'll find the debs under builds for your archictecture and I guess the following packages need to be downgraded:
libgl1-mesa-dri
libgl1-mesa-glx
libglapi-mesa
libxatracker1
libglu1-mesa

---

### Post by ventrical on 2012-08-30
> **Bowmore said:**
> You'll find the debs under builds for your archictecture and I guess the following packages need to be downgraded:
libgl1-mesa-dri
libgl1-mesa-glx
libglapi-mesa
libxatracker1
libglu1-mesa


libglapi breaks libgl1-mesa glx and mesa-glx will not install.

ready for reboot anyways :)

Installing:

libxatracker1
libglu1-mesa
libgl1-mesa-dri

worked just great!

Thanks Bowmore.

---

### Post by Bowmore on 2012-08-30
Well, you shall download those debs and store them in a new folder and then run the commands:
```
cd <path_to_that_folder>
sudo dpkg -i *.deb
```
Sorry, you made it work ;)

---

### Post by ventrical on 2012-08-30
Doh ! I used the Qapt package installer. mabey thats why  those other two files didn't load. But works great anyways. as ronacc says . ."if it ain't broke, don't fix it". ! lol

---

