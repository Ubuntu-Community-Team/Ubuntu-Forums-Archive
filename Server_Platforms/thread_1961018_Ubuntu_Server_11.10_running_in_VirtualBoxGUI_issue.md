---
title: "Ubuntu Server 11.10 running in VirtualBox/GUI issue"
date: 2012-04-18
forum: Server Platforms
---

### Post by taman29 on 2012-04-18
So I just installed ubuntu server 11.10 successfully in VirtualBox, and decided to install a gui. So I wanted a barebones gui so I ran
[COLOR=red]sudo apt-get install --no-install-recommends ubuntu-desktop[/COLOR]
[COLOR=red][COLOR=black]Rebooted the virtual machine, and the screen expands for a brief second as if it is trying to launch the gui, then returns to the command prompt screen, which no longer responds to keyboard commands. I tweaked the virtual machine settings by giving it additional video ram, but to no avail. Any ideas? At the very least how can I get back to using the normal command line interface?[/COLOR][/COLOR]

---

### Post by arrrghhh on 2012-04-18
> **taman29 said:**
> So I just installed ubuntu server 11.10 successfully in VirtualBox, and decided to install a gui. So I wanted a barebones gui so I ran
[COLOR=red]sudo apt-get install --no-install-recommends ubuntu-desktop[/COLOR]
[COLOR=red][COLOR=black]Rebooted the virtual machine, and the screen expands for a brief second as if it is trying to launch the gui, then returns to the command prompt screen, which no longer responds to keyboard commands. I tweaked the virtual machine settings by giving it additional video ram, but to no avail. Any ideas? At the very least how can I get back to using the normal command line interface?[/COLOR][/COLOR]

It no longer responds at all to any commands?  Did you take a snapshot of the VM before you made that change?

Honestly if you want a GUI, install Ubuntu Desktop - not the metapackage ubuntu-desktop, the full blown install for Ubuntu Desktop.  There's really no point in installing the server edition if you want a GUI - will just create a lot more work and A LOT more headache down the road.

---

### Post by taman29 on 2012-04-18
Unfortunately I did not take a snapshot.  The whole point in my experimenting with Ubuntu server was really just to try Owncloud. I guess I can just do a reinstall.

---

### Post by arrrghhh on 2012-04-18
> **taman29 said:**
> Unfortunately I did not take a snapshot.  The whole point in my experimenting with Ubuntu server was really just to try Owncloud. I guess I can just do a reinstall.

You'll save yourself a lot of time and headache by just reinstalling.  Go for Ubuntu Desktop this time ;).

---

### Post by haqking on 2012-04-18
you will also need guest additions installed for enhanced graphic support.

And if you want a barebones GUI i would go for something like xfce or lxde for a lighter alternative to Ubunt-Desktop (Gnome and Unity)

Cheers

---

### Post by jerome1232 on 2012-04-18
> **haqking said:**
> 
And if you want a barebones GUI i would go for something like xfce or lxde for a lighter alternative to Ubunt-Desktop (Gnome and Unity)


I'm seconding this, you can install lubuntu-core for a pretty light weight hassle free gui. Have you considered using a web based gui like webmin?

---

### Post by taman29 on 2012-04-18
Thanks for all the great suggestions!  I think I may try webadmin.

---

### Post by taman29 on 2012-04-18
I tried out webmin and love it.  And as an added bonus, I was able to get my owncloud up and running!  Not bad for a linux noob :D

---

### Post by jerome1232 on 2012-04-18
One caveat to webmin, just as with ssh or anything else that allows remote administration, is that you need to make sure you know how to secure it before you think about exposing it to the Internet.

This is all I could find with a quick on webmin's site

[http://doxfer.webmin.com/Webmin/SecuringWebmin](http://doxfer.webmin.com/Webmin/SecuringWebmin)

---

