---
title: "What about Server edition?"
date: 2006-04-26
forum: Server Platforms
---

### Post by borzoi on 2006-04-26
Good morning to everybody,
it seems to me Ubuntu-Server is free just like desktop edition.
But, in what differ from desktop version?
Are there value-added services for Server distro?

---

### Post by tikal26 on 2006-04-26
AS far as I know they have a different kernel  optimized for server, but besides that I don't know

---

### Post by imagine on 2006-04-26
The server and the desktop editions share the same repositories.
The differences are:
- If you pick the server installation no graphical user interface (X-Server, Gnome, etc) is installed.
- For Ubuntu 6.06 the server packages will have five years of support, whereas the desktop packages only have three years.
- A differently configured kernel is installed.

---

### Post by breezyfox on 2006-04-26
[QUOTE=imagine]
- If you pick the server installation no graphical user interface (X-Server, Gnome, etc) is installed.
[/QUOTE]

Hi
I have downloaded dapper beta live cd and i could't find  any options to install server through that or there is  any other procedure to install server.

your help will greatly be appreciated.

bz

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=tikal26]AS far as I know they have a different kernel  optimized for server, but besides that I don't know[/QUOTE]Nope. The only difference is what is on the CDs.

---

### Post by warpforge on 2006-04-27
[QUOTE=breezyfox]Hi
I have downloaded dapper beta live cd and i could't find  any options to install server through that or there is  any other procedure to install server.

your help will greatly be appreciated.

bz[/QUOTE]
You need to use the "INSTALL" only version ISO.

---

### Post by az on 2006-04-27
[QUOTE=LordHunter317]Nope. The only difference is what is on the CDs.[/QUOTE]
To be more specific, Dapper will have a server release which will include optimised kernels and a turn-key LAMP installer.

The Breezy release includes a server option in the installer which installs *less* software, since you don't really want to be running desktop applications (or even a graphical environment) on a server.

---

### Post by az on 2006-04-27
[QUOTE=borzoi]Good morning to everybody,
it seems to me Ubuntu-Server is free just like desktop edition.?[/QUOTE]
It is all GPLed software.  That means that it is not someone's property, but *everybody's* property.  It is free-libre software.


[QUOTE=borzoi]
But, in what differ from desktop version?
Are there value-added services for Server distro?[/QUOTE]

"Value-added" is a term used by people who sell you software, who try to make you beleive you are getting something for nothing.

All the applications you would need are in the repositories.  You can install any or all of the server packages in your regular desktop installation, if you want.

It is probably a lot safer to just install a server without including all the desktop software, which is why the installer gives you the option to do that.

---

### Post by az on 2006-04-27
[QUOTE=breezyfox]Hi
I have downloaded dapper beta live cd and i could't find  any options to install server through that or there is  any other procedure to install server.

your help will greatly be appreciated.

bz[/QUOTE]

Ubuntu can be installed via the installer cd or (in Dapper) using espresso from the live cd.  The espresso installer copies the live cd back to your hard drive.  You really don't get the option of picking and chosing the software you get.

If you want to install anything other than the default desktop, use the "install" cd, as mentioned.

---

