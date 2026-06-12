---
title: "GUI Interface for Ubuntu server edition"
date: 2008-12-22
forum: Server Platforms
---

### Post by ishfady on 2008-12-22
Hi

I have just download Ubuntu Server Edition. I come from microsoft window, But I would like to move into Linux.

I bit new and been told that I need to download GUI Interface separtley. I Would like to install graphical inteface to do admin work on server.

Please could you recomend me any good GUI or how to activate GUI on Buntu.

many thank

---

### Post by clw3388 on 2008-12-22
Fairley strait foward..
in the terminal window type sudo startx..(X might be capitol? im stuck on a windows box atm..:( )
if it cant find it install it sudo apt-get install ubuntu-desktop...

---

### Post by lykwydchykyn on 2008-12-22
there's no gui installed by default, so "startx" will not work.

```

sudo apt-get install ubuntu-desktop

```

...will get you the whole shebang -- GNOME desktop, apps, effects, etc.  

If you want something lighter, just so you can look at a GUI while editing config files instead of a console, you might want to use XFCE or JWM.

lighter GUI:
```

sudo apt-get install gdm xfce4 xorg

```

Really light GUI:
```

sudo apt-get install xdm xorg jwm

```

The question is, what do you want from a GUI?  I ask because there are many options, and picking the right option means knowing what you want.

---

### Post by hictio on 2008-12-22
The command its 'startx' w/o the quotes and no capital X.
Issuing a "sudo apt-get install ubuntu-desktop" will install a full blown Gnome desktop, which is perfectly fine, if that's what you want.

Also, take a look at some other variants:

[Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)
[Installation Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Iowan on 2008-12-22
Another option (as if you needed more) is to use [eBox]("https://help.ubuntu.com/community/eBox") or [ WebMin]("https://help.ubuntu.com/community/WebMin") to administer the server.

---

### Post by walter_j on 2008-12-22
i use ssh to log into the server and can maintain it from a remote site. check out openssh.

not including a gui for the server was a poor choice imo. They could have installed gnome or xfce and left the user to start it manually when needed. i don't know if there is a way to only stop the gui tho.

i tried installing gnome too, but i had problems during the install, so i didn't bother with it. If you use the cli you may have to learn to use the vim editor though. nano editor is simple, but if you need line numbers you may be out of luck.

---

### Post by Titan8990 on 2008-12-22
It is best not leave it without the GUI. If you must I would recommend something lightweight:


sudo apt-get install jwm

startx


> Another option (as if you needed more) is to use eBox or  WebMin to administer the server.


For databases there is also phpmyadmin.

---

