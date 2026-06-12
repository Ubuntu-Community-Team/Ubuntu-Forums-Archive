---
title: "ubuntu server vs ubuntu desktop?"
date: 2020-08-21
forum: Server Platforms
---

### Post by LMH1 on 2020-08-21
Hi can some one give my little support, what is difference with desktop vs server?
I have i tryed them both i find out that server its more terminal based and more hard with hardware charging its more hard to charge networkscard and get it works out the box did not know why?

I have hope that someone tell me why its shuld be more hard?

Because windows server 2020 vs windows 10 its not so much difference on the hardware charges. Its only linced that can be cost if its changed much.

---

### Post by TheFu on 2020-08-21
desktop has a GUI.
server doesn't have a GUI.

desktop loads common desktop applications during the install.
server doesn't load any desktop applications and should only load the specific server packages requested from the install menu beyond the base OS.

After the fact, you can load desktop applications on the server install 
OR
you can load server applications on a desktop install. 
In general, desktops have many more problems with drivers, especially GPUs, so having a GUI installed on a real server is asking for a failure much quicker.

The server install doesn't include all the same drivers as a desktop. For example, drivers for wifi and USB network devices aren't included in a server install. Servers need to use a wired, ethernet, connection, not wifi. Servers need to have static network addresses.  Servers are managed by professionals, not end-users.

Windows servers crash much more often than Unix servers. That's an unfortunate comparison you are trying to make.  The longest I've had a Windows system stay up was about 3 months.  The longest I've had Linux servers stay up is well over a year - back in 2000, had one up almost 2 yrs and is would still be running today if I didn't need to replace the OS.

Sorry, I didn't understand all that was written.

---

### Post by darkod on 2020-08-21
Just to add, if you are complaining about a network card being recognized on install or not, there are rare cases where the OS by default doesn't have a driver for the specific network card. Again, as TheFu said, we are talking about wired connections. I don't enter into discussion of using wifi/usb cards for servers.

So talking about wired connections, in most cases the card should be recognized and it would be no problem to configure it during install.

If you wanted to say that the card is recognized but you find difficulties using the server installer to configure it, that is different subject.

---

### Post by richieserver on 2020-08-22
If you want your network to work, install desktop.

If you want your network to work erratically, then install server

---

### Post by TheFu on 2020-08-22
> **richieserver said:**
> If you want your network to work, install desktop.

If you want your network to work erratically, then install server

false. unhelpful.

---

### Post by SeijiSensei on 2020-08-22
Show us the output of the command "lspci | grep Ethernet". On my Dell T30 server that returns:
```
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
```
That's the adapter on my motherboard. Intel adapters are well-supported because Intel itself writes the drivers and submits them to be included in the Linux kernel.

---

### Post by richieserver on 2020-08-22
> **TheFu said:**
> false. unhelpful.


I'm telling you, that is happening to me right now

---

### Post by wildmanne39 on 2020-08-22
richieserver please do not spread FUD Millions of users including many many many businesses use Ubuntu Server without a desktop.

---

### Post by richieserver on 2020-08-22
OK, I found the problem, I do apologise

---

### Post by TheFu on 2020-08-22
> **richieserver said:**
> I'm telling you, that is happening to me right now

Zero chance of user error.

---

### Post by LMH1 on 2020-08-22
But how did you manage network card in server? is look like ubuntu desktop its easy to charge card without to do anything?
Why did not networks icon show on server?

---

