---
title: "How to install ubuntu-desktop-14.04-x64.iso on server"
date: 2014-11-22
forum: Server Platforms
---

### Post by lindevox on 2014-11-22
Hi,

After done installing ubuntu 14.04-x64 server and managed to install ubuntu 14.04 Desktop on it by typing:
```

       $ sudo apt-get update
       $ sudo apt-get install ubuntu-desktop

```

allow me to have GUI on ubuntu server, But every time I need Internet connection to install the Desktop, and because of slow internet connection at my place,
I was thingking if there is any instruction on how to install ubuntu 14.04 x64 desktop on the server from the downloaded ubuntu desktop iso file. 

Wonder if someone could share a light! TIA

---

### Post by ibjsb4 on 2014-11-22
I have never had the need to use it, but what about apt-cdrom?

In terminal:
```
man apt-cdrom
```
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apt-cdrom&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apt-cdrom&sa=Search&cof=FORID:9)

---

### Post by lindevox on 2014-11-23
Hi ibjsb4, your answer did share me a light to google for apt-usb and found a thread: [http://ubuntuforums.org/showthread.php?t=1010582](http://ubuntuforums.org/showthread.php?t=1010582) tho it might not be very useful for my situation now. TQ

---

### Post by ibjsb4 on 2014-11-23
What about a clone of the first install?

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Tadaen_Sylvermane on 2014-11-24
Backup your /var/cache/apt/archives folder. Specifically the .debs inside it. Then you need only download a package once. On a fresh install just copy the backed up *.debs into /var/cache/apt/archives on the new install. It will work with those instead of a download unless of course there is an update for that package available.

---

### Post by mastablasta on 2014-11-25
ad the cd to repositories (software sources) and install from CD?

anyway you don't need a whole desktop to have a GUI on server. just install webmin, zentyal or ajenti or something like that. control the server from browser webgui and via SSH.

BTW zentyal install media comes with GUI (XFCE) on server as well as webgui. selecting expert mode will offer to install only webgui without the desktop.

---

