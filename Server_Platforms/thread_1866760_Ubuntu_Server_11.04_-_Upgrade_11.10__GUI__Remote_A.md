---
title: "Ubuntu Server 11.04 - Upgrade 11.10 / GUI / Remote Access"
date: 2011-10-21
forum: Server Platforms
---

### Post by AviAndroid on 2011-10-21
Goal

    Upgrade to Ubuntu Server 11.10
    Install GUI
    Install remote access

So far I have upgraded from Ubuntu Server 11.04 to Ubuntu Server 11.10

    do-release-upgrade

Then I did a minimal installation of the GUI desktop

    apt-get install --no-install-recommends ubuntu-desktop

Next I would like to remotely access the GUI desktop of this server

This is where I have stalled out for the moment and humbly ask for your assistance on how to proceed from here.  I would like to, as you can see from above, remotely access the GUI desktop of this server. Please advise if I have not proceeded correctly in my steps above and missed a crucial step in this equation.  I will say that this server is more than capable of handling such a task as well as its connection and if need be it would be no problem to reinstall the operating system and start over.

---

### Post by newbie-user on 2011-10-21
You'll likely need some VNC client on the remote computer that will connect to the server.  Also, you'll need Vino installed on the server if you don't have it already.  Then from the VNC client, you can remote into the server's desktop environment.

---

### Post by sandrodz on 2011-10-22
I was doing the same thing, but I found access to desktop utterly useless. SSH is more than enough for any administration needs. Why would you install gui?

---

