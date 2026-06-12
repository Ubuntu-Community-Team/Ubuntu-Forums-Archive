---
title: "New Network Design"
date: 2007-08-10
forum: United Kingdom Team
---

### Post by Beamerboy on 2007-08-10
Hey Peeps,

Towards the end of this year my local exchange will be ADSL2+ capable via Be which is great because on their Pro Package I can switch to a 2.5Mbit/s upload spead.

Obviously I need to upgrade my home network for adsl2+ as my current router doesn't support the adsl2+ specification.  So I am starting to consider the best way to go about it.

There will be a number of considerations to take into account for the new network as follows:

[LIST=1]
[*]VOIP
I am planning on switching all our telephony to VOIP using Asterisk.
[*]Gigabit LAN
I would like to upgrade the LAN to 1000Mb/s (switched) so I can set up a nice multimedia network throughout the house.
[/LIST]

**What I already Have**
[LIST=1]
[*]1000 Feet of Cat5E Cable
[*]Cable Ends and Covers
[*]Digital Cable Tester
[*]Crimpers
[/LIST]

**What will be on the network**
[LIST=1]
[*]HTPC in the lounge running Edubuntu and MythTV Frontend
[*]My Desktop Machine (inc MythTV Frontend)
[*]Main Server (Web, Mail, MythTV Backend, Asterisk Server)
[*]2 HTPC's in the Bedrooms (inc MythTV Frontend)
[*]Wireless Access Point
[*]My iPAQ Web Server
[*]NFS Server
[*]Wii
[/LIST]

The 3 HTPC's and NFS Server will be on a separate Gigabit (or gigE if you prefer) private subnet in the 192.168.0.0/24 range and I will refer to this as the Family LAN from now on.

The desktop will be on a Static Public IP and will be bridged to the Family LAN through a second Gigabit NIC.

The Main Server will also have a Static Public IP and a bridge to the Family LAN

The iPAQ will have a Static Public IP and a bridge o the Family LAN to access NFS.

The Wii will have a Static Public IP

The switch for the Family LAN will have a Public Static IP and will manage the DHCP for the Family LAN.

**What I think I need.**
[LIST=1]
[*]4 Port Gigabit Switch for Family LAN
[*]8 Port ADSL2+ Modem Router GigE
[*]PSDN Card for the Asterisk Server
[/LIST]

So firstly can anyone recommend a decent 4 port Gigabit switch preferably with a decent firewall, SNMP and QoS so I can manage the bandwidth for VOIP and Multimedia.  I will want Video on the VOIP channel too, so decent QoS software is kind of important.

Secondly, I haven't been able to find any 8 Port ADSL2+ Modem Routers which also have GigE.  Again, I would like a decent firewall, decent QoS and SNMP.

Finally this is going to be the first time I have played with VOIP at any serious level, so can anyone recommend a good  psdn card (we only have 1 incoming line)  that is fully compatible with the UK phone network and Asterisk?

If anyone else can think of anything I have missed, please let me know :)

Paladine

---

### Post by Beamerboy on 2007-08-10
OK I am trying to figure out the best way to utilise my existing hardware too, so this is what I am thinking.

Currently I have a nice server doing pretty much nothing, it has the following specs:

Tyan Thunder K7 Dual Socket 462
2x Athlon MP 2200
2x 1GB ECC Registered PC2700 RAM
2x 120GB PATA Drives

Now currently on my desktop system I am running Apache2, Courier+Postfix, MySQL, NFS and Myth Back End/Front End.

I am finding this tedious at the moment because I evade doing gutsy updates because of the risk of downtime if something breaks, and obviously I don't want downtime on my web/mail/nfs/mythtv services.  So I was thinking of turning the desktop back into a desktop instead of a server.

So I am thinking of making the following changes to the server mentioned above:

Adding 5x 73.5GB 10k RPM SCSI Drives on one of the SCSI channels.  This would be used for the MythTV file storage including tv recordings, mp3s and digital photos.  Myth Back End would be moved to this server and be used by multiple Myth Frontends for video, music and photo galleries.  I would also add 3x Hauppauge PVR250 PCI cards which would give MythTV 3 capture sources.

Adding another 5x 73.5GB 10k RPM SCSI Drives onto the second SCSI channel.  This would be used for NFS (specifically /home and the doc tree for the iPAQ webserver), Asterisk, MySQL, Apache2, Postfix, Courier-imap.

Then on my desktop I could add 4x 500GB SATA II Drives and run them over NFS as a Video Archive.  Basically I would set it up so that anything recorded in MythTV would stay on the SCSI array for 60 days, at which point it will be transcoded to mpeg4 and archived to the 2TB SATAII array using the MythArchive plugin and accessible via the MythVideo plugin).  I could use one of my existing 250GB SATA I drives for my normal desktop system and my second 250GB SATA I drive as a backup drive for the NFS /home partition, mail, mysql databases, logs and configuration files and of course web.

Sounds like a much more sensible setup than I have at the moment, what do you guys think?  At least that way the web/mail/nfs and mythtv services would not be at the mercy of my desktop updates, I would have more than enough storage/backup storage and a kick*** multimedia server.

Paladine

---

