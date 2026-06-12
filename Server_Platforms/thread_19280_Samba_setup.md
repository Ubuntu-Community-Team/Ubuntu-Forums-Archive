---
title: "Samba setup"
date: 2005-03-11
forum: Server Platforms
---

### Post by poyner on 2005-03-11
Hi all, I was wondering if I could get some help with setting up samba. I've been playing with it for a fair while with little success. 

My setup is. a PC with dual boot XP/Ubuntu and a laptop running Windows ME. They are connected through a modem/router (NB5580W). The PC is hard wired and the laptop is wireless. The NB5580W is acting as a DHCP host and handing out IP's. This is all working fine. 

In the PC there is a HD that I want to be able to share with the laptop. This works fine under XP however I don't seem to be able to get it working under Ubuntu. 

I have installed samba. my smb.conf currently looks like:

[global]
workgroup = homegroup
os level = 20
netbios name = HOBBIT
security = share
wins support = true

[sharedrive]
comment = shared drive
path = /media/share
read only = yes
guest ok = yes

It used to be a lot more complicated (the standard one) but I stripped it down to try and simplify things. 
my problem is that I can't see either computer at all from the other one.

I'm thinking the problem could well be at the laptop end. Currently under TCP/IP properties i have DNS disabled. gateway set as my router. wins server set as the ip of my pc. and ip address is obtained automatically. 
I can ping between the computer fine.

I have just tried installing ethereal and watching the traffic at the ubuntu end but unfortunately it hasn't really helped me. Does anyone have any suggestions/tips/help that they can offer. Thanks heaps.

---

### Post by Rottweiler on 2005-03-11
[QUOTE=poyner]In the PC there is a HD that I want to be able to share with the laptop. This works fine under XP however I don't seem to be able to get it working under Ubuntu.[/QUOTE]What sort of error or problem are you having exactly?

I usually add "public = yes" to the share definition for something where security/authorization is not an issue.

Have you installed samba?
```
sudo apt-get update && sudo apt-get install samba
```Is samba running?```
sudo /etc/init.d/samba start
ps aux | grep -E '(smbd|nmbd)'
```Can you ping the server from the laptop?

Can you connect to the share manually via IP address?
Start...Run...\\192.168.0.101\sharedrive   (or whatever the IP addr is)

Can you connect to the share manually via server name?
 Start...Run...\\hobbit\sharedrive

---

### Post by nemin on 2005-03-12
[QUOTE=poyner]Hi all, I was wondering if I could get some help with setting up samba. I've been playing with it for a fair while with little success. 
[/QUOTE]After the nice post of Rottweiler, I just want to mention this link, that you'll probably find usefull:
[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)

Good luck :)

---

### Post by ubuntu_demon on 2005-03-12
[QUOTE=poyner]Hi all, I was wondering if I could get some help with setting up samba. I've been playing with it for a fair while with little success. 

My setup is. a PC with dual boot XP/Ubuntu and a laptop running Windows ME. They are connected through a modem/router (NB5580W). The PC is hard wired and the laptop is wireless. The NB5580W is acting as a DHCP host and handing out IP's. This is all working fine. 

In the PC there is a HD that I want to be able to share with the laptop. This works fine under XP however I don't seem to be able to get it working under Ubuntu. 

I have installed samba. my smb.conf currently looks like:

[global]
workgroup = homegroup
os level = 20
netbios name = HOBBIT
security = share
wins support = true

[sharedrive]
comment = shared drive
path = /media/share
read only = yes
guest ok = yes

It used to be a lot more complicated (the standard one) but I stripped it down to try and simplify things. 
my problem is that I can't see either computer at all from the other one.

I'm thinking the problem could well be at the laptop end. Currently under TCP/IP properties i have DNS disabled. gateway set as my router. wins server set as the ip of my pc. and ip address is obtained automatically. 
I can ping between the computer fine.

I have just tried installing ethereal and watching the traffic at the ubuntu end but unfortunately it hasn't really helped me. Does anyone have any suggestions/tips/help that they can offer. Thanks heaps.[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org) also gives good information about samba

I had problems with samba when using an ubuntu warty as client. When I upgraded the client to hoary the problems vanished.

---

### Post by lukem on 2005-03-12
I have installed samba and wanted to install swat.  I get the following error screen when trying to mark it for installation in synaptic:

swat:
  Depends: samba but 3.0.7-1ubuntu6.3 is to be installed

Any suggestion.  I'm not even sure what this means.

Thanks
Luke

---

### Post by nikolokolus on 2005-03-12
[QUOTE=lukem]I have installed samba and wanted to install swat.  I get the following error screen when trying to mark it for installation in synaptic:

swat:
  Depends: samba but 3.0.7-1ubuntu6.3 is to be installed

Any suggestion.  I'm not even sure what this means.

Thanks
Luke[/QUOTE]

In order to get swat I had to enable a vanilla debian repository in my apt/sources.list (word to the wise use these non-ubuntu repositories with great care; as doing any kind of mass update with these enabled will likely thrash your system).  Either add the following through synaptic or edit your /etc/apt/sources.list by hand: 

Deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing main

search for samba and/or swat and you'll upgrade from version 3.0.7 to 3.0.10 

After you install swat there is still some more editing of config files:

Edit the /etc/services text file and append the following line to the end of the document: 
# Local services 
swat                 901/tcp 

next you need to append the following at the end of your /etc/inetd.conf 
swat stream tcp nowait.400 root /usr/sbin/swat swat

the next step is to restart/start the inetd daemon to make these new services available.  Open a browser and type:  localhost:901 into the address window enter your root password and you should be good to go.


note:  Swat assumes root privleges (unless you configure it otherwise) so to make it work I've enabled the root account on my system which is done by simply using the following command in a terminal:   $ sudo passwd root 
and entering whatever password you desire for the root account


Hope that helps

Nick

---

