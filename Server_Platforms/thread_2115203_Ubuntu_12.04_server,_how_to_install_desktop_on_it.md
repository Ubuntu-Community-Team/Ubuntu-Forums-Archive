---
title: "Ubuntu 12.04 server, how to install desktop on it ?"
date: 2013-02-12
forum: Server Platforms
---

### Post by jaho22 on 2013-02-12
I have ubuntu 12.04 on my server, i have the server edition.

How to install desktop to my server, and what remote desktop i can most easyly use and how to install and setup this remote desktop.

I have earlier experience only with ubuntu desktops.

---

### Post by rubylaser on 2013-02-12
If you want the standard desktop on your server, it is really much easier to install the Ubuntu Desktop version.  The main point of the server version is to have minimal packages installed to have a smaller resource load and fewer potential programs to compromise.  You would typically administrated the server version via SSH (or Webmin if you really want a GUI).

---

### Post by The Cog on 2013-02-12
The command would be one of:
> sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install kubuntu-desktop
If you install more than one, I think you get the choice of which one to use at the graphical login window. However, I would probably only install one as I don't know what conflicts in settings ther might be between them.

As for which, I'm not sure. Personally I would go for Xubuntu, but that's a very personal decision. For occasional server maintenance Lubuntu (the lightest weight desktop) would probably suffice. Ubuntu itself is the heaviest weight, requiring 3D graphics acceleration.

I'm not sure about remote desktops - hopefully someone else can provide info. I don't use them myself, I just use ssh/sftp for remote terminal login and remote file management. On the odd occasion where I want to run a GUI on the server, I just use "ssh -X" to tunnel the application window back to my local desktop and launch the app fromn the command line.

---

### Post by ajgreeny on 2013-02-12
The desktop you need depends on exactly what you want to do with it.

You do not really need to add any of the ***ubuntu-desktop** packages with all the dependencies they will bring, but could install either xfce4, lxde, kde, without all the artwork and add-ons that the *ubuntu-desktop will bring along as well.

You should also consider using a simple window-manager such as **openbox**, to which you could then add the file manager, and other apps you want or need, of your own choice.

---

### Post by ibjsb4 on 2013-02-12
A minimal desktop install using gnome-classic.

```
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback
```

---

