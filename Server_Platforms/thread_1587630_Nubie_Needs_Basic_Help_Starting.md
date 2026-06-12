---
title: "Nubie Needs Basic Help Starting"
date: 2010-10-03
forum: Server Platforms
---

### Post by Ed_Ziffel on 2010-10-03
Hi all,

I've loaded Ubuntu Server 10.04 on a dedicated machine.  I'm all set to begin to attempt to configure it and bang!: its a command prompt with extra tiny fonts due the system loading at maximum resolution.  

Q's:

1.  Can I get a GUI?  This is a real butch box.  Quad Phenom running at 3.4 with 4 gig 1600 ddr3 with extra cooling and capable of OC ing to ultra stupid.  In addition there will only be test traffic on it. (As I'm installing it I'm wondering why I don't use an old box and do something different with this one, probably later...) So I think I can take the hit.  

2.  Do you manage this from a work station on the lan?  If so How?

Thanks

---

### Post by Jesse B on 2010-10-03
1.) Yes, you can install a GUI if that's what you want.
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

2.) This is also an option.  "sudo apt-get install openssh-server" will allow you to ssh into the server via a workstation on the lan.

---

### Post by wojox on 2010-10-03
#1 Yes but you should use [Webmin]("http://www.webmin.com/")
I believe it's in the repo's.

#2 Web browser for Webmin or ssh for command line. If you don't understand the command line it's a great time to start.

---

### Post by kaginken on 2010-10-03
Here's something I found that looks correct:  [http://www.ubuntugeek.com/how-to-install-gui-in-ubuntu-10-04-lucid-lynx-server.html](http://www.ubuntugeek.com/how-to-install-gui-in-ubuntu-10-04-lucid-lynx-server.html) 
You really don't need the GUI, but if you're a newbie it might be useful.

As far as managing it, I do it all via command line from my laptop.

---

### Post by Jesse B on 2010-10-03
My honest opinion, to add on to what I already said.  I'm a complete noob, I've only been using Linux for a couple months, and that's just Ubuntu on my desktop.  When I made my home server, I put Ubuntu Server 10.04.1 on there, and decided I'd learn to use the command line properly.  It's been a fantastic learning experience, and have learned a ridiculous amount in the last month.  It's definitely worth doing, in my opinion.

---

### Post by Ed_Ziffel on 2010-10-03
Thanks,

Will do:  Check out webmin, try the ssh, read the suggested links and yeah I have some grip on the command line just don't know all the commands.  

How do you access the help and the man files from the prompt.  Been a while and I don't recall.

---

### Post by Jesse B on 2010-10-03
> **Ed_Ziffel said:**
> Thanks,

Will do:  Check out webmin, try the ssh, read the suggested links and yeah I have some grip on the command line just don't know all the commands.  

How do you access the help and the man files from the prompt.  Been a while and I don't recall.

~$man man :)

Example:

man apache2

---

### Post by E-call on 2010-10-05
You should also download putty for using the command line interface from a remote machine. Its small and lightweight and works very well.

---

### Post by Zanthir on 2010-10-05
1. I would say go ahead and run a desktop environment on your server. Something like
 
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
```
 
should do the trick. [Reverence.]("http://ubuntuforums.org/archive/index.php/t-186298.html") (That person needed to enable the universe repository. See [this]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Extra_Repositories") to find out how, if you need to too.)
 
This will install the gnome desktop and a suite of applications which you will probably find very helpful since you are new to Ubuntu. I'm very new too, and I just feel more relaxed when I have a desktop GUI in front of me. The command line makes me feel anxious.
 
This will not run the desktop environment at boot. You will have to type
 
```
startx
```
 
to start your desktop session. That way you can use it like a net to catch you when you get stuck at the command line. It sounds like you have enough horsepower under the hood that you won't be too concerned with eating up a few resources, at least while you're getting things set up. This way you can set up your server from within GNOME if you wish, and then reboot into just a command line to free up your resources.
 
2. To manage it over the LAN use SSH for a CLI and VNC for desktop. To install and connect with SSH without security (not recommended - please read [other guides]("https://help.ubuntu.com/7.04/server/C/openssh-server.html") for setting up security) use
 
```
(install on server)
sudo apt-get install ssh
 
(connect from client)
ssh [EMAIL="username@hostname"]username@hostname[/EMAIL]
(assumes port 22 - default port)
```
 
Setting up VNC from within GNOME is easy ([link]("https://help.ubuntu.com/community/VNC/Servers#vino")).

---

