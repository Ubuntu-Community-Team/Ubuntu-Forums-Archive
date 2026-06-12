---
title: "Need help with Server OS / Network"
date: 2015-04-22
forum: Server Platforms
---

### Post by adam_f2 on 2015-04-22
Hello everyone!

I'm not quite sure where to post this as it isn't strictly Ubuntu-related, but I reckoned the newbie forum might be a good place. My son recently built a computer for his grandfather (nothing special, just a Pentium inside). He installed Ubuntu desktop 14.04 LTS on it. Before being given to his grandfather, however, he used the server to create some sort of server for playing video games. Recently, he has expressed interest to me that he would like to build a real server (as in one with a Xeon, probably a 1230v3 or 1245/46v3, but I may chip in and we may get a combination server for playing video games and for holding media like songs and movies as well). He told me that if he did do this, he would put Linux on the server. I did a little research, and it appears to me as though there are two or three main options when it comes to Linux. Ubuntu, which is the distribution I would like to use because I bought him a book titled "Ubuntu Linux Toolbox 2nd Edition" by Christopher Negus and I wouldn't want to see it go to waste if he used another distro, CentOS, which seems like a very viable option and also one that most enterprises use, and possibly Debian or Linux Mint. My question is, would running Ubuntu Server be a viable option for his server? He says he wants to run Murmur, the server client for the VoIP service Mumble, a Team Fortress 2 server (which is a video game where 9 classes fight each other or something), and maybe a Minecraft server (where you are a block man running around and building things and destroying other things). He doesn't want to run a large server, and in his exact words "Maybe a 20 person Mumble server, 20 person Minecraft server, and a 20 person Team Fortress 2 server, but not all at the same time. Just Mumble and one game."

First of all, will our network upload speed of 10 MbPS be able to handle this (approximately 1.25 megabytes per second upload)?

Second, between Ubuntu Server, CentOS, Debian, and Linux Mint, which would be the best route to go? Both of us are more GUI-inclined, but we'll be able to figure out a program like Putty eventually if it comes to that. However, we aren't the most tech-savvy when it comes to operating systems.

Edit: Just to put this out there, I put an 80GB partition of Ubuntu's 14.04 LTS desktop OS on my son's 2TB hard drive, so he has been playing around with it and says he likes it.

Once again, sorry if this was posted in the wrong place, I've tried to tag it as a Server post. If it needs to be moved or something, please don't hesitate to do so!

Sincerely,

Adam

---

### Post by ricky-flammia on 2015-04-22
Ubuntu currently has three LTS versions supported (10.04, 12.04 and 14.04), is backed by Canonical who also offers the Ubuntu Advantage support plan and Landscape system management software, Ubuntu's package manager derives from the Debian package manager (same for Mint and many other popular distros but not Cent OS) and Ubuntu has a regular update cycle. What this all means is that Ubuntu gives you options, reliability and is supported in a way that the other two distros that you had mentioned aren&#8217;t. P.S. Server versions of Ubuntu offer more server geared setting and software however they do not come preinstalled with a GUI however you have the option to install it yourself if you so choose. If you are interested in doing so I can post a link to a tutorial if you would like me to.

---

### Post by sandyd on 2015-04-22
> **adam_f2 said:**
> Hello everyone!

I'm not quite sure where to post this as it isn't strictly Ubuntu-related, but I reckoned the newbie forum might be a good place. My son recently built a computer for his grandfather (nothing special, just a Pentium inside). He installed Ubuntu desktop 14.04 LTS on it. Before being given to his grandfather, however, he used the server to create some sort of server for playing video games. Recently, he has expressed interest to me that he would like to build a real server (as in one with a Xeon, probably a 1230v3 or 1245/46v3, but I may chip in and we may get a combination server for playing video games and for holding media like songs and movies as well). He told me that if he did do this, he would put Linux on the server. I did a little research, and it appears to me as though there are two or three main options when it comes to Linux. Ubuntu, which is the distribution I would like to use because I bought him a book titled "Ubuntu Linux Toolbox 2nd Edition" by Christopher Negus and I wouldn't want to see it go to waste if he used another distro, CentOS, which seems like a very viable option and also one that most enterprises use, and possibly Debian or Linux Mint. My question is, would running Ubuntu Server be a viable option for his server? He says he wants to run Murmur, the server client for the VoIP service Mumble, a Team Fortress 2 server (which is a video game where 9 classes fight each other or something), and maybe a Minecraft server (where you are a block man running around and building things and destroying other things). He doesn't want to run a large server, and in his exact words "Maybe a 20 person Mumble server, 20 person Minecraft server, and a 20 person Team Fortress 2 server, but not all at the same time. Just Mumble and one game."

First of all, will our network upload speed of 10 MbPS be able to handle this (approximately 1.25 megabytes per second upload)?

