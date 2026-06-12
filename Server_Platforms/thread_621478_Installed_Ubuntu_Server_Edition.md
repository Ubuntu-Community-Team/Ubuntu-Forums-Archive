---
title: "Installed Ubuntu Server Edition :/"
date: 2007-11-23
forum: Server Platforms
---

### Post by DaveTurnbull on 2007-11-23
I was expecting to be greeted with a GUI, but all I got was a command line interface - how do I get a GUI?

---

### Post by obrient on 2007-11-23
With the server edition you won't get the GUI. However I believe that if you do

```
sudo apt-get install X11 gdm gnome
```

you should that apt will add the dependencies for you. I have done this once when uninstalling something and believe that this fixed it.

---

### Post by HermanAB on 2007-11-23
The server edition is for use in a data centre.

If you have a 'server' with a screen and keyboard attached, then you should rather install Xubuntu.  It comes with a light weight desktop that doesn't waste resources.

Cheers,

Herman

---

### Post by DaveTurnbull on 2007-11-23
> **HermanAB said:**
> The server edition is for use in a data centre.

If you have a 'server' with a screen and keyboard attached, then you should rather install Xubuntu.  It comes with a light weight desktop that doesn't waste resources.

Cheers,

Herman

Ah, thanks for the response. :)

---

### Post by WIGGMPk on 2007-11-23
DavTurnbill:

If you want to setup a server, or just tool around. I can assure you if you have the desire to learn about a Unix/Linux based operating system then keeping the command-line only approch will definatly teach you how things operate.

I would recommend to anyone wanting to learn how to Unix/Linux really WORKS to use a non GUI interface. It helps to have another machine as well (like a laptop).

But getting a GUI is even simpiler then that:

```
sudo apt-get install ubuntu-desktop
```

That will install all the packages that are on Ubuntu Desktop version. If your looking for a light weight GUI to run a server. I believe there's an "Ubuntu-Lite" project that appeals to a user freindly Ubuntu Server setup. Dont have the link off the top of my head but its in these forums somewhere and im sure google/blackle.com will turn up some results.

Hope this info helps

---

### Post by cerebellum on 2007-11-23
> **WGGMk said:**
> DavTurnbill:
If you want to setup a server, or just tool around. I can assure you if you have the desire to learn about a Unix/Linux based operating system then keeping the command-line only approch will definatly teach you how things operate.

I would recommend to anyone wanting to learn how to Unix/Linux really WORKS to use a non GUI interface. It helps to have another machine as well (like a laptop).


Can everything be done in GUI (the default GNOME) as it is in command line?

And if I am to install the ubuntu-dekstop, how much resources can it be? Say I'm running a file server and web server (LAMP) in a network with 10 computers accessing the server.

Thnx.

---

### Post by WIGGMPk on 2007-11-23
> Can everything be done in GUI (the default GNOME) as it is in command line?

With the involvment that this community has, and the fact that this is an OpenSource love fest at Ubuntu. There prolly is an application for a GUI to do just about everything. Depending on what it is.

For instance, adding and removing users/groups can easily be done in the desktop version. But I still find it a lot faster to just pop open a terminal and add the user directly. Its a matter of taste and preference really.

Basically speaking, the server edition is tailored for, well, being a server. Mostly in the IT field (non Windows based) you wont find a server (that serves a large base) with a GUI. Its not nessecary and it bloats the operating system and slows down performance.

> And if I am to install the ubuntu-dekstop, how much resources can it be? Say I'm running a file server and web server (LAMP) in a network with 10 computers accessing the server.

This is also going to be an ambigious answer. It depends on different factor's. Computer hardware spec's, data being served, connection speed, and ultimatly how much work your willing to put into the server.

But a general answer, if you have a decient machine that can handle the recommended spec's for the Desktop version then you shouldnt have a problem with what your trying to do.


But I encourage you that if you choose the route of a GUI to try doing things with the command line (terminal) first, and resort to a GUI app if you cant figure things out.


Plus, you have an excellent resource.... THESE FORUMS.

There is so much documentation in this community (Ubuntu) that sometimes you think your head's gonna explode. Good luck to you sir, and dont hesitate to ask questions. But one of the most secretive tools on the forums is the 'search' button lol.



Knowledge is power.

---

### Post by wolfear on 2007-11-23
> And if I am to install the ubuntu-dekstop, how much resources can it be? Say I'm running a file server and web server (LAMP) in a network with 10 computers accessing the server.
I think that would mostly depend on the amount of traffic, what services you are running, and what your users are doing.

Personally, if you are worried about resources, I would say keep the server clean (without the GUI) and install Webmin if you really need a visual interface.

But I agree with the others: If you are going to admin a server, getting comforatble with the command line is essential.

I use a combination of Webmin and SSH for just about everything on my server.

---

### Post by herbie_popnecker on 2007-11-24
```

sudo apt-get install ubuntu-desktop
```

Is the correct way.... I didn't read down this thread and got really messed up trying to install gnome.
Fortunately it only took 15 mins to redo the server install and then apt-get ubuntu-desktop worked flawlessly....

---

### Post by koenn on 2007-11-24
> **herbie_popnecker said:**
> ```

sudo apt-get install ubuntu-desktop
```

Is the correct way.... I didn't read down this thread and got really messed up trying to install gnome.
Fortunately it only took 15 mins to redo the server install and then apt-get ubuntu-desktop worked flawlessly....
apt-get install ubuntu desktop installs all packages ubuntu-desktop depends on  - that's everything in a standard ubuntu desktop : openoffice, screensavers, gimp, firefox, ...
(try 'apt-cache depends ubuntu-desktop' to get a complete list)
I don't think that's suitable for a server. 

