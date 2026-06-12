---
title: "web development office running Ubuntu"
date: 2013-02-19
forum: Server Platforms
---

### Post by Kanhai Patel on 2013-02-19
Hello Guys, 

I am comparitively new to Ubuntu (i.e. less then 1 year experience), but i have started liking it a lot. It seems to be the perfect platform for development of PHP applications and websites. 

The main reason to start this thread is I want more information on how I can setup Ubuntu Server/Desktop in my office. 

We have about 7 computers at our office, both desktops and laptops. All are connected to a wifi router via USB wifi cards and the wifi router is connected to a ADSL modem. 

All PCs are almost independent right now and this is what I would like to change. What I want is to:

1. Control the internet access (create a proxy server or similar which helps me block few websites etc. and check the usage)

2. Install PHP, Apache on one server and MySQL on another server (for load sharing).

Also, I would like to inform that we use NetBeans for the development and SVN for maintaining the files. So Is it possible for me to make all the PCs connect to one central file location and work from there instead working on their localhost?

Looking forward for your responses..

Thanks in advance.
Kanhai Patel

---

### Post by lykwydchykyn on 2013-02-19
> **Kanhai Patel said:**
> 
1. Control the internet access (create a proxy server or similar which helps me block few websites etc. and check the usage)

Squid proxy server, and maybe an add-on like Squidguard, should get you going on this.  See this for a start: [https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)

> 
2. Install PHP, Apache on one server and MySQL on another server (for load sharing).

Shouldn't be a problem.  You just need to make sure MySQL is listening on the server's IP rather than the loopback address (the latter is default).  Then your PHP apps just need to point to the other server in their connection strings.
> 
Also, I would like to inform that we use NetBeans for the development and SVN for maintaining the files. So Is it possible for me to make all the PCs connect to one central file location and work from there instead working on their localhost?

Install openssh-server (if it's not installed already) and use svn+ssh to access a shared folder.  Should work fine.

---

### Post by SeijiSensei on 2013-02-19
> **Kanhai Patel said:**
> 
1. Control the internet access (create a proxy server or similar which helps me block few websites etc. and check the usage)

Do a Google search for "[squid transparent proxy]("http://www.lesismore.co.za/squid3.html")" and follow the instructions you find to install Squid on a box with two network cards.  Connect one side to the Internet and plug your current wifi router into the other.  Make the proxy server the wifi router's default gateway.  Now all the traffic will go through the server and be managed before going out on the Internet. You'll need to add a few simple iptables rules to "[masquerade]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29")" all non-HTTP traffic out to the Internet.  

Squid has a rich "access control language" which uses allow/deny rules attached to regular expressions that can match various parts of a URL request.  The proxy I manage has many lists to permit or block URLs by target domain, request method, requesting IP, file extension, etc.

> 2. Install PHP, Apache on one server and MySQL on another server (for load sharing).

That's not really necessary.  None of those impose large performance costs in a web development context.  I'd put them all on the same box you use to run Squid.  Any modern computer has more than enough processing power for all of that and then some.  For instance, you could easily add a mail server to this box, too.  Having the MySQL server on the same box as Apache and PHP is more secure (since you are using the localhost interface for all the DB transactions).  It also doesn't create a second point of failure if the DB server goes offline or falls off the network for some reason.  

> Also, I would like to inform that we use NetBeans for the development and SVN for maintaining the files. So Is it possible for me to make all the PCs connect to one central file location and work from there instead working on their localhost?

Sure.  For ordinary shared directories you can use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for Linux clients and [Samba]("https://help.ubuntu.com/community/Samba") for Windows clients.

You can put the SVN repository there, too, of course.  If you ever switch to git, that is supported as well.

I suggest you start by browsing the [Server Guide]("https://help.ubuntu.com/12.04/serverguide/").

---

### Post by ranger12 on 2013-02-19
Yep, I agree with SeijiSensei. The best place to start is with the server guide. I used that for setting up my home lan. I do not have as many clients as you do(Only 1 at the moment) but I do have a solid base for expanding it if I choose.  I use autofs and NFS for mounting users home directories on the client and it works very well. I also have DNS, openLDAP, Samba(set up as a PDC), NTP and who knows what else:;:) all on the same box.  Your needs of course are different than mine.

---

### Post by Kanhai Patel on 2013-02-20
Hello, Thanks to all for their responses.

One query tho... 

> **SeijiSensei said:**
> Do a Google search for "[squid transparent proxy]("http://www.lesismore.co.za/squid3.html")" and follow the instructions you find to install Squid on a box with two network cards. 

Can I use a Wifi USB dongle instead for connecting to the wifi router? or even better, can i make my pc into a wifi router using the USD dongle?

Kanhai

---

### Post by SeijiSensei on 2013-02-20
You could, but why bother?  I presume the router you use now connects directly to the Internet over an Ethernet cable (unless it uses a direct DSL connection).  If your router connects over Ethernet, it's a lot easier just to put a second network card in the proxy server and connect your current wifi router to that so the proxy sits between the wifi router and the Internet.  Why reinvent the wheel when you already have a device that does what you need?

---

### Post by Kanhai Patel on 2013-02-20
> You could, but why bother?  I presume the router you use now connects  directly to the Internet over an Ethernet cable (unless it uses a direct  DSL connection).  If your router connects over Ethernet, it's a lot  easier just to put a second network card in the proxy server and connect  your current wifi router to that so the proxy sits between the wifi  router and the Internet.  Why reinvent the wheel when you already have a  device that does what you need?     I believe you and i will move ahead with this solution. The only concern is that if I do this, then all the connection will be in the same IP table correct?

Kanhai

---

### Post by SeijiSensei on 2013-02-21
I see your concern.  It depends on whether the wifi router can be configured simply as a router without network address translation ("masquerading").  If so, then it will preserve the source addresses of the client machines.  If not, then I can see an argument for replacing the router with the proxy server.  In this case, I'd recommend using a [wifi bridge]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833168104") In this arrangement. You'll still need two Ethernet cards in the box, one to connect to the Internet router and one to connect to the bridge.  You'll also need to run **isc-dhcp-server** on the Linux box to assign addresses to the client workstations.  

I suspect you could build a bridge with a regular wifi adapter and the bridging code in Linux, but sometimes it's just easier and more reliable to use a specialized hardware component.

---

### Post by Kanhai Patel on 2013-02-26
Hello, Sorry for late reply, I was trying to cinfigure everything on the new machine and I must say, with your help I was successful in doing so. 

So here is how its setup:

I installed Ubuntu 12.04 LTS on the main machine. On it i installed webmin. Via the webmin I installed DHCP server, DNS server, Firewall, Squid server. This machine has 2 LAN cards. eth1 connects to the ADSL+ router (AUTOMATIC DHCP). eth0 connects to the internal network (Static IPs). This card is connected directly to the wifi router (all my PCs in network has wifi cards). Wifi router does not provide ip addresses, the server does that.

When a PC connects, the server assigns IP address to that machine, the proxy is transparent (i.e. all connection to port 80 is forwarded to port 3128 of the proxy server and this is done by the firewall installed) All other important ports are forwarded directly like ftp, https etc. 

We have been testing it since last 24 hours and all seems to be working well (except of few glitches on other PCs like mysql etc.)

I really appreciate your help with this. 

Do let me know if you have any questions for me or the setup.

Thanks and regards,
Kanhai

---