Second, between Ubuntu Server, CentOS, Debian, and Linux Mint, which would be the best route to go? Both of us are more GUI-inclined, but we'll be able to figure out a program like Putty eventually if it comes to that. However, we aren't the most tech-savvy when it comes to operating systems.

Edit: Just to put this out there, I put an 80GB partition of Ubuntu's 14.04 LTS desktop OS on my son's 2TB hard drive, so he has been playing around with it and says he likes it.

Once again, sorry if this was posted in the wrong place, I've tried to tag it as a Server post. If it needs to be moved or something, please don't hesitate to do so!

Sincerely,

Adam
Upload speed: Depends
Best is to test it out, but here are a few quotes
[From Mumble Wiki]("http://wiki.mumble.info/wiki/FAQ/English#What_are_the_bandwidth_requirements.3F"): 144kbits/s
TF2: Varies, if your using custom maps, your upload speed will hinder how fast the maps download on TF2 cilent.
MC: no idea

2. Cross out Linux Mint - mainly focused on GUI
Test the rest of them in VirtualBox. Server installations are meant to be minimal so all of them are by default non-gui installs except for the OS mentioned above. I have also found that when GUIs break, you will have to go into the terminal to investigate anyways, so better off knowing the configuration then doing it through a GUI

Some advice about SeLinux if your running into issues with it on CentOS:
If you want to work with it, be prepared to have some struggles at the beginning and be ready to read up on SeLinux policies/tools (e.x: audit2why/audit2allow/semodule). Dan Walsh's blog is a nice place to start to learn.
If you don't, and you're fine with less security, then turn it off. Its a nice idea for people to learn SeLinux and how to create custom modules/policies to suit their needs, but it's not for everyone. It is one of the reasons why I feel that CentOS is more geared towards professional use where people are supposed to figure out how to actually us SELinux properly without disabling it.

Side Note: E3-1230 v3 uses 80W TDP, that might be something to think about as well

---

### Post by mastablasta on 2015-04-23
why would you need a Xeon for that? 

your web connection is kind of low for 20 people I think.

while servers are by default a non GUI there are webGUI that will use a lot less system resoruces and make it easy to configure the server. for example Zentyal, OpenMediavault... I) persona&#269;lly like Ajenti with it's clean interface and many use Webmin. ofcourse Putty will come in handy as well.

unless you need some enterprise grade data accuracy, then a desktop with strong CPU that has good power management, plenty of ram and maybe an SSD for system disk will do.

I got a Gen7 HP micro server. The Gen8 ones are nice. they are small, quiet and cool. with many server funcitons built in. I run the system off a very good USB stick :-) it's a cheap enterprise grade server. you might want something with stronger CPU. and as I read Minecraft server needs plenty of RAM.

---

### Post by matt_symes on 2015-04-23
Hi

Welcome to the forums.

Your first question is pretty broad so here are just some thoughts.

Ubuntu server will be fine for what you are trying to do and i would really suggest running the server version. It may not have a GUI but will consequently use less server resources, use server optimisations out of the box and have a smaller attack vector should you put it in the DMZ behind your router. 

Also Ubuntu has a large user base and receiving help can be easier because of this.

I would suggest setting the server up and testing it extensively on your local LAN before exposing it to the world. Once it has been set up and tested, tear it down and set it up again. Once that has been done a couple of times, it'll be easier to fix and identify problems or compromises.

Always think security first when setting up a server that is exposed to the Internet.

There are other options as well as running a server in your home and chewing up your electricity bill, such as digital ocean droplets that seem pretty popular at the moment with some people that i talk to. I have no association with digital ocean so i cannot comment on whether they are suitable for what your son is trying to do.

Kind regards

---

### Post by adam_f2 on 2015-04-30
Wow! Sorry for the long reply, I haven't had a lot of time recently. Thank you all for your wonderful feedback and suggestions! I think I will help my son with just installing the Ubuntu Server, due to the general consensus that it isn't necessarily at a disadvantage compared to the other server distributions and I can draw upon the large group of avid Ubuntu fans here if he or I need help.

> **ricky-flammia said:**
> What this all means is that Ubuntu gives you options, reliability and is supported in a way that the other two distros that you had mentioned aren&#8217;t.
I see. Not to mention the fact Ubuntu has a great support forum full of great, helpful people!

> **sandyd said:**
> If you don't, and you're fine with less security, then turn it off. Its a nice idea for people to learn SeLinux and how to create custom modules/policies to suit their needs, but it's not for everyone. It is one of the reasons why I feel that CentOS is more geared towards professional use where people are supposed to figure out how to actually us SELinux properly without disabling it.
How much of a disadvantage is it to be running Ubuntu Server rather than CentOS because of the loss of SELinux? Is there an equivalent to it on Ubuntu Server? Does it come with Ubuntu Server? I'm not very knowledgeable about these things, I'm sorry.

