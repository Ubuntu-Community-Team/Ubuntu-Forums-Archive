---
title: "Server + X?"
date: 2009-05-21
forum: Server Platforms
---

### Post by iissmart on 2009-05-21
Hi,

I'd like to install Ubuntu Server, however I will need to run an application which only has a GUI interface (specifically, PS3 Media Server). I know I can forward X via ssh (I'll be doing it through Putty and Xming), but what are the minimum packages I need to install after installing Ubuntu Server to be able to run a GUI program? I don't need Gnome and am trying to avoid installing useless apps, I just need the very basics to be able to configure and run this program on a server installation.

---

### Post by hictio on 2009-05-21
> 
The absolute minimum for any graphical environment is X.org

Installing X.org
On Ubuntu Edgy (6.10), Feisty (7.04), and Gutsy (7.10), use the command:

sudo aptitude install xorg

On Ubuntu Dapper (6.06), use the command:

sudo aptitude install x-window-system-core

Starting X.org
This package gives you the framework for an X session, complete with a variety of drivers and configuration files. Installing xorg (or x-window-system-core) also triggers the self-configuration sequence, so when it finishes, your hardware should be ready to use, barring any errors or incompatibilities.

It's important to note that installing xorg or x-window-system-core really doesn't leave you with much. You can start X at this point with this command:

startx

but without a window manager and some software, you probably won't get much done.


Taken from here [Installation on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems) and another page on that regard [Modest Spec or Barebones Installation of Ubuntu](http://www.psychocats.net/ubuntu/minimal)

---

