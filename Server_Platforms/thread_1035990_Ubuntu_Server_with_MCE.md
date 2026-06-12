---
title: "Ubuntu Server with MCE"
date: 2009-01-10
forum: Server Platforms
---

### Post by badeguruji on 2009-01-10
Hello,

I want to run LinuxMCE and ubuntu server. LinuxMCE uses KDE and ubuntu uses Gnome. The Ubuntu server feature page shows a good list of packages. Can I have a kubuntu server with same server feature list? I guess I want to ask, does ubuntu server installation gives me option to install KDE /Gnome at the time of install? so that i end up with a kubuntu server with exact same feature list except the desktop-manager? I do not want to have two desktop managers on my server.

I want to keep it simple, i understand that i can remove gnome and install kde later, but i feel that leaves residual software behind and might affect other apps, which needs desktop manager to function.

Thank you.
-Rajeev

---

### Post by volkswagner on 2009-01-10
The server install disk only has a command line interface.  There is no desktop manager.  You would need to install xfce via apt, after the install is complete.

There is a how to which you could use, under the minimal [install]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

Why not just install kubuntu?

Why would you dual boot a server?  Or is it a VirtualMachine?
Just curious?

---

### Post by atboom on 2009-01-10
LinuxMCE is an addon to Kubuntu and not a seperate distro, so it wouldnt be dual boot.
Volks is right that the server does not have a desktop installed, but you can install kubuntu afterwards by just typing 
```
sudo aptitude install kubuntu-desktop
```

---

