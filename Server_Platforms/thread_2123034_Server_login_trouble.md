---
title: "Server login trouble"
date: 2013-03-06
forum: Server Platforms
---

### Post by jonessoda219 on 2013-03-06
Good evening,

I have installed ubuntu 12.10 server on my computer. I am very new to the server system and I am stuck on a screen and cannot get to the desktop of the server. I do not know what to do. Please try to help, I can provide further details if not needed. Pictures are below..

---

### Post by ranger12 on 2013-03-06
The server edition does not come with a desktop GUI. It uses a command line interface. You can install one but it is not recommended. For what reasons did you install the server edition for?

---

### Post by jonessoda219 on 2013-03-06
I installed the server edition for something like a vpn and also a file server. I do not have the server online as of now.

---

### Post by ibjsb4 on 2013-03-06
There are several light server GUIs you could install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by jonessoda219 on 2013-03-06
Is there any way to get to the desktop from this screen?

---

### Post by ibjsb4 on 2013-03-06
Looks like your in console, so yes you can install a desktop from there.  My simple (starting point) desktop:

```
sudo apt-get install -y lightdm gnome-terminal firefox synaptic && sudo apt-get install -y --no-install-recommends gnome-session-fallback nautilus
```

But you can go lighter than this, just got to figure out what you want.

---

### Post by jonessoda219 on 2013-03-07
Okay im going to try that. Im still at the command screen.. Does anyone know the commands to get the server to recognize the ethernet cable from my laptop?

---

### Post by ibjsb4 on 2013-03-07
> **jonessoda219 said:**
> Okay im going to try that. Im still at the command screen.. Does anyone know the commands to get the server to recognize the ethernet cable from my laptop?

.:confused:

That was done during the install process, unless you were not hooked up to the internet durning the install process.

---

