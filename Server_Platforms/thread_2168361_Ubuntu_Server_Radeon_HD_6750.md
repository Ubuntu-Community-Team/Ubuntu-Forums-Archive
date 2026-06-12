---
title: "Ubuntu Server Radeon HD 6750"
date: 2013-08-17
forum: Server Platforms
---

### Post by Neverwill on 2013-08-17
Hello everyone, I am attempting to install the drivers for an ATI Radeon HD 6750 graphics card into my Ubuntu Server 13.04.. I have a Minecraft server, and I'm hoping that installing a graphics card, will speed up the server chunk/block loading at least a little bit...
 I keep running into a error, which is x-server.. and from what I remember x-server is the GUI.. which... is not what I want, seeing as it is a server that I connect to via putty.

[COLOR=#ff0000]Here is the Error..

[/COLOR][COLOR=#ff0000]minecraft@server:/$ sudo sh amd-driver-installer-catalyst-13-4-x86.x86_64.run[/COLOR]
[COLOR=#ff0000]Created directory fglrx-install.CMle5q[/COLOR]
[COLOR=#ff0000]Verifying archive integrity... All good.[/COLOR]
[COLOR=#ff0000]Uncompressing AMD Catalyst(TM) Proprietary Driver-12.104....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................[/COLOR]
[COLOR=#ff0000]=====================================================================[/COLOR]
[COLOR=#ff0000] AMD Catalyst(TM) Proprietary Driver Installer/Packager[/COLOR]
[COLOR=#ff0000]=====================================================================[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]error: X Server version cannot be detected. (default:v2:x86_64:lib::none:3.8.0-27-generic:)[/COLOR]
[COLOR=#ff0000]Installation will not proceed.[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Removing temporary directory: fglrx-install.CMle5q[/COLOR]



So, my question is, will my graphics card work up to peak performance without the drivers? I'm assuming not.
And, how does someone install drivers on a Ubuntu server?

I'm fairly new at linux.. So apologies about the noobish question.

---

### Post by Cheesemill on 2013-08-18
Welcome to the forums Nerverwill.

First of all, what makes you think that installing a graphics card in your server will improve the performance of the Minecraft server at all?

Minecraft server is limited by RAM and disk I/O and installing a graphics card won't do anything to help this. To increase performance you should look at things like allocating more RAM, moving the world to an SSD or RAM disk, and using Oracle Java if you aren't already.

---