for a minimal GUI, you need xorg, the x window system, and a window manager (fluxbox, xfce4, ..) and possibly a GUI login manager a.k.a. a desktop manager (eg xdm), and probably at least an X terminal emulator (eg xterm)

## some of these require 'universe'
## some package names may have changed in newer releases 
```

apt-get install xorg x-window-system-core xterm xdm  fluxbox

```

Then, you just add any GUI application you need.

If you want a gnome environment, you'd 
- use gdm in stead of xdm, and 
- replace fluxbox or xfce4 window manager by some gnome components such as gnome-panel, gnome-menus, gnome-session and add metacity (window manager) 

this will pull in additional gnome components to satisfy dependencies.

---

### Post by cerebellum on 2007-11-25
> **WGGMk said:**
> 
Basically speaking, the server edition is tailored for, well, being a server. Mostly in the IT field (non Windows based) you wont find a server (that serves a large base) with a GUI. Its not nessecary and it bloats the operating system and slows down performance.

...

But I encourage you that if you choose the route of a GUI to try doing things with the command line (terminal) first, and resort to a GUI app if you cant figure things out.


I'm planning this out coz the admin is not a power user. I'm proposing this open source solution to a church administration office with [www.churchdb.org](www.churchdb.org) and centralized file sharing host for documents, spreadsheets, pictures, videos, and other archiving.

The admin (the guy who maintain users) are just a user and I can't force him to learn commands on the terminal.

> **wolfear said:**
> 
Personally, if you are worried about resources, I would say keep the server clean (without the GUI) and install Webmin if you really need a visual interface.


Webmin sounds interesting, but if i'm installing the GUI, how do i start the server in command line by default and manually get into GUI when needed? Is that a feasible solution in this condition?

Please advice.

---

### Post by WIGGMPk on 2007-11-25
Webmin is a program that allows you to have complete control over the server via [https://,](https://,) which can aid you in configuring the server.

But this is usually just a lazy tool for admins, or a remote tool for an ever tinkering mind. It allows you to access it from anywhere in the world with internet basically.

The drawback of this solution is there would still be SOME command line driven work that would need to be done just to setup the webmin server. Given the fact that this is a not for profit organization installing a server edition OS with no graphical aid with an none Linux (debian based) savy administrator, I would say install the desktop verion.

So, you need to sit down with the admin and lay out his options for proposing this kind of solution. Server edition WILL require some light work and prolly some reading. As far as the desktop edition is concerned there are resources on these forums for setting up prolly any server you need easily because of the aid of the GUI.

Decide what you need.... Are there more computers in the church/organization your serving, that you will need to server DHCP?. Do they need a master domain with an authentication backend to have client logon's. ? Do I need this server for hosting web pages? etc....

Take the answer's to those questions and find your solution. Ubuntu is a very versatile system and can definatly fit any need you would have for it without a doubt. Its a matter of a lot of things. When does it need to be setup? Who will set it up/ Do they know how? yadda yadda.


Hope im sounding right. Its late.




EDIT: Forgot to mention..... Once the packages are configured for the server they will automatically start once the server is powered on. Unless of course you change it to not automatically start, which usually you wont and a server is ment to be kept on.

---

### Post by wolfear on 2007-11-27
> But this is usually just a lazy tool for admins, or a remote tool for an ever tinkering mind. It allows you to access it from anywhere in the world with internet basically.

The drawback of this solution is there would still be SOME command line driven work that would need to be done just to setup the webmin server. 
Yup...have to edit the sources.list and use apt-get. Might be too much for us lazy admins to handle.

---

### Post by stormcrowe on 2007-11-27
I am a total noob at this so this is probably an easy answer but when I type all of those strings into the command line I get a whole lot of nothing...

anytime I put in something like "sudo apt-get install (whatever)"   It comes back with..

"couldnt find package (whatever)"

I am kind of at a loss what to do. Like I said I am a TOTAL linux noob.  Any links in the right direction would be fine as well. Thanks for the patience.

By the way I just trying to set up a basic file server for a LAN.

---

### Post by crouton on 2007-11-27
try 'sudo apt-cache search <pkgname>' where pkgname is the package you want to install.

If you don't know what the package name is, you can go to packages.ubuntu.com with your web-browser and do a search there.  It's a bit more userfriendly if you aren't used to the APT system.

---

### Post by WIGGMPk on 2007-11-28
> **wolfear said:**
> Yup...have to edit the sources.list and use apt-get. Might be too much for us lazy admins to handle.

I ment no disrespect by the comment. The point I was trying to hit is, you learn more by doing it the way its been done for many years. Webmin is a very nice program to help administration but can be intimidating to someone that doesnt know what exactly their looking at.

I apologize for any offense.

---

### Post by wolfear on 2007-11-29
> **WGGMk said:**
> I ment no disrespect by the comment. The point I was trying to hit is, you learn more by doing it the way its been done for many years. Webmin is a very nice program to help administration but can be intimidating to someone that doesnt know what exactly their looking at.

I apologize for any offense.
No worries.

---

### Post by DraK on 2007-12-04
I did  "sudo apt-get install xubuntu-desktop" , everything installed fine but on rebooting still no gui. Have i missed something out?

advice please!

---

### Post by wolfear on 2007-12-05
I am not 100% certain, but I think after you log in on the command line, you should be able to type "startx" to start the desktop.

---

### Post by crouton on 2007-12-05
You may need to install 'gdm' as well, although that should have been in xubuntu-desktop....

---

