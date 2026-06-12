---
title: "Tried Ubuntu Server for 1st Time.  No GUI?!"
date: 2010-09-29
forum: Server Platforms
---

### Post by BlackRoseBud on 2010-09-29
I tried Ubuntu Server for the first time today.  Using M$ server OSs are easy, so I figured Ubuntu would be easier.  I couldn't even figure out where the GUI was.  Does it not come with one?  Shall I go buy one of those thick books they used to use in the 80's and early 90's full of commands to input into my server installation.  Come on, it should come with a GUI! :mad:

---

### Post by Fafler on 2010-09-29
No, it comes with out GUI, but you can easily install one. You basically have two choices: Webmin, a webinterface that is able to control most server tasks. And the normal Ubuntu GUI.

Rad about how to install them here:
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)
If you choose Webmin, use this file instead: [http://www.webmin.com/download/deb/webmin-current.deb](http://www.webmin.com/download/deb/webmin-current.deb)

And yes, you can have both.

---

### Post by inoculator on 2010-09-29
Hello,

of course the server comes w/o GUI. What should it be good for?

Well, don't take me to serious, as I know Your experience very good -I am Nintendo-Admin, too ;-)

If You really want to implement the GUI, You can install it via APT:

```
sudo apt-get install ubuntu-desktop
```It will load about 450MB extracted to around 2.something GB.
After finilazing and reboot, You will be directly booted into the GUI.

Don't be angry about this. You don't need to buy expensive book. You only need the Ubuntu Forum and Docs and some more coffee.
It works for me up to now -thanks to the comunity.

br

Carsten

---

### Post by Grenage on 2010-09-29
> **BlackRoseBud said:**
> I tried Ubuntu Server for the first time today.  Using M$ server OSs are easy, so I figured Ubuntu would be easier.  I couldn't even figure out where the GUI was.  Does it not come with one?  Shall I go buy one of those thick books they used to use in the 80's and early 90's full of commands to input into my server installation.  Come on, it should come with a GUI! :mad:

No, a GUI is generally not required for a linux server.  A Linux 'server' with a GUI, is a desktop.

---

### Post by BlackRoseBud on 2010-09-29
Okay, I appreciate your patient responses.  Will set aside some time soon to figure it all out.

---

### Post by HermanAB on 2010-09-29
If you want a server with a GUI, just install regular Ubuntu.

The Linux 'server' distributions are meant for use in a data centre with racks full of machines, where having a GUI installed is quite useless, since the machines are managed remotely over SSH.  These machines don't have screens, keyboards, rodents and whatnot, so there is no point in installing all the pointy-clicky-crapware.

---

### Post by spynappels on 2010-09-30
+1 HermanAB

---

### Post by sikander3786 on 2010-09-30
> **inoculator said:**
> 

```
SUDO APT-GET install ubuntu-desktop
```



Linux is case sensitive my friend. It should have looked like this

```
sudo apt-get install ubuntu-desktop
```

;-)

---

### Post by dragos2 on 2010-09-30
Use this, it works and it is not bloated by all Ubuntu desktop components:

```

$ sudo apt-get install xorg-core gnome-core gdm # ubuntu-artwork

```

---

### Post by duindain on 2010-10-12
> **dragos2 said:**
> Use this, it works and it is not bloated by all Ubuntu desktop components:

```

$ sudo apt-get install xorg-core gnome-core gdm # ubuntu-artwork

```
E: Couldn't find package xorg-core
;(

---

### Post by Grenage on 2010-10-12
Isn't it xorg-common?

---

### Post by flodulv on 2010-10-12
is there any way to uninstall x (gnome) and vnc. I installed this, and i don't need this :)

---

### Post by mainerror on 2010-10-12
Not to sound like a troll but what is wrong with reading books? Is it considered being "out" nowadays?

I'd totally recommend buying books and reading the documentation and not using a GUI for a server.

---

### Post by arrrghhh on 2010-10-12
> **flodulv said:**
> is there any way to uninstall x (gnome) and vnc. I installed this, and i don't need this :)

Did you install everything with aptitude?  Much easier to purge with that tool.

If you installed with apt-get, you can remove all of the packages individually.

Otherwise, clean install :D

---

