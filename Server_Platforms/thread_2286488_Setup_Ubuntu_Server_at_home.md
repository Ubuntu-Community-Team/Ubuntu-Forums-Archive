---
title: "Setup Ubuntu Server at home"
date: 2015-07-12
forum: Server Platforms
---

### Post by penuel1310 on 2015-07-12
Hi everyone, I want to setup a Ubuntu server at home. I'm a complete beginner. Please help me. I need to do the following. (please refer to the diagram)

I want to install "Ubuntu Server 12.04" on "Laptop 2" and use it as a web server, file server and sharing. "Laptop 2" will be connected to the Internet via USB modem. and "Laptop 2" should also be able to share its Internet connection with other devices. (I think this can be done using 'hostapd')  

I also want to access the server from "Laptop 1" via Ethernet cable and wireless (for viewing web pages and files stored on "Laptop 2")

Please help me set this up. I'm using a very old laptop as a server (Samsung Sens X10)

---

### Post by TheFu on 2015-07-12
If you are doing a fresh install, 14.04 LTS is really the version that should be deployed today. 12.04 only has 2 more yrs of support remaining.
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

There is so much you need to know to do the things you are asking I don't know where to start.  It really is a steep learning curve for someone completely new to tackle.  You will definitely learn a bunch.

Sounds like you need a router. For someone new to Linux, installing an all-in-one router distro is probably best. It will prevent lots of the tiny mistakes that are likely.  Something like smoothwall or pfsense. Or if you really want to put all the eggs into 1 basket - ClarkConnect (or whatever the new name is).

The first service that anyone at home should get working is openssh-server. That alone provides enough for pretty much any remote access needs: [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) Take a look at that list.  

Enjoy.

---

### Post by ranger12 on 2015-07-14
Well I can take a shot at helping - hopefully. I have a server - client network setup at home. The server is a Dell Pentium 4 machine running 12.04.5 server and I have one dedicated Dell Pentium 4 running 12.04.5 Desktop. I also have a a Lenovo T61 running 14.04.2. It sounds like you want to do something similar, not exactly the same hardware setup, as I do. I have a networked printer on it too as well. I would be willing to share settings in my configuration files if you would like. The laptop running 14.04.2 I don't think you will have to do much configuration on that - I certainly didn't to be able to access my files on the server. Have you made an attempt to install the server software on Laptop 2 yet? You probably should go ahead and use 14.-04.2 server simply since it will give you another 2 years of support. I have not upgraded mine simply because it is working fine and suiting my needs so I don't see a reason to upgrade the server right now. If you have any questions than just ask. It looks like a pretty simple layout you want to use.

---

### Post by penuel1310 on 2015-07-14
Hi ranger12, 
I did install "Ubuntu Server 12.04" on "Laptop 2". It's running all right. I'm setting this whole system up for educational purposes. I really want to learn how servers and clients work in real life. I'll use the server to host web pages and files.. things like that. Please let me know what to do next.

---

### Post by penuel1310 on 2015-07-14
Hi TheFu,
I don't have a router. So is there a workaround? I'm a complete beginner... in using "Linux Server".. I've been using Ubuntu Desktop as my main OS for the last 5 years. I tried setting up pfSense but the installation failed.

---

### Post by ranger12 on 2015-07-14
Okay after looking at your setup again I didn't notice that you were not using a router. I am using a 4 port adsl router/modem in mine. I have never tried it the way you have it diagrammed. Hmm, let me do some research on that one. I would recommend you get a router though. I think that is the usual way to go. I have my server connected by ethernet into my router as well as the one client workstation. In my opinion, it would make things a little less complicated down the road. Oh by the way, educational purposes was the same reason I setup a server-client network also, well there were some other reasons but mainly to figure how to setup this kind of network from scratch myself.

---

### Post by ranger12 on 2015-07-14
Okay so far the tutorials I have seen indicate you need 2 nics on the server machine to set it up as a router although it maybe possible to do it with just 1. Since that is a laptop you might want to get a router/modem.

Okay so far all the tutorials I have seen indicate you need 2 nics to setup a Ubuntu server as a router.

---

### Post by penuel1310 on 2015-07-15
Hi ranger12,
How about just accessing "Laptop 2"'s sever from "Laptop 1" via Ethernet cable. Is that possible?

---

### Post by ranger12 on 2015-07-15
Hmm, well you can take a look at this:

[http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router)

The thing to keep in mind though, is that they are talking about networking 2 machines using Desktop and not one of them running Server Edition. I still think a router/modem setup would be best if you are going to run Server Edition on one of the laptops.

---

### Post by ranger12 on 2015-07-15
This is the diagram of my home network. The only thing I didn't put in was my laptop that is running 14.04.2 LTS but it is not configured as a workstation.
[ATTACH=CONFIG]263226[/ATTACH]

---

### Post by TheFu on 2015-07-15
> **penuel1310 said:**
> Hi ranger12,
How about just accessing "Laptop 2"'s sever from "Laptop 1" via Ethernet cable. Is that possible?

Sure, pretty much anything that can be done in networking can be done on Linux. The harder part is whether it is worth your time for a one-off answer that $20 for a home router will solve, simply, quickly, AND likely with higher security.  If you don't really understand networking, it will be frustrating for you AND for the people trying to help to get things setup.