### Post by LHammonds on 2020-08-22
> **LMH1 said:**
> But how did you manage network card in server? is look like ubuntu desktop its easy to charge card without to do anything?
Why did not networks icon show on server?
Icon?  Server?  I have never installed a GUI on my servers for the express purpose of keeping my used resources and security weak-points low.  I use PuTTY + SSH to manage my servers.  The only thing I have ever touched with my servers regarding network, is the configuration file which is located here since Ubuntu Server 18.04 --> /etc/netplan/*.yaml

When I boot up a server for the 1st time, it comes up using DHCP and one of my 1st steps is to convert it to a static IP.  I have detailed such steps [here.]("https://hammondslegacy.com/forum/viewtopic.php?p=813#p813").

LHammonds

---

### Post by TheFu on 2020-08-22
> **LMH1 said:**
> But how did you manage network card in server? is look like ubuntu desktop its easy to charge card without to do anything?
Why did not networks icon show on server?

servers don't have icons. They don't have any GUI.
Network management is through config files.  Search for "ubuntu server guide" for instructions.  This is common across all linux and unix servers and always has been the method used.  The specific config details have changed over the decades.

If you need a GUI, perhaps the skills are not ready to run a server?

This management method is much easier than using a GUI that changes from release flavor to release flavor. It is especially easy to manage 1000 servers or 5000 when text config files are used for all settings.  This s a foreign idea to average desktop users who need some gui to lead them through settings.

---

### Post by LMH1 on 2020-08-23
Can someone make a guide how to make domain user (automatcally backup) everthing from a desktop computer to a server? And how caching (proxy) or some like that works?

Because i did not find pfsense support to make its to ruter also so i have hoped to get some help.

---

### Post by TheFu on 2020-08-23
Those are new questions needing different expertise.

BTW, pfSense isn't Linux, so that should probably be in a completely different forum.  I use OPNSense, previously used pfSense, have deployed pfSense for clients.  Don't see what Ubuntu/Linux has to do with router software like those.

If you can't find a guide, maybe create one?  Linux solutions tend to build on each other, so jumping to the end of the book to solve the problem doesn't work. You need to learn chapter 1, 2, 3 in order first.  Background is key.

There are a number of posts in these forums around backups.  IMHO, all the "1-click" solutions are terrible and prone to total failure. We see that a bunch.  What you need depends completely on your situation. Lots of choices. No need to rehash all those issues now.

---

### Post by LMH1 on 2020-08-23
I have asus\netgear ruter very easy but most its very outdated and poor.
What is difference with PFsense and OPNSense?

Because ubuntu 20.04 works with 2.5 gigabit ethernet and SFP+ and QSFP+ and UEFI bios.
PFsense did not works and did not have UEFI bios support and support of more than 4 GB ram, drives in freeBSD is poor compare with ubuntu.

---

### Post by mastablasta on 2020-08-24
if this is for home use or LAN server in smaller company there are a couple of options that come with GUI. 

For example **Zentyal server** will come with desktop as well as a webgui (you control server via web browser graphical interface) dashboard. it is specifically designed to help migrate windows server users to linux. it is based on ubuntu. i am unsure if they still have official Cannonical support/backing. they used to have it. the community edition is free of charge.

**Open media vault (OMV)** is a Debian based server that offers a very nice WebGUI. it is easy to install and setup. it is aimed at creating media storage server. but has many GUI addons and is versatile, so you can use it for other things as well. good community support in forums.

**Nethserver **is a server based on CentOS (which is basically a community edition of Red Hat Linux). It also has a very nice WebGUI and is easy to install and setup. again this one is aimed at small businesses and home users. it's been a while since i tested this one, but it does have descent community support and good documentation.

there are a few others that offer various types of GUI interfaces for easier management of smaller or larger servers. but these 3 stuck in my mind the most due to their ease of use.

i use **Ajenti WebGUI** installed on Ubuntu server. it does make some things easier to administer. i have a home LAN server with limited internet connections.

as other mentioned the best thing is to learn and then have text only (Command line interface =CLI), especially if you plan to open it to internet. 

if you plan to access it from internet make sure you **_harden your server_** as much as you can and_** regularly monitor**_ what is going on on server. and don't forget about _**backups**_.

here is one of many hardening lists: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)
this one is from digital ocean - also good source of information: [https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)

---

### Post by math492m on 2020-08-26
if you use ubuntu server 18.04 you wont have thoose nic problems 

and with gui it basicly looks the same as regular ubuntu

---

### Post by math492m on 2020-09-03
server is a little more reliabul and maybe more powerfull for long time use

but why you can download gui for the server makes little sense

---

### Post by ameinild on 2020-09-07
> **math492m said:**
> server is a little more reliabul and maybe more powerfull for long time use

Errr, what? Ubuntu desktop is basically Ubuntu server with GUI packages added. They core systems are completely identical, the only remote truth to your statement might be that the server maybe has fewer packages that can break.

---