### Post by damo12 on 2011-10-22
Have you tried using Webmin ([http://www.webmin.com/]("http://www.webmin.com/"))?

It is fantastic and is extremely easy to use and manage a server from anywhere in the world if you forward the port through your router and use a DNS service like DynDNS ([http://dyn.com/dns/dyndns-free/]("http://dyn.com/dns/dyndns-free/")).

There's an excellent guide on how to install and configure Webmin at [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/]("http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/").  It's designed for Ubuntu 10.04 but I'm sure it will work just as well on 11.

For future use, you might also find it better to stick to the LTS releases of Ubuntu server the next one being 12.04 (ie the next release).

---

### Post by haqking on 2011-10-22
> **AviAndroid said:**
> Goal

    Upgrade to Ubuntu Server 11.10
    Install GUI
    Install remote access

So far I have upgraded from Ubuntu Server 11.04 to Ubuntu Server 11.10

    do-release-upgrade

Then I did a minimal installation of the GUI desktop

    apt-get install --no-install-recommends ubuntu-desktop

Next I would like to remotely access the GUI desktop of this server

This is where I have stalled out for the moment and humbly ask for your assistance on how to proceed from here.  I would like to, as you can see from above, remotely access the GUI desktop of this server. Please advise if I have not proceeded correctly in my steps above and missed a crucial step in this equation.  I will say that this server is more than capable of handling such a task as well as its connection and if need be it would be no problem to reinstall the operating system and start over.

a GUI on a server is not recommended.

For admin use SSH and if you use it with -X

ssh -X username@host

Then you can forward X apps to your local X server.

If you really a remote desktop function then you can VNC over a secure ssh tunnel.

---

### Post by koenn on 2011-10-22
I'm with the "use ssh" crowd - server mgmnt is a mere matter of a handful of commands, and editing text files. You really need an entire desktop to edit a text file ?  

2nd choice would be running ssh -X to pull GUIs from the server to your desktop.

a neat extension to that is this : run gnome-panel over ssh -X :
```

ssh -X username@host
gnome-panel

```
this runs the server's gnome-panel on your desktop, and the programs you start from its menus will be the programs on the server.

It can be a bit slowish on a slow network, but it works (or it did the last time i tried)


You can also look at xdmcp  - [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp)

---

### Post by Vegan on 2011-10-22
I find it problematic to do a disto upgrade, seems to be all kinds of file system crashed subsequent

better is a new vm with the new release and then migrate over to it

---

### Post by AviAndroid on 2011-10-22
Thank you all for your replies.  I appreciate your take on this project.  It looks like VNC e.g. Vino and SSH -X are the two most popular methods for performing remote access.  Can you suggest a list of active software projects that would allow me to perform this remote access function and a current guide to follow maybe starting with Ubuntu Server 11.04 to Ubuntu Server 11.10 as I am still relatively new to Ubuntu Server and trying to transition from a Microsoft Windows dominated world.  

newbie-user - You suggested using Vino.  Can you point me in the direction of a good how to guide for installing, configuring, and using on Ubuntu Server 11.04 to 11.10.

damo12 - Thank you for suggesting Webmin and providing a link to that excellent guide.  I believe I will also have to integrate this into the server project as well.

koenn/haqking - I agree with both you concerning SSH.  I like the idea of being able to have essentially the best of both worlds.  Is there a guide for Ubuntu Server 11.04 to 11.10?

---

### Post by haqking on 2011-10-23
> **AviAndroid said:**
> .  Is there a guide for Ubuntu Server 11.04 to 11.10?

[https://help.ubuntu.com/](https://help.ubuntu.com/)

then click on version and then choose server guide, ssh is covered in each one.

Good luck

---

### Post by newbie-user on 2011-10-23
> **AviAndroid said:**
> Thank you all for your replies.  I appreciate your take on this project.  It looks like VNC e.g. Vino and SSH -X are the two most popular methods for performing remote access.  Can you suggest a list of active software projects that would allow me to perform this remote access function and a current guide to follow maybe starting with Ubuntu Server 11.04 to Ubuntu Server 11.10 as I am still relatively new to Ubuntu Server and trying to transition from a Microsoft Windows dominated world.  

newbie-user - You suggested using Vino.  Can you point me in the direction of a good how to guide for installing, configuring, and using on Ubuntu Server 11.04 to 11.10.

damo12 - Thank you for suggesting Webmin and providing a link to that excellent guide.  I believe I will also have to integrate this into the server project as well.

koenn/haqking - I agree with both you concerning SSH.  I like the idea of being able to have essentially the best of both worlds.  Is there a guide for Ubuntu Server 11.04 to 11.10?

You can install vino using "sudo apt-get install vino" in the terminal.  Then in the gui, just access "remote desktop" from the menu, check the boxes for allowing others to view and control your desktop, then set a password.  After that, you're all set.

---

### Post by AviAndroid on 2011-10-23
I decided to start out using VNC because I am somewhat familiar with that and have used it in the past to troubleshoot customer support issues involving the Windows operating system via the GUI of both operating systems, but never from the CLI like this.  I wish I had better news to report but I can't for the life of me figure out how to get VNC to work via the CLI.  I really don't want to give up and crawl back to Windows.  I installed Vino and tried configuring it, but can't seem to get anything to appear on my personal computer.  Can you guys explain in full detail how this is accomplished from start to finish.  There is just so much conflicting and outdated information online it is hard to decipher what works from what doesn't/didn't.

---

### Post by adym333 on 2012-03-11
sudo apt-get install --no-install-recommends ubuntu-desktop

after entering above comnd got all the installation done but aftr running whole processes ............ still not able to get GUI for ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

help required .....!!!.....:(:(

---

### Post by volkswagner on 2012-03-11
> **adym333 said:**
> [sudo apt-get install --no-install-recommends ubuntu-desktop

after entering above comnd got all the installation done but aftr running whole processes ............ still not able to get GUI for ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

help required .....!!!.....:(:(



You should probably start a new thread in the future rather than dig up an old, thread marked solved.

EDIT: I see you already have a thread... Please don't double post.

Do you get a login prompt at all?

If so login and run:

```
startx
```

Since it is a server install X may not be configured to start automatically.

---

### Post by Iowan on 2012-03-11
Thread closed.
> Do not cross post, or post the same thing in multiple locations.

---