BTW - there really isn't any difference between "server" and "desktop" - desktop has a GUI and some GUI tools to make life easier when the users don't understand certain things ... er ... like networking. If you do static IPs manually, in config files, as God meant, there is NO difference.

You do NOT need a DHCP server.  You will need to understand basic ethernet and ip protocols, simple routing, a tiny bit about DNS and name resolution and how to setup routing on linux, however.  

Actually - the more I think about this, the easier it becomes - provided you can answer a few questions.
* What is the gateway IP?
* What is the "server" LAN IP?
* What is the "desktop" LAN IP?
* What is the netmask?
* What are the DNS servers you will be using?
* Is the WAN IP static or DHCP from your provider? Do you have 1 IP or a subnet on the WAN side?
* Besides these 2 systems, will anything else need to be on the LAN? Can it work with static IPs or must there be a DHCP server?
* What are the device names for each of the interfaces being used - 2 for the "server" and 1 for the "desktop" please.

When you have the answers to those questions, we can tell you what to type, where.

BTW - I did an ascii diag - if you only have 1 NIC port in the server, then you need a $10 switch to connect the wifi-AP and desktop.
```
WAN
|____USB-Modem
|    |____Server (1 NIC)
|    |    |____switch
|    |    |    |____Desktop (1 NIC)
|    |    |    |____WiFi-AP
```

---

### Post by penuel1310 on 2015-07-16
Thanks ranger12, for the link: ([http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router))
Now I can directly access "Laptop 2" (The Server) via Ethernet cable from "Laptop 1", and it's working all right.

How can I setup a file server? (something to do with 'samba' I think)
Does (/var/www/html) work as the web server?

FYI: I formatted my computer and replaced "Ubuntu Server 12.04" with "Lubuntu 15.04 Desktop"

---

### Post by limbenjamin on 2015-07-16
> **penuel1310 said:**
> Thanks ranger12, for the link: ([http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router))

How can I setup a file server? (something to do with 'samba' I think)
Does (/var/www/html) work as the web server?

FYI: I formatted my computer and replaced "Ubuntu Server 12.04" with "Lubuntu 15.04 Desktop"

There are a number of file servers you can choose from, samba is one of them. Others prefer an NFS server as it is supposedly faster and less resource intensive. 

Relevant thread here : [http://ubuntuforums.org/showthread.php?t=1909625](http://ubuntuforums.org/showthread.php?t=1909625) 

For web server, as a beginner, I would recommend apache or nginx, it is easier to find guides for configuring apache in my opinion. Putting files in /var/www/html will not do anything. After installing and running a web server, that will be the default root directory and all files in that folder will be accessible from a web browser. 

To install a service
```
sudo apt-get install samba
```
```
sudo apt-get install apache2
```

To start a service
```
service apache2 start
```

---

### Post by TheFu on 2015-07-16
Please do NOT use samba for Unix-to-Unix file services. Use NFS or sftp.  The only time to use samba ( CIFS is the protocol) is when Windows is involved.  NFS is faster and storage "feels" like local storage - same permissions, hardlinks, softlinks, it is just better for all sorts of reasons. People stuggle with CIFS permissions issues, but with NFS, if the uid/gid matches across all the NFS systems, it just works.  You can make this happen by manually controlling the /etc/passwd and groups files or using NIS or using LDAP for central management. For less than 5 systems, manually is the easy answer.

Samba is a lowest common denominator solution.  You can run both NFS and samba for the same physical storage to be shared with different clients.  Even with that said, there are times when Samba for Linux-to-Linux file sharing **is** the best answer, but it doesn't happen often - maybe 2% of the time.

For clients like smartphones, I'd strongly suggest sftp. This is secure from anywhere in the world, provided you on'y use passwords. Samba and NFS are not secure outside the LAN without a full vpn.  If you have openssh-server installed, sftp is enabled already.  You should know and use ssh, sftp as a Linux admin. Period.

sftp can be used from almost any client - it is built into all Linux file servers - sftp:// .... android has a few nice free clients. Windows has filezilla and WinSCP.  Be certain to setup fail2ban and use ssh-keys for authentication - don't use passwords.

For a web server, there are 20+ options.  Most people choose apache. Nginx is also popular. People have written simple web servers in bash, perl, python, php, ruby ... C, C++, java, ... you get the idea.  If you don't know what you need, apache is the most common answer. As a learner, that is probably the most useful to learn. I run nginx for the better performance, lower RAM use and easier configuration from a security standpoint.

Did you get the WiFi-AP working?

---

### Post by penuel1310 on 2015-07-16
[[COLOR=#000000]Hi [/COLOR]]("http://ubuntuforums.org/member.php?u=1989256")limbenjamin, samba and apache2 were already installed. Started the service, what should I do next?

Hi TheFu, I tested out sftp, it seems to work fine over Ethernet cable. I can access the files from the other computer.
 I also followed this guide: ([https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-14-04)) and installed NFS. It's working properly!!!

About the Wifi, I shared wifi from Laptop1, using "ap-hotspot". 
I installed "ap-hotspot" on Laptop2 but it didn't work. I get some kind of error (sudo: unknown user:sudo: unable to initialize policy plugin)
Any other way to share Internet over wifi adapter?

---

