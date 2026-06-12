---
title: "Router/Gateway with Windows Stations"
date: 2012-02-21
forum: Server Platforms
---

### Post by ElderSyrinx on 2012-02-21
Gateway/Router = Ubuntu 11.10 64bit (desktop version not the server version, bad choice?)
Workstations = Windows 7 (64bit) / Windows xp

I'm attempting to replace my current router (cisco box which is wide open) with a pc for a configurable firewall with Internet access control on a small workgroup (16 wired workstations and various wireless phones, laptops and other hand held devices) and future ftp access to our file server.

I'm an old msdos man so Yes, I am way over my head.  But I am attempting to get this to run step at a time and maybe learn something within this process.

I have followed online instructions for created a router here;
           [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
As well as creating a dhcp here;
           [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
I have also followed other online instructions that I can't recall at the moment.

At the moment I have a windows 7(64bit) station connecting by way of a static ip setup with no Internet access.  I receive an error message "DHCP is not enabled for "Local Area Connection"".  When I configure the windows box to connect to the cisco router it works fine.  So I am of the opinion that I am missing something or some settings are incorrect on the ubuntu side of things.  I have tried to keep the numbers consistent for both but I am unsure and I am a bit confused for I have created several files and scripts that I had to re-edit with each additional instruction.  Currently I have no idea how to check everything to make sure everything matches and everything works together.  I would be grateful for any help with this and I thank you in advance.

---

### Post by ElderSyrinx on 2012-02-21
...additional information

applications installed thus far;
docky
compizconfig-settings-manager
samba
ethtool
glade
python-glade2
system-config-samba

ifconfig information for today;
eth0      Link encap:Ethernet  HWaddr fc:75:16:5f:03:02  
          inet addr:10.152.187.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::fe75:16ff:fe5f:302/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1704028 (1.7 MB)  TX bytes:27119 (27.1 KB)
          Interrupt:18 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4d:06:96:ee  
          inet addr:192.168.2.17  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe06:96ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27783 errors:1 dropped:0 overruns:0 frame:1
          TX packets:4365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7534516 (7.5 MB)  TX bytes:674558 (674.5 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16819 (16.8 KB)  TX bytes:16819 (16.8 KB)

---

### Post by drdos2006 on 2012-02-21
You might be better off to install Zentyal where most of the settings are semi-automatic but can be altered with a GUI. Zentyal is based on 10.4 Long term Support ( as far as I remember ).
Here is a screenshot of the GUI and features.
[http://trac.zentyal.org/wiki/Features](http://trac.zentyal.org/wiki/Features)


Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

When you read Debian in the HOWTO, think Ubuntu.

( IMHO I think Digital Research DOS was the best OS for PCs )

regards

---

### Post by ksudbury on 2012-02-21
ElderSyrinx, have you setup NAT on your Ubuntu box? 

If so and you have the routing sorted out you should be pointing your windows boxes default route at your internal NAT IP address on the Ubuntu router.

---

### Post by mbuell on 2012-02-21
First - I feel your pain. Been there, still trying to do that. Setting up a router is not dead-simple. Neither am I an expert - but I've been mucking about trying to get various things working for the past few years in Linux and Ubuntu - so I think I might be able to add something useful.

1. Check both the router machine and workstations - disconnect from the outside, and turn OFF any firewall settings until you get the router running to your satisfaction. When all is running, then restart any firewalls (win) or firewall settings (linux side). Firewall settings on your router: using iptables is, by itself, a full semester course. UFW, GUFW (Ubuntu supported) and Firestarter (in the repos, but not supported for Ubuntu) work nicely to help you manage iptables, but it can still be extremely problematic. 

2. Judging from the error - DHCP is not working on your custom router. Can you ping the box from the workstation? I think you are on the right track, thinking that you have missed a setting somewhere. Probably for the DHCP server.  

Next: 
> Gateway/Router = Ubuntu 11.10 64bit (desktop version not the server version, bad choice?) Afaic, no big deal. You will have some extra packages installed, and extra services you will want to shut down. Running the gui creates extra machine overhead. Ultimately you don't want that, but there is a good chance it will never make enough difference that you would care. It sounds like we are talking a light load to begin with - 16 workstations.  Far more important are extra services that will be running - each running service creates another security risk. But, for the most part, these things will be small problems to resolve. And they will create only a little extra risk which you will manage by shutting them down before you put this thing online. The gui has tools that will accelerate your ability to get this running. 

However, I see you mention having installed Samba or samba tools - which means you're thinking of using the same box as a file server. Now, maybe I am wrong, but the LAST thing I would think was appropriate is using the same box as my outside contact to do ANYTHING inside the network. I mean NOTHING else - not apache, samba, nothing. And, I would definitely revert to the old-style Linux expert usage of multiple partitions and/or multiple hard drives to box out different OS functional areas. A partition for /home, one for /var, etc. If you do get a break-in, it makes it harder or impossible for to mess up everything. For instance - if the intruder managed to execute an endless hard drive write - which is a real-life exploit - it could only fill one partition - and your machine would be that much less compromised. 

For that matter, since you want this thing to run as a server - I have found putting var on its own partition is a good idea because you can fill your hard drive with error logs, without an intruder. 

Now - if I were to revive my "linux-as-router" project, I would seriously consider running the whole thing off a custom CD, and no hard drive at all in the router. If somebody does break in - you can kill the router and reboot and be on your way. 

Next - I don't think I would offer any services to the outside from the router - no ftp, no file services, no http, no mail. I know we have security-type admins around here - so maybe they will pitch $.02 at this - but my understanding is that the router should be dedicated. You poke holes in it to allow outside services, but those holes should go to other hardened targets - your ftp or web or whatever server. 

I apologize that this is not more directly related to your questions - but these are the things I think of when I read about what you are trying to do. 

I agree with the poster who recommended a Linux already assembled as a router. There are a few of these around. Might want to give a couple a shot - just install them and see if the work out of the box. Might save you some headaches. 

Last item - you say your Cisco router is wide open. That seems odd to me. Also, given the low expense of small, high-quality routers today, I don't see much practicality in trying to "roll-your-own", except as a learning exercise. If it is a learning exercise - when you get bogged down, you would do well to find your local Linux User Groups. But, I decided, for me, this particular exercise - creating a router - was simply not worth the amount of time required for me to figure it out. And, at the end of the day, when I got something running - it would very likely have more security holes than the available routers on the market. For your network - you'd have to run some switches to expand your port quantity - but I just bought a Cisco/Linksys router, 4 port, wifi N extreme range (whatever - you know, with bells and whistles). It is replacing a Netgear that an Iphone couldn't connect to. For small networks - meaning less than 100 or so connections - I don't know of any reason not to go with something like them. 

Good luck!

---

### Post by ElderSyrinx on 2012-02-22
Thank all of you for your comments and suggestions.  

I have reinstalled the O.S. to try to configure again slowly while triple checking settings.  This may seem extreme but I am too inexperienced to be sure of resetting everything back to default.  If it works or doesn't I will post again.  

drdos2006:
I am looking into the Zentyal as a possibility.  As in I am downloading it as I write this.   But as I am very limited in my Linux experience I would prefer to stick with what I know so far, which is Ubuntu. I remember going from Fedora to Ubuntu and there was a good amount of time to get adjusted to the change.


Ksudbury:
I have no idea.

mbuell:
I try to keep all firewalls in the off position on all the workstations around here.  It just slows down the machine and causes people to complain that they need a faster computer.  I just go in and remove bugs and viruses as needed.  The Samba that I installed was for a basic workgroup join.  This machine won't be keeping any files or doing any file sharing.  But I like to see it on the network as a first step.  Your suggestion of having all of this on a custom cd is something that I have been thinking about.  I'd just have to learn how to do it properly.  Which would be yet another post from me on here I'm sure.

---

### Post by Cheesemill on 2012-02-22
If you only want to use your server as a firewall and don't specifically need Ubuntu I'd recommend using something like SmoothWall. It can be set up in minutes and has a good web interface for all of its administration.

[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by drdos2006 on 2012-02-22
If Zentyal ( based on Ubuntu 10.4 Long Term Support ) is not an opton there is alos Untangle. Uses 1 Network Interface card to connect to the Internet, 2nd Network Interface card to connect to the internal LAN. From your internal LAN, you could setup another box for FTP operations, rather than have the firewall run FTP for your Window boxes.

[http://www.untangle.com/untangle/features/](http://www.untangle.com/untangle/features/)

Come back when you have your setup running and let the rest of us know how you achieved your outcomes.

regards

---

### Post by wirepuller134 on 2012-02-23
Another vote here for Untangle, easy to setup and operate.

---

### Post by ElderSyrinx on 2012-02-23
I attempted Zentyal.  It locked up and would never find a connection.  I'm sure it was operator error, but none the less I removed it and have placed it in the "no" box.  Untangle and Smoothwall will be next.  Thank you all for the helpful suggestions on my trip to Way Over My Head Land.

---

### Post by BenWuan on 2012-02-23
The woodel guide DrDos posted can do this, page5, I've used it many many times to setup routers.
I would read the whole thing though, skipping pages isn't recommended.

---

### Post by ElderSyrinx on 2012-02-24
_**[COLOR=black]Half way there.  Here is what I've done so far.  [/COLOR]**_


All stations have Internet access at this point.  The basic setup is what was best for me to begin with I think.  Using the "Network Connections" I set eth1 as external with ipv4 settings auto and ipv6 settings ignored.  I set eth0 as internal with ipv4 settings shared and ipv6 ignored.  If I am to understand correctly all I need to do is place the firewall between the two. *** Or am I way off track here?***  On a side note, the Untangle O.S. looked very promising but unfortunately I do not have the training or know-how in IT to get it to do anything other than look impressive on the screen. To all of you who spent their valuable time helping with this "Thank You".  I'm now going to poke around in the firewall world.  There seems to be many to choose from.

I tried to put a diagram of the setup but I think the forum doesn't trust my login yet.  Here is the basics.  Modem -->  Cisco Router -->  Ubuntu Box --> Switches -->  Work Stations.

---

### Post by iponeverything on 2012-02-24
> **ElderSyrinx said:**
> _**[COLOR=black]Half way there.  Here is what I've done so far.  [/COLOR]**_


All stations have Internet access at this point.  The basic setup is what was best for me to begin with I think.  Using the "Network Connections" I set eth1 as external with ipv4 settings auto and ipv6 settings ignored.  I set eth0 as internal with ipv4 settings shared and ipv6 ignored.  If I am to understand correctly all I need to do is place the firewall between the two. *** Or am I way off track here?***  On a side note, the Untangle O.S. looked very promising but unfortunately I do not have the training or know-how in IT to get it to do anything other than look impressive on the screen. To all of you who spent their valuable time helping with this "Thank You".  I'm now going to poke around in the firewall world.  There seems to be many to choose from.

I tried to put a diagram of the setup but I think the forum doesn't trust my login yet.  Here is the basics.  Modem -->  Cisco Router -->  Ubuntu Box --> Switches -->  Work Stations.

creating an access list on the cisco and having it do the NAT be your best route.

---

### Post by ElderSyrinx on 2012-02-24
An access list on the cisco would be awesome, but making any changes on that thing is a pain in the posterior.  It fights you every step of the way and nothing is user friendly except for total block or total freeway.

---

### Post by mbuell on 2012-02-25
> **ElderSyrinx said:**
> I attempted Zentyal.  It locked up and would never find a connection.  I'm sure it was operator error, but none the less I removed it and have placed it in the "no" box.  Untangle and Smoothwall will be next.  Thank you all for the helpful suggestions on my trip to Way Over My Head Land.

(rofl)!

Yeah!  Having attempted to set up a router using Ubuntu myself - and realizing that it just wasn't that simple - I am glad to hear you will invest a little time in some of the distros that are designed to do the firewall thing. With a little handholding by the developers - the firewall/router should be a lot simpler. 

Also, it seems very odd to me that your users were complaining about slow network speeds, and that you attribute that to closed ports. That just doesn't sound right - if I understood you correctly, and this was what you found - that network speeds improved when you opened all the ports on the router - that sounds like a hardware problem. I would definitely get new hardware. Which is what you are doing! 

Good luck.

---

### Post by ElderSyrinx on 2012-02-29
_**Total disaster. **_ Here is what happened.  The "workgroup" here has xp,vista and '7' stations on it.  There are already issues with 7 and xp on this as far as sharing files, random drops and stubbornness abound, and with the ip's coming from a new source 7 and Vista was very adamant about forming a new "home" group and refused to let xp come to the new play house.  Almost each station had a different problem and different solution just to access and trust the new connection which I am still amazed by this.  I never solved the xp's connection problem with either internet access or access to shared files after the new ip's and "home" group.  I wanted to leave the system on dynamic so I wouldn't need to make changes to every p.c. and printer in the building but I'm thinking that this is not going to be the case if this is to be a smooth transition.  I will try to keep posting this misadventure for a warning to others out there like me who are way over their heads and have the attitude of "Hey, how hard could it be".  If there is a way to place this machine between the network and the router without the need to change ip's or cause windows to think that anything has changed I would love to hear about it.  Thanks again for your time and thought in this matter.  

By the way.  I have Ubuntu 11.10 / 64bit at home and I don't think I'll ever go back to windows.  So all of this helps  me learn for the future.  For I am a firm believer that Ubuntu  (Linux) is the future.  And as soon as I can learn enough to have some of our business programs running on here this office will be windows free.  But that is another post altogether.

---

### Post by mbuell on 2012-03-10
To judge from the "workgroup" problems - it sounds to me like an LDAP/master browser issue. 

Here is what I would do - go back to a $150 4-port router - drop a couple of switches between it and the boxes to give you enough ports for your lan. Let that router do the routing and DHCP. Set the ubuntu server up as a file server until you can get some of the network issues worked out. 

Google swerdna and opensuse - swerdna has some excellent pages that discuss, in a clear and understandable manner - setting a local linux box as the master browser. The pages are for opensuse, but the idea is the same, and you should be able to figure out the small technique differences involved. 

The ubuntu wiki pages have some discussion of setting up your server as an NT master browser offering LDAP to your network - resolving all that will probably resolve all that workgroup issue. Look for LDAP and server in the wiki.

I also guess I wasn't clear enough before - when you originally pointed to your users complaining about speed, and then you said that opening the router resolved the speed issue - that just doesn't jive. Something else was going on - and opening the ports somehow sidestepped the real issue. Regardless - dropping a new router in there should still resolve the speed issue.

---

