---
title: "Server vs Desktop for a non-experienced user?"
date: 2011-04-28
forum: Server Platforms
---

### Post by Espionage724 on 2011-04-28
I host 2 server computers in my home. I host a TeamSpeak 3 server, a Minecraft Server, and an Unreal Tournament GotY server. All of which have Linux binaries (except maybe UT, but thats not a concern)

These computers would probably have a keyboard/mouse and screen hooked up to them for initial install and setup, but I plan on having these machines sit unattended, and administrated on LAN via a Windows machine (or Ubuntu, if 11.04 works out nicely) (I'm thinking RDC would work for remote control).

From my understanding, Ubuntu Server uses no GUI, and it's all terminal based. If this is true, then I don't believe I could use this (I'm not that skilled with linux). However I would imagine that a apt-get install command could install a desktop gui (gnome, etc), but if I would need to do this, wouldn't a Desktop edition work best then?

---

### Post by lisati on 2011-04-28
The good news is that you have options. One option is to install the server edition and add a gui: webmin is a browser-based interface you can access from another machine.

---

### Post by Espionage724 on 2011-04-28
> **lisati said:**
> The good news is that you have options. One option is to install the server edition and add a gui: webmin is a browser-based interface you can access from another machine.

Hmm, never heard of webmin but I will check it out.

But something I just thought of, is there some way I could maybe, have a Desktop GUI on another computer, and control my server with that?

Might be a far out there idea, but it would be interesting :p

---

### Post by lisati on 2011-04-28
It is possible to install the server edition and add the regular desktop GUI to it with
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Espionage724 on 2011-04-28
> **lisati said:**
> It is possible to install the server edition and add the regular desktop GUI to it with
```
sudo apt-get install ubuntu-desktop
```

If I install the GUI, would I be able to basically disable it when I don't need it? Because wouldn't the GUI basically be taking more resources from the system then needed? And if I can't disable it, would a Desktop OS be better?

---

### Post by spynappels on 2011-04-28
What will you need to do by way of administering? Is it just stopping and starting services? I'm sorry, but I have no knowledge of gameservers at all.

Running a full blown desktop is probably not the best use of system resources.

Webmin is a good way of managing services but if you need to run GUI programs on the server, you could look at installing only an Xserver and use X forwarding over an SSH connection, rather like your second post suggests. This allows the program to run on the server, but the GUI to be rendered on a different (client) computer.

---

### Post by Espionage724 on 2011-04-28
Well pretty much the only things I would need to do is:

Minecraft:
- Install Java
- download a .jar and put it into a folder
- run it

TeamSpeak 3 though I believe is a similar process:
- Download it
- Extract it somewhere
- run it

This probably seems like no problem at all, but will I only have access to 1 terminal at a time on Server? Like can I have multiple terminal "tabs" similar to the ones in Desktop?

---

### Post by spynappels on 2011-04-28
You can have as many SSH connections to the same server as you like, and if you use Terminal on a Linux system you can have several tabs open and each tab connected to the same server if you want.

Although from what you describe, you should be able to do all the tasks you say using Webmin and some CLI through SSH.

---

### Post by Holdolin on 2011-04-28
> **Espionage724 said:**
> Well pretty much the only things I would need to do is:

Minecraft:
- Install Java
- download a .jar and put it into a folder
- run it

TeamSpeak 3 though I believe is a similar process:
- Download it
- Extract it somewhere
- run it

This probably seems like no problem at all, but will I only have access to 1 terminal at a time on Server? Like can I have multiple terminal "tabs" similar to the ones in Desktop?

You have 2 options.  If you're sitting in front of your server, you can have multiple "tabs" running, using the alt+F2, 3 and so on.  If you are remoting in, you can make multiple ssh connections.  I'm new to Ubuntu Server, but I hope this helps a bit  :)

---

### Post by msandoy on 2011-04-28
I run Teamspeak 3 on my server, and I have been running UT dedicated servers under linux some years back. This is not a problem. I do not know about Minecraft dedicated servers, but hopefully there are a linux port of them. Game servers like these are not resource hungry, and can be run on low end servers, as long as you run the dedicated mode. If I were you, I would set up a default ubuntu server, read up on a program called screen, run each of those programs in separate screen sessions via ssh. When you log out, the screen sessions continue to run in the background.

No need to clutter the clean install of the server with a desktop GUI.

---

### Post by CharlesA on 2011-04-28
> **msandoy said:**
> I run Teamspeak 3 on my server, and I have been running UT dedicated servers under linux some years back. This is not a problem. I do not know about Minecraft dedicated servers, but hopefully there are a linux port of them. Game servers like these are not resource hungry, and can be run on low end servers, as long as you run the dedicated mode. If I were you, I would set up a default ubuntu server, read up on a program called screen, run each of those programs in separate screen sessions via ssh. When you log out, the screen sessions continue to run in the background.

No need to clutter the clean install of the server with a desktop GUI.

+1. The first thing I thought of was screen.

You can also forward X over SSH if you need to access a graphical application and the host doesn't have a GUI installed (I use it for Virtualbox, and a few other things).

---