> **mastablasta said:**
> why would you need a Xeon for that?
I'm hoping to use the server later on after my son's gone off to college and won't need it so often as a file storage server, which will more than likely mean a new motherboard and ECC. Using FreeNAS or something similar. Xeons support ECC, so I'd rather make the investment now than wait until later and have to buy a whole new rig. At least now I'll have the CPU already ready to go, and by the time I get it done the Haswell workstation/server motherboards will have dropped a bit in price so they are more affordable as Broadwell/Skylake (Skywell? not sure)/whatever the heck else Intel comes up with CPUs come out.

> **mastablasta said:**
> while servers are by default a non GUI there are webGUI that will use a lot less system resoruces and make it easy to configure the server. for example Zentyal, OpenMediavault... I) personally like Ajenti with it's clean interface and many use Webmin. ofcourse Putty will come in handy as well.
Duly noted, I will look into it. Having a GUI of some sort without having to install a GUI onto the computer will be nice.

> **matt_symes said:**
> Welcome to the forums.
Thanks!

> **matt_symes said:**
> Ubuntu server will be fine for what you are trying to do and i would really suggest running the server version. It may not have a GUI but will consequently use less server resources, use server optimisations out of the box and have a smaller attack vector should you put it in the DMZ behind your router. 
I see. Well, I think this is pretty good. Will a GUI really affect performance? On my normal PC with Windows installed (I know, I'm a terrible person), my CPU usage is only ever about 1% on a normal screen, maybe jumping up to around 10% on something more intense like a video. I realize that the Xeon 1230v3 doesn't have a graphics chip in it, but the 1245/1246v3 does and I could use that if graphics performance isn't really a huge drawback to performance.

> **matt_symes said:**
> I would suggest setting the server up and testing it extensively on your local LAN before exposing it to the world. Once it has been set up and tested, tear it down and set it up again. Once that has been done a couple of times, it'll be easier to fix and identify problems or compromises.
Noted.

> **matt_symes said:**
> Always think security first when setting up a server that is exposed to the Internet.
I'm sorry, but could you point me in the direction of some tutorials that would help me in keeping my router and/or IP secure? My son plans on using a service called No-IP which supposely reroutes your IP address through another address in order to simulate a static IP and also protects your privacy, or so he says. Anything else I could do? I don't have a very fancy router, but it can open and close ports and other such things. I know that the servers my son would be using wouldn't be 24/7, so if there was a script that would automatically close ports X, Y, and Z would that help with keeping us protected?

Sorry for the late response and for writing so much, but thank you all for being great people with an old newbie and his son!

---

### Post by sandyd on 2015-04-30
> **adam_f2 said:**
> 
How much of a disadvantage is it to be running Ubuntu Server rather than CentOS because of the loss of SELinux? Is there an equivalent to it on Ubuntu Server? Does it come with Ubuntu Server? I'm not very knowledgeable about these things, I'm sorry.

Ubuntu uses Apparmor instead of SeLinux.

There isn't much loss unless your looking to focus on creating a security-targeted installation. That being said, Selinux offers much finer control than Apparmor, and that is what most people stumble into. Its complicated simply because it allows for fine-grained control.
> **adam_f2 said:**
> 
I see. Well, I think this is pretty good. Will a GUI really affect performance? On my normal PC with Windows installed (I know, I'm a terrible person), my CPU usage is only ever about 1% on a normal screen, maybe jumping up to around 10% on something more intense like a video. I realize that the Xeon 1230v3 doesn't have a graphics chip in it, but the 1245/1246v3 does and I could use that if graphics performance isn't really a huge drawback to performance.
It will use system resources (i.e. RAM/HDD/CPU) unless you choose a minimal gui. In that case, the usage is negligible. 
> **adam_f2 said:**
> 
I'm sorry, but could you point me in the direction of some tutorials that would help me in keeping my router and/or IP secure? My son plans on using a service called No-IP which supposely reroutes your IP address through another address in order to simulate a static IP and also protects your privacy, or so he says. Anything else I could do? I don't have a very fancy router, but it can open and close ports and other such things. I know that the servers my son would be using wouldn't be 24/7, so if there was a script that would automatically close ports X, Y, and Z would that help with keeping us protected?

the last time i checked, no-ip is a dynamic dns service that keeps your dynamic IP Address synced up with a hostname. Whenever your IP changes, the ip of the hostname is updated using a dynamic dns updater.

That being said, don't use DMZ, use port forwarding to forward one port at a time. Use fail2ban or some other SSH brute force protection, and keep applications updated.

---

### Post by matt_symes on 2015-05-03
Hi

> That being said, don't use DMZ, use port forwarding to forward one port  at a time.

I think this is pretty good advice from sandyd as you seem pretty new to this. You won't have to play with iptables yourself so much and only the ports forwarded from the router will be visible.

Kind regards

---

