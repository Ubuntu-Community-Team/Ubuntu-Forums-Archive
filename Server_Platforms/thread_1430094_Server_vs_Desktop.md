---
title: "Server vs Desktop?"
date: 2010-03-14
forum: Server Platforms
---

### Post by houldsworth1 on 2010-03-14
I had already tried this post elsewhere with no luck so trying it in the server section.
 
I have Ubuntu 9.10 installed on an old Gateway desktop. It is running a system called Jira using a Tomcat web server, so 99% of the time access is thorugh the web browser. For the rest of the time I access it remotely using TightVNC.

This works great so far but the system will not boot if I remove the screen (which I need to do since it is in the way). I have tried several remedies suggested by folks on this forum but none of them have worked. So my question is this...

a. If I uninstall and reinstall using Ubuntu Server edition (32-bit) will the system boot without the screen?

b. Assuming the above will work - can I still access the machine directly using TightVNC (I presume not since that needs the graphics setup). If not, how do I connect to the machine remotely?

Thank you!

---

### Post by RasterBurn on 2010-03-14
a couple years back i used to run my own webhosting business, i owned all the hardware (including the server) i used a couple different distros during that time finding the one that worked the best for me, in the end i was using Ubuntu Server (dont remember which version) but anyways, the server didnt have a gui on it which was perfect after all it was a server, not a desktop, it ran web, web SSL, ssh, ftp, and mail, anyways, where i was living the server ran behind a board (at the time my son liked to push power buttons on computers) and i only had a screen hooked up to it during the initial install, the rest of the time there was no screen, keyboard, or mouse hooked up to it and any admin work i did on the server was through ssh with putty or else through web SSL, so in otherwards, yes UBUNTU Server will boot up without a physical screen connected to it. also, for running server apps, like Tomcat it i recomended to use a server distro over a desktop distro (more or less to free up more resources for server operations), just my experiences with things, hope that helps :)

---

### Post by Samatva on 2010-03-15
I agree w/ RasterBurn - the server version runs more efficiently, lees wasted resources.

Since server administration is only a small part of my job, I have a hard time getting/staying proficient from the command line. My solution is Webmin - uses almost no resources when you are not using it, yet allows a GUI (albeit web) administration screens. I find myself at the command line only once in a while - Webmin won't *quite* do everything easily ;-)

---

### Post by Agent ME on 2010-03-15
It's possible that your computer's BIOS might have checks so that it doesn't boot if there is no monitor, keyboard, or mouse. Maybe you should check the BIOS menu.

---

### Post by RasterBurn on 2010-03-15
yes, webmin is very robust in terms of a simple browser based gui it also has alot of mods that expand what it can do to almost anything you need it to do including modifying cronjobs, setting up dns, apache, tomcat, postgre, mysql, even doing system updates, although on the other hand, if you prefer to run tightVNC you could setup a method to run it, before i started running a server i cofigured a with a debian where it would boot into a CLI and after logging in i was able to start the xserver (i dont remember if xserver or xorg requires a physical screen to be attached when starting or not) but you could always go the route of fluxbox for a GUI on the server if it doesnt need a screen to startup

---

### Post by houldsworth1 on 2010-03-15
> **Agent ME said:**
> It's possible that your computer's BIOS might have checks so that it doesn't boot if there is no monitor, keyboard, or mouse. Maybe you should check the BIOS menu.
 
I have checked that - nothing obvious there but I don't think I will know for sure until I try it out.  That said, it is an Ubuntu message that is waiting for a response, not a BIOS one, so I think I will be OK.
 
Thanks to everyone for the responses so far.  Does the webmin run on windows? If so, where would I find a copy of that?
 
Thanks!

---

### Post by HermanAB on 2010-03-15
Webmin is in the repos - so is ssh-server.

---

### Post by houldsworth1 on 2010-03-15
> **RasterBurn said:**
> ...if you prefer to run tightVNC you could setup a method to run it, before i started running a server i cofigured a with a debian where it would boot into a CLI and after logging in i was able to start the xserver ...you could always go the route of fluxbox for a GUI on the server if it doesnt need a screen to startup
 
> **HermanAB said:**
> Webmin is in the repos - so is ssh-server.
 
It's like their trying to communicate with me... :grin:
 
Seriously though...I'm a newbie here. I have a little experience with Unix from many years ago, but as a person with an application installed on it rather than an administrator of it. So, while I know there is some fantastic information in the replies above, please go easy with me as I have a lot of catching up to do and will pribably never reach your level of expertise.
 
But, now that I know that those tools are there, I will search them out in the next few days - thank you.

---

### Post by houldsworth1 on 2010-03-15
One quick question.  This PC connects to the network via a Linksys wireless network product that plugs into the USB port.  
 
On the desktop version I simply plugged it in and everything worked - all I had to do was enter the WEP key and I was done.  
 
Will the same thing happen in the server version or will I have to manually install the driver and execute some command lines to make things work?  If I have to do this manually is that something that Webmin will help me with?
 
TIA!

---

### Post by RasterBurn on 2010-03-15
hello again, i see your issue on running the machine without a "head" the server version of Ubuntu will most likely have issues with the wireless card also you wont have a native GUI so all the setup to get it to work will be through a CLI (command line interface) how far away are you from the dlink router with this machine? I am gonna guess that your a room or 2 away from the router with this machine, if i remember correctly webmin will allow you to configure all of your network interfaces through it, you can have a look over the webmin site at [WebMin]("http://ubuntuforums.org/www.webmin.com") there you can search through the available modules and documentation

---

### Post by houldsworth1 on 2010-03-16
OK - following the advice in another thread I have changed the value for GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to an empty string and changed /etc/X11/default-display-manager to be empty. I then ran 'sudo update-grub' to update things and the machine will now boot without a screen attached.  
 
Now the machine starts but doesn't run the GUI (no need to install the server then) and drops to a login prompt instead and, after logging on, I can access the machine through the CLI.
 
This is fine however the problem is that I can't access it remotely anymore.  TightVNC won't connect (I wasn't surprised about that) so I tried running Putty SSH and that didn't seem to work either.
 
Does anyone know how I can get around this last bit and connect to the machine so that I can login remotely?
 
Thanks!

---

### Post by RasterBurn on 2010-03-16
to use putty you will need a telnet or ssh server, i recommend ssh so once you login using your account run the command "sudo apt-get install sshd" this will install the ssh daemon needed to connect via ssh using putty :) you will of course need to input your password to install

---

### Post by houldsworth1 on 2010-03-16
> **RasterBurn said:**
> to use putty you will need a telnet or ssh server, i recommend ssh so once you login using your account run the command "sudo apt-get install sshd" this will install the ssh daemon needed to connect via ssh using putty :) you will of course need to input your password to install
 
This sounds like what I am after but when I run that I get 
E: couldn't find package sshd

---

### Post by houldsworth1 on 2010-03-16
Forget that - I took at guess at just ssh instead of sshd and it works!!!
 
Thanks!

---

### Post by RasterBurn on 2010-03-16
try installing the package "ssh" that should be the one you are looking for, it will install both the client "openssh-client" and the server "openssh-server"

just on a note, all the items in quotation marks are valid packages that can be installed exactly as they are typed

---

### Post by houldsworth1 on 2010-03-17
It works now - thanks!!  :)

---