### Post by Viruk on 2007-08-13
If you have that amount of kit why don't you get an ADSL 2 modem, forget the router and set up a smoothwall (or similar) and use that to perform the router functions. 
I mention smoothwall as I have used it for about 3 years and have had no problems with it and its fast and easy to set up. I know you can do plenty with a linux server with the right services set up on it but I can't really help you there as I've never needed to look into it. Regardless of the choice of software you can probably do more (and for less cost) by setting up an old computer to perform the tasks of the router. 

You can slap a couple of extra network cards in the gateway computer and you can segregate the zones in your network to cover a DMZ for servers with external access, a trusted zone for your main computers and you can even put the wireless AP into its own zone so anyone who might have a go at your wireless would be "contained" without getting at any non-wireless areas of your network. 

> The desktop will be on a Static Public IP and will be bridged to the Family LAN through a second Gigabit NIC.

The Main Server will also have a Static Public IP and a bridge to the Family LAN

The iPAQ will have a Static Public IP and a bridge o the Family LAN to access NFS.

The Wii will have a Static Public IP

The switch for the Family LAN will have a Public Static IP and will manage the DHCP for the Family LAN.
You will usually only get 1 static public IP - do you just mean you will assign a static IP manually for these devices?

A smoothwall (or alternative) could do your dhcp so you don't have to worry about assigning IP addresses to all your machines, although you would still have to assign IPs for anything in your DMZ due to the port forwarding rules required for servers that accept incoming connections from the internet.

---

### Post by Beamerboy on 2007-08-13
> **Viruk said:**
> If you have that amount of kit why don't you get an ADSL 2 modem, forget the router and set up a smoothwall (or similar) and use that to perform the router functions. 
I mention smoothwall as I have used it for about 3 years and have had no problems with it and its fast and easy to set up. I know you can do plenty with a linux server with the right services set up on it but I can't really help you there as I've never needed to look into it. Regardless of the choice of software you can probably do more (and for less cost) by setting up an old computer to perform the tasks of the router. 

You can slap a couple of extra network cards in the gateway computer and you can segregate the zones in your network to cover a DMZ for servers with external access, a trusted zone for your main computers and you can even put the wireless AP into its own zone so anyone who might have a go at your wireless would be "contained" without getting at any non-wireless areas of your network. 


You will usually only get 1 static public IP - do you just mean you will assign a static IP manually for these devices?

A smoothwall (or alternative) could do your dhcp so you don't have to worry about assigning IP addresses to all your machines, although you would still have to assign IPs for anything in your DMZ due to the port forwarding rules required for servers that accept incoming connections from the internet.

I would prefer an adsl modem router, it uses very little power, takes up very little space and works fine.  I have plenty of kit to setup a linux router using existing hardware but there is the size and power usage downside.

I actually have a /29 subnet with 8 public IP addresses (5 useable) and rDNS but whenI switch to ADSL2+ I will either stick with the current /29 or I will go for 16 static IPs.  I don't like running NAT because I hate the hassle involved in port forwarding and it does create a bottleneck, thats why I pay for a block of public IPs instead and have done for 5 years now.  I need a public IP for my desktop, public IP for the iPAQ, public IP for the mail/web server and a public IP for the Family LAN switch.  The switch routing the family LAN will probably run NAT unless I decide to go with 16 IPs because they won't be running any services so they will be fine with passive routing.  But ideally I would prefer they had their own public IPs so I just need to come to a decision on cost with regards to whether I want the extra cost of an extra 8 IPs.

Paladine

---

### Post by Beamerboy on 2007-08-13
I have been having a bit of a think anyway so I am probably going to go for something like this:

[indent]
Main Server: Dual Athlon MP 2200's s462, 2GB ECC Registered RAM.

I will be upgrading this machine with a PCI GigE NIC, 2x DVB-S Tuners, 1x PSDN Card and 1x 4 Port SATA Controller (PCI).

That will use up all 5 of my available PCI slots.  I would have preferred to use one of the 2 SCSI channels (or both) to setup the disk array, but the cost of SCSI disks compared to SATA simply makes it more viable to get a SATA controller.

This box will run as:
[INDENT]
Mail Server (SMTP and IMAP)
Web Server for Blog, Gallery and other projects
Asterisk Server
MythTV Master Backend Media Server
NFS Server
[/INDENT]
[/indent]
[indent]
My Desktop
AMD Athlon 64 X2 4400+ Toledo Core, 2GB DDR400, Dual Graphics and Dual LCD.

This box will run as
[indent]
A desktop instead of server
MythTV Frontend
[/indent]
[/indent]

Then the HTPC in the lounge will get another 2 DVB-S tuners and will run as a MythTV Slave Backend, giving us a 4 tuner MythTV system.  It will also run MythTV Frontend.  The whole system will be plugged into the HD LCD TV.

The two HTPC's in the bedrooms will just be regular Ubuntu boxes with MythTV Frontend running, the displays will be HD LCD TVs.

The iPAQ will continue to run as its own web server for the LiPAX project.

There will be 2 networks, the main network running on Public IPs and then the inner network running on gigE and either NAT'd to Private IP space or running their own Public IPs.

I think thats about the most sensible setup I can come up with at the moment.

Paladine

---

### Post by Johnathon on 2007-08-15
For asterisk, try and get one that is supported by the zaptel  or libpri drivers. You *really* don't want to have to try to get some of the less-popular cards working. (It took a SVN build of the misdn drivers to get one of our cards to work :()

---

