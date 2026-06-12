---
title: "how full is disc"
date: 2009-05-08
forum: Server Platforms
---

### Post by andyrowe on 2009-05-08
Sorry... linux server noob. How do I tell how full my disc is? Ubuntu server 9
How about graphic directory viewer? do I need GUI / window manager to use internet browser? Should I load Gnome? Basic network monitoring tools for a new linux user?
MS system admin for 10+ years but just getting my feet wet with Linux

---

### Post by milton1 on 2009-05-08
df -h will give you a run-down of filesystem usage.

Any graphic tools, directory viewers, browsers, etc, will need X11 running. The simplest way to do this is running gnome or kde. If you pick kde, I would stick with the old 3.5 version for any kind of stable system. 4.2 is pretty, but not ready for prime time just yet.

There are network management tools built into the GUI systems, and I'm sure there are terminal versions as well, but I am not familiar with them.

---

### Post by andyrowe on 2009-05-08
thank you sir
df -h told me what I needed to know. I had gnome on ubuntu desktop lab box. Liked it, wouldn't mind having it on server. Don't want to mess with unstable kde (another gui i'm guessing) Sorry for noob questions. How to install gnome on already running ubuntu server. Will it run on start up? What is X11? window manager?
Happy with ubuntu server so far but don't need any potential problems. Server in production already. Replaced $1500 NAS with $240 ubuntu server.... nice!
thanks for the help
andy <---- MS guy up until now

---

### Post by Alekz_ on 2009-05-08
If you have an internet connection you can use apt-get like this:

```
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```

It's the easier way to install a X environment with gnome.

PS: Forgot about gdm

One more command:
```
apt-get install gdm
```

---

### Post by milton1 on 2009-05-08
Installing gnome will be very easy.

```
sudo apt-get update && sudo apt-get install ubuntu-desktop 
```

This will install all the graphical goodies you want. Rebooting should bring up the GUI, or you can start without the reboot with this:

```
 sudo /etc/init.d/gdm restart 
```

---

### Post by andyrowe on 2009-05-08
OK.. thank you both... but ah.... you're both getting a little ahead of me.
alekz_ I know apt-get will install new apps. The command you gave, it will find stuff on the internet? Machine has internet access, gateway configured. Is there a gnome specifically for server? and what is gdm?
milton1 I know apt-get update makes all the new apps available (think I ran it already) but what does the && do? string commands together?
generally when you guys post code, I type in exactly what you put?
thanks so much
EDIT: oh and did I mention this server is already in prodution. any of this stuff will apsolutely positivly not mess up the machine right. Because I'll skip it for now and experiment on a lab box

---

### Post by milton1 on 2009-05-08
Both of our approaches will work. You are correct, the && just strings commands together. The difference between the two codes we posted is that Alexz's code will install just a base gnome desktop set, and mine will install the entire gnome-based ubuntu desktop, with all the bells and whistles, office apps, plugins, browsers, etc. Both should be safe for your machine, but as a computing professional, I'm sure you already know that ANY system upgrading runs the risk of breaking something, so backup anything you absolutely can't lose.

---

### Post by andyrowe on 2009-05-08
> **milton1 said:**
> but as a computing professional, I'm sure you already know that ANY system upgrading runs the risk of breaking something
Thanks milton
oh yeah I know all to well... but anyhow, this is a storage server used to store... you guessed it backups!
thanks again guys.

---

### Post by milton1 on 2009-05-08
> **andyrowe said:**
> Thanks milton
oh yeah I know all to well... but anyhow, this is a storage server used to store... you guessed it backups!
thanks again guys.

You are welcome.  :)

Good luck learning the joy that is linux. If you want a bit more info on tuning the network interface for this machine, try this:
```
 man ifconfig 
```

---

