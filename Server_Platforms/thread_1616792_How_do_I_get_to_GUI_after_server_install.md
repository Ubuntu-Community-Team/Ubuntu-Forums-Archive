---
title: "How do I get to GUI after server install?"
date: 2010-11-08
forum: Server Platforms
---

### Post by tehpwnerer1918 on 2010-11-08
I just finished installing Ubuntu Server Edition 10.10. After reboot it brings me to a shell prompt asking for username and then password. After putting it in I just get a blank shell prompt. How do I get into the GUI ?

---

### Post by arrrghhh on 2010-11-08
There isn't one.

With that said, I use Webmin - web based UI.  If you want a UI directly on the machine, see the Ubuntu doc on [ServerGUI](https://help.ubuntu.com/community/ServerGUI).

Also, you can run ALL services and applications from Ubuntu Desktop just the same as Ubuntu Server.  Server edition is optimized to run bare-bones, so I would **NOT** recommend putting a GUI onto the server edition when Ubuntu-desktop already exists for those that want a GUI.

---

### Post by thegodfaza on 2010-11-08
On my Ubuntu Server I installed ubuntu-desktop (apt-get install ubuntu-desktop) then I disabled it from starting up with the system (sudo update-rc.d -f gdm remove). When I need to use gnome to configure GUI-only apps that I run using the X11 emulator xvfb, I just run "sudo service gdm start" and whem I'm done, "sudo service gdm stop" or I use a tightvnc session.

---

### Post by arrrghhh on 2010-11-08
Also keep in mind any apps that require X can be forwarded over ssh, no need to install GNOME or ubuntu-desktop then ;)

Again, if you want GNOME, it's probably easiest to just install ubuntu-desktop and forego the -server edition :D

---

### Post by amauk on 2010-11-08
If you want a GUI on a server, you're doing it wrong ;)

---

### Post by HermanAB on 2010-11-08
Howdy,

Either install regular Ubuntu, or install the Gnome packages.

---

### Post by James78 on 2010-11-09
The server doesn't have a GUI for a reason! You should use the command line for everything, just learn how it works, it's really powerful. I don't have a GUI on my server and I have it setup perfectly. Just install SSH and maybe Samba, SSH from your desktop Linux computer, and use Samba to access/edit/add/delete the files easily. No need for any extra unneeded overhead or packages on a server that could be using the CPU to process web traffic instead.

---

