---
title: "Needing a desktop/server setup"
date: 2011-05-19
forum: Server Platforms
---

### Post by Kivech on 2011-05-19
Gents,

I have a nice challenge:

Me and my wife are both freelancers who work at home. We have a limited budget (say hello to the global financial crisis) but need a solid home/small business system set up at home.

I have been trying out various combinations, but am undecided what would be best for our needs. Hence the reason I came here to ask you guys (the more experienced ones) for advice.

I have a PC (Asus P5Q Pro mobo, 4Gb mem, 3 SATA disks of 250Gb Core2 dual core processor).
I set up the first two disks as software raid1 and the third I use for backup.
My wife has some outdated laptop (I refuse to work with it :P), and we both are hooked up to the net through a router/modem.

We need printer sharing (printer hooked up to my PC), and I will be running OpenERP with PostgreSQL and a web development environment on my PC (Drupal environment).
Next to that I need the common desktop applications, but for OpenERP I need Thunderbird as a mail client and OpenOffice for office software.
My wife runs Windows XP on her laptop.

On my PC I need:
LAMP server
PostgreSQL server
OpenERP server/client/web client
Cups for printing
samba for printer/file sharing with my wife's laptop
various web development software

As a desktop environment I chose Xubuntu, because it is lighter than Gnome, and more stable than KDE. Also the fact that it comes with Firefox and Thunderbird as default internet and mail clients makes that an appealing choice to me. And then, it is more customizible than gnome, which I consider to be a big plus for any desktop environment.

My question is: how would you set up ubuntu around this?

Would it be ubuntu-server as a basis and start from there, adding the xubuntu (or maybe even just the xfce desktop) and take it from there?
Or would it make more sense to part with Xubuntu and add the needed server components?

I tried both, but find (dis)advantages to both setups. eg. The server install software installs a boot screen that allows you to boot a safe/rescue environment, which I think is fundamental when you are running a production environment with server services. If I install Xubuntu, I do not have that. Honestly, I have no idea if that would be something I could add manually later on in an easy fashion or not.
However, when I install ubuntu-server and add the xubuntu desktop later on, the system has all kinds of rights issues (package manager refuses any user/password combination), etc.

And what about the desktop environment? Does xfce make sense for the kind of needs we have, or would it be better to go for an even lighter desktop like Fluxbox or Openbox?
Mind you, I am not afraid of the command prompt, but I certainly am not a techie in Linux, so I appreciate the GUI very much when it comes to administration tasks.

Also, considering the nature of our work, the more hassle free a setup is, the better.

All suggestions are welcome. :)

---

### Post by Lars Noodén on 2011-05-19
I would start even lower and use the alternate install disk to set up a "command line" system.  From there I would add only what you need for OpenERP, then add the meta package xubuntu-desktop.

---

