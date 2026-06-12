---
title: "ubuntu server"
date: 2006-10-11
forum: Server Platforms
---

### Post by visualfox on 2006-10-11
Hi guys,
Congratutlations for excellent work in ubuntu,it is very good specially for begginers.I installed ubuntu server and it hasn't got
graphical enviroment,Can i login or install xwindows(graphics) in ubuntu server edition??
If no how i can install servers(apache) from command line(unix)?
Thanks you very much!

---

### Post by Endwin on 2006-10-11
Yes you can install a graphical enviornment on the server (some people don't reccomend it for security/resource problems). You can do so with...

```
sudo aptitude -R ubuntu-desktop
```

If you have a weaker machine as the server maybe xface would be better.

```
sudo aptitude -R xubuntu-desktop
```

However you can do all the server stuff on the console. 

To install apache...

```
sudo aptitude -R apache2
```

---

### Post by XplOzIOn on 2006-10-11
Yep, i been using ubuntu server for some time now, and its pretty good i rather to have it without any GDM, and everything i do via terminal. Just post what are your needs, we will be glad to help

---

### Post by bswilson on 2006-10-11
> **visualfox said:**
> I installed ubuntu server and it hasn't got
graphical enviroment,Can i login or install xwindows(graphics) in ubuntu server edition??

The easiest way to install all the GUI tools you need is to install one of the prepackaged desktop environments:

```
$ sudo apt-get install ubuntu-desktop
```

You can install **ubunutu-desktop** (Gnome), **kubuntu-desktop** (KDE), or **xubuntu-desktop** (XFCE) depending on which one you want.

---

### Post by Iowan on 2006-10-11
Cute tag - but **server** or **graphical user interface** might draw more responses.

---

