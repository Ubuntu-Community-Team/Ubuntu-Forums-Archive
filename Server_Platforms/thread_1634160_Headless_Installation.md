---
title: "Headless Installation"
date: 2010-11-30
forum: Server Platforms
---

### Post by Powderking on 2010-11-30
Hi all

I'm planning to set up a server at home. It should act as a MythTV backend.
As I don't plan to install a graphics card I would like to install Ubuntu Server without a monitor.

Some time ago I have set up an Alix Board using this guide: [http://wiki.ubuntuusers.de/Alix](http://wiki.ubuntuusers.de/Alix)
It is described how to install Ubuntu Server with a serial terminal.

Unfortunately the mainboard I want to use (Intel Desktop Board DP55KG) doesn't have a serial port.

What do you think is the easiest way to install the OS?
Should I install a graphics card for the installation, set up SSH and remove the graphics card afterwards?
Or is it possible to install over PXE and log in over SSH to somehow install Ubuntu Server?
What other possibilities do I have?

---

### Post by ikonia on 2010-11-30
buy a cheap graphics card, it will make it a lot easier to install, and re-connect if the machine is having a problem later down the line.

---

### Post by Powderking on 2010-11-30
I know it sounds a bit stupid. But because of ideological reasons I want a machine that doesn't consume much power.
Therefore I don't like the idea to have a device that I wont need most of the time.

What if I take a graphics card from another PC to just do the installation and then remove it again?
Will this be a problem because of drivers or something like this?

My Alix Server is running for about a year now and I didn't have to use the serial terminal after the installation again.

I don't want to make things more complicated. So if you think it's a bad idea to remove the graphics card again I'll buy a cheap one...

---

### Post by jfmanamtr on 2010-11-30
you should be able to take the card from another PC. I have a server in the basement that I move my computer's video card into when I need to. I haven't had any issues out of doing that I have found.

~JFM

---

### Post by dtfinch on 2010-11-30
You should be able to install on a desktop, making sure to install openssh, then move the drive(s) to the headless box and boot it up, and resume setting things up over ssh.

One snag is that on the new computer, udev will assign the network card a new name (like eth1 instead of eth0) and if you use dhcp it won't come online unless you first edit /etc/network/interfaces to add eth1 with dhcp. The default only enables dhcp on eth0.

---

### Post by Powderking on 2010-12-01
Thx alot for your answers!

Someone told me that it should be possible to set up a bootable PXE image with SSH enabled and then run the installer.
It's certainly the most difficult way. But just because I'm curious I'll try to do it like that.

And if (or let's say when ;) ) I get stuck I'll try it like you propose.


Maybe I can try it with this PXE image?
[http://www.linuxforge.net/docs/crunching/dc-pxe.php](http://www.linuxforge.net/docs/crunching/dc-pxe.php)

---

### Post by surfer on 2010-12-01
i use [FAI]("http://fai-project.org/") for this kind of installation. but it takes a while to get your head around it and that may not be worth the pain for just one installation...

---

### Post by Powderking on 2010-12-01
This looks great! Thx alot :)

---

### Post by surfer on 2010-12-01
should you really use FAI, tell me, i'll give you 1-2 hints that will save you a lot of trouble. these may be things you would not be foolish enough to do wrong yourself; but it got caught in doing...

---

### Post by Powderking on 2010-12-01
It'll take some time untill I'll buy the hardware.

If I'm going to try with FAI I'll post here again...

---

### Post by surfer on 2010-12-01
i may not be following the thread... so feel free to pm me.

---

### Post by Powderking on 2010-12-01
Great, I will.

Thanks alot!

---

