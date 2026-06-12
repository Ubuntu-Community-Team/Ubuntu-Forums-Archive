---
title: "No screen server installation"
date: 2007-10-11
forum: Server Platforms
---

### Post by slimsumo on 2007-10-11
Hi,

 I was wondering if it was possible to actually create a script to install ubuntu server automatically at the moment you boot the cd  because I have a server with no screen and only a keyboard. The only other computer I have here is a laptop so i cannot plug a screen into the server.

Let me here your ideas please

---

### Post by netlogic on 2007-10-11
only thing that i know is kickstart, but it won't be purely automatic like nlite does on XP.

---

### Post by Xenaco on 2007-10-11
You can get a cheap dual KVM switch with cables for $20 to 50.

---

### Post by Brazen on 2007-10-12
yeah, installing an OS without a monitor is a tough one.  It is probably doable with a kickstart script.  I've never used kickstart though, so I don't know how complicated it is to put the script together.  You'll just have to make sure that openssh-server is installed at some point in the script so you can get in and manage it remotely when the install is done.

---

### Post by koenn on 2007-10-13
> **slimsumo said:**
> Hi,

 I was wondering if it was possible to actually create a script to install ubuntu server automatically at the moment you boot the cd  because I have a server with no screen and only a keyboard. 
Yes, that exists : it's called a preseed file and contains answers to all the questions the installer asksn so you can run the installation completely unattended. ( [http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm) )
At least in theory. 
The problem is : how to let the server read the preseed file. It can be placed on a web server, but then it won't be accessible until the installer has configured the network - and it may prompt for user input before it reaches there. 
So you'd need to create a customized CD with a suitable preseed file and a way to tell the installer to just read the file and never ask questions. 
Another way is to use a network boot and download installer etc from a server. I this case, the dhcp/bootp server would have to be configured to pass the (location of) necessary files, the way LTSP / edubuntu work.
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install)


The debian installer (and presumably ubuntu installer in Expert mode) have an option to provide a network console for remote installations. Again, it will only work after the network has been configured. 

Lastly, it should be possible to install from within a working Linux system, so that instead of booting an installcd, you start the installer from a running system, just as you would any other program. So this is something that could work while you ssh into your server.  I've seen it mentioned on a Debian siite but I don't know much more about it. 
[http://www.debian.org/releases/stable/i386/apds03.html.en](http://www.debian.org/releases/stable/i386/apds03.html.en)


It's probably way easier to borrow a monitor somewhere. 

one more :
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

---

### Post by netlogic on 2007-10-14
[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

---

