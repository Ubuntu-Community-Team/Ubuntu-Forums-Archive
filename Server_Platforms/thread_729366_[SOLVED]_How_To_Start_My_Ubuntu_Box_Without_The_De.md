---
title: "[SOLVED] How To Start My Ubuntu Box Without The Desktop and Use as NAS?"
date: 2008-03-19
forum: Server Platforms
---

### Post by MountainX on 2008-03-19
I want to set my machine so it will boot without starting up the desktop environment.

I want to temporarily use this box as a file server (home made NAS) on my LAN. I do not want to remove/uninstall the desktop environment. I just want to temporarily disable it. I'm running Gutsy.

How do I let it boot up and have the file sharing services start up without any user logging in locally at the machine?

I want to be able to log into shared folders from other computers on my LAN.

There are really several questions here:
1. how to change Gutsy so it will boot without the desktop environment.
2. how to enable shared folders. (I will mostly access the folders from another Ubuntu machine, but I also need access from a WIndows box).
3. how to make services available without logging in to the machine locally.

Thanks

---

### Post by mreynaga on 2008-03-19
not sure if you can disable this. i am probably wrong. i have all my ubuntu servers setup and never even installed the GUI desktop. this way it never runs and you can share files and folders and then simply mount them from the client computers and that is it. you never have to login to the server but can easily do so from a terminal with the SSH command

what do you mean by services? one of my servers is a print server and again i never have to login to it i simply add the printers to the clients and everything is lovely what other types of services are you talking about.

again you may be best off just installing the server without the GUI, this way it takes up way less resources and if you are running them as virtual servers you can have more servers without performance drops.

---

### Post by MountainX on 2008-03-20
> **mreynaga said:**
> 

what do you mean by services? one of my servers is a print server and again i never have to login to it i simply add the printers to the clients and everything is lovely what other types of services are you talking about.



All I really need is a file server. Glad to know I can just boot it up & let it do its job without logging in locally.

I would think there is some way to just tell Ubuntu not to start X when it boots up. That would be a lot easier than installing everything again.

---

### Post by mreynaga on 2008-03-20
wish i could be more help but i have no idea how you would start the server without the desktop environment.

---

### Post by Jose Catre-Vandis on 2008-03-20
Have a look here, should solve most of your problems
[http://ubuntuforums.org/showthread.php?t=174900](http://ubuntuforums.org/showthread.php?t=174900)

But I have a server that boots to the gdm login and just sits there, allowing logins via ssh and vnc if needs be. The overhead of running to gdm shouldn't hurt, and you have the benefit of gui if you need it

---

### Post by MountainX on 2008-03-20
> **Jose Catre-Vandis said:**
> Have a look here, should solve most of your problems
[http://ubuntuforums.org/showthread.php?t=174900](http://ubuntuforums.org/showthread.php?t=174900)
t

Excelllent. Thank you.

---

### Post by MountainX on 2008-03-24
I ended up installing the beta version of Hardy server and I'm really happy with it so far.

---

