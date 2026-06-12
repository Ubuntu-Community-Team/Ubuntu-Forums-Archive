---
title: "Server 8.04 installed, need help"
date: 2008-06-28
forum: Server Platforms
---

### Post by CyberDean on 2008-06-28
I have been trying to get my server functional for three months.  I have been reading, researching, following "HowTo's" etc.

I refuse to give up and go back to -------, or do something else.

I have installed most of the software that comes with the live CD, DNS, LAMP, OpenSSH, PostgreSQL, Print server, SAMBA, Quota, and I even installed Ubuntu Desktop GUI to assist me during my learning of the terminal commands.

I have gone to DynDNS.com and got a domain for my server and installed ddclient, I have installed Putty on my desktop, and I have been pouring over my DSL modem/router/gateway just trying to get the File server working.  Yes, I confirmed that my DSL ISP does not block home servers.

The only thing I can do with my server is login from my desktop using Putty SSH using the IP address.  If I try using the server name, I get back "unable to open connection to --------, Name or service not known",  or if I try to use the domain name I get "connection refused".  After logging using the IP address I can do anything as if I was on the server in terminal mode.

It appears to me that my DSL modem/router/gateway needs some reconfiguring just to get the LAN setup correctly before I attempt to get the "File Server" working on the WAN.  DSL modem/router/gateway is a Seimons Speedstream 6520 wireless ADSL Gateway with the DSL input, two (2) server ethernet connections (eth0 and eth1) and two (2) PC ethernet connections.

Right now I am so confused I do not know which direction to go, I'm not even sure if all the config files are correct.

Anyone daring enough to jump in and help me?  I sure need it. 

Thanks to the brave one.

---

### Post by Uluen on 2008-06-28
I think you need to configure DNS correctly.

You can cheat by editing windows hosts file (WINDOWS\system32\drivers\etc).
Syntax is "hostname IP", like this: "youtub 192.168.1.2".

---

### Post by windependence on 2008-06-28
Uluen is correct here. The problem is you cannot reach your server from inside you lan using the FQDN. You should really put aliases in all your hosts files, on your linux box as well as you Windoze box. On the linux boxes you need to edit /etc/hosts.

On your router, there should be a setting for port forwardng. You need to forward at least port 80 and probably 443 back to the local IP of your Linux server in order to reach it from the outside. You may also want to forward 22, although that is a bit of a securty risk. If you open ssh, you should probably at least change the port to something else like 9000.

Also, just for grins and giggles go to [www.canyouseeme.org](www.canyouseeme.org) and check your ports after you have forwarded them back to your box. Your 80 and 443 should be open if you opened them up. If not, you have a firewall problem or your ISP lied to you.

-Tim

---

### Post by CyberDean on 2008-06-29
Hi Uluen and windependence, /etc/hosts is one of the conf files I am not sure of, and it changes on me somehow.  Here is /etc/hosts yesterday evening -

127.0.0.1       localhost 	localdomain
192.168.XXX.XXX XXXXXXXXX	XXXXXXXXXX.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and here it was later last evening and this morning, and the server was acting very slow and odd, and I made no changes to the /etc/hosts conf file, and I was getting an error message - unable to resolve the host -

127.0.0.1       localhost 	             localdomain
192.168.XXX.XXX XXXXXXXXX.XXXXXXXXXX.com     XXXXXXXXXX.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I changed it back to what it was earlier yesterday, the error is gone and the server is acting correctly as far as I know.

The IPv6 setting were in the default hosts conf file so I did not remove them, what are they for?  How can I tell if my server needs them?

In the network settings I have added the IP following the LocalHost name on eth0 on the server (eth1 I left it roaming) and on both Ubuntu PC's. Prior to today I had set a static IP for each of them from the Gateway router.

When I get into the DSL Speedstream modem/router, login as admin, I go to "Home Network" and select "Configure the Local Speedstream Gateway Server Ports", it shows three (3) Applications with it's respective Port #, HTTP - 80, FTP - 21 and Telnet - 23, I can change and save the port #, but I can't find how to add or delete from this table, and there is nowhere to add the server name or anything.  No other options seem to be the Port redirect.

I hope this helps in some way.  Sorry for not coming back sooner, I was in church this morning and in the field and orchard working this afternoon.

Thanks for any help, I am still confused but I'm willing to work on it till it is finished.

---

### Post by CyberDean on 2008-06-29
Hi windependence, I went to canyouseeme.org and started checking for open ports.  All the common ports checked are not open to include port 80, but how can this be when I am on the web checking the port I am using?

I also used "Network Tools" on the server and did a "Port Scan" of my server and the DSL router, only port 80 is open on the DSL router while ports 21, 22, 53, 80, 111, 139, 443, 445, 631, 1021, 3306 and 43908 on the server.  It appears to me at this time that the DSL router and/or my ISP is blocking my LAN from the WAN.  But if port 80 is detected open by the "Network Tools" "Port Scan", why does canyouseeme.org see it as not open?

I don't understand how I can get conflicting info like this.  Can you explain this to me?  Is there a possibility that a port can be seen incoming and out going or only one way?

Thanks.

---

### Post by Uluen on 2008-06-29
Does your hosts file really look like this *192.168.XXX.XXX XXXXXXXXX XXXXXXXXXX.com*?

It should probably be like this:
"*192.168.1.5  yourhostname*"

You have static IP on the server I assume?

What is the output of *# cat /etc/resolv.conf*?
[I]search yourdomain
nameserver 192.168.1.1[/I]

```
# cat /etc/network/interfaces
```
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1
```


Note, having your Samba server open to the internet without tunneling is a really bad idea.

A port seen as closed may well be open in your router but can be seen as "closed" when no service (IE HTTP for port 80) is responding.

---

### Post by Uluen on 2008-06-29
If nothing on your server is working and you have no data stored on it, I'd recommend reinstalling, planning ahead and having some [documentation]("https://help.ubuntu.com/8.04/serverguide/C/index.html") at hand.

**I usually do like this:**
[LIST=1]
[*]Install minimal, SSHD only.
[*]After install is finished, note the IP in use.
[*]Log in with Putty and change the interface(s) to static (see above) with working gateway.
[*]Restart networking, reconnect with Putty to the new IP.
[*]Apt-get update & upgrade.
[/LIST]

Now you should have a working minimal server running.
Do Apt-get install samba, make sure it's running like it should before adding the next service.

Go slow, one step at the time.

---

### Post by CyberDean on 2008-06-29
> **Uluen said:**
> Does your hosts file really look like this *192.168.XXX.XXX XXXXXXXXX XXXXXXXXXX.com*?

**Yes it does, shows IP address localname localdomain**

You have static IP on the server I assume?  **Yes**

What is the output of *# cat /etc/resolv.conf*?
[I]search yourdomain
nameserver 192.168.1.1[/I]

[B]### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4917
#
### END INFO

search romneysecuredata.com


nameserver 192.168.254.254[/B]


```
# cat /etc/network/interfaces
```


[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.254.4
        netmask 255.255.255.0
        network 192.168.254.254
        gateway 192.168.254.254
[/B]


```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1
```


Note, having your Samba server open to the internet without tunneling is a really bad idea.

**I understand, at this time the server is only up and running when i am working on it, I need to learn to fix this also.**

A port seen as closed may well be open in your router but can be seen as "closed" when no service (IE HTTP for port 80) is responding.

[B]Ok, understand.

Thanks, hope this info helps.[/B]

---

### Post by CyberDean on 2008-06-29
Hi Uluen, I have reinstalled the server software at least 4 times, the last two times following [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) .  But I continue to have the same problem of checking everything out or even get started to.

You are correct, I have no data on the server at this time, another reinstall will not hurt, but will it help?

I have completed the steps you list, noteing the info, set IP to static, update interfaces and restart the network.  Updated and upgraded and all and still ended up where I am today.

I apologize if I sound frustrated, I agree with your method and I have basically followed it many times.  I must not understand some terminalogy, method, or something, because I must be making the same mistake over and over and don't know enough about linux software and setting up a server to save myself.  I am learning and will not give up on this.

I really appreciate you trying to help me.

---

### Post by windependence on 2008-06-30
Please do NOT reinstall. It is not necessary and this is not Windoze :)

In order for your port to be seen from the outside, there must be something listening on your LAN like your web server. Please note that there is still a chance your ISP is blocking 80.

I am almost positive your problem is with your router and forwarding your ports back to the server. Can you take a print screen of your router config page? What make and model router do you have. Most routers, besides having the "standard" applications will let you add your own custom apps to the ruleset so that you can forward each port to the server of your choice on your LAN. Of course constanly reinstalling things fixes none of this. :)

-Tim

---

### Post by CyberDean on 2008-06-30
> **windependence said:**
> Please do NOT reinstall. It is not necessary and this is not Windoze :)

In order for your port to be seen from the outside, there must be something listening on your LAN like your web server. Please note that there is still a chance your ISP is blocking 80.

I am almost positive your problem is with your router and forwarding your ports back to the server. Can you take a print screen of your router config page? What make and model router do you have. Most routers, besides having the "standard" applications will let you add your own custom apps to the ruleset so that you can forward each port to the server of your choice on your LAN. Of course constanly reinstalling things fixes none of this. :)

-Tim


I am running Ubuntu 8.04 and have not found the solution to screen print,
but here is the router info:

System Type:	  	                      SpeedStream 6520 Series
High Speed Internet Connection Information:   UP
Router IP Address:	  	              192.168.254.254
WAN IP Address:	  	                      74.46.247.91
Firewall:	  	                      Off
Config Part #:	  	                      003-8102-G05
Firmware Part #:	  	              004-E752-A8R
MAC Address:	  	                      00:18:D1:69:57:8F

under ISP Connection there is:

     Configure the ATM Virtual Circuit

     Add Static Routes for direct IP Connections

     View the current Routing Table

     Set up Dynamic DNS



under "View routing table" is
     	
	Current Routing Table

	
	This is a listing of all currently mapped routes in the SpeedStream Gateway. It shows both static and dynamically learned routes.
Destination	Netmask	Gateway	Flags	Metric	Interface
127.0.0.0	255.0.0.0	127.0.0.1	 	1	lo0
192.168.254.0	255.255.255.0	192.168.254.254	 	1	LAN
74.46.247.91	255.255.255.255	74.46.247.91	 	1	PPPoA(0) 0/35
Default Gateway	-	74.47.212.1	 	5	PPPoA(0) 0/35
Flags legend: (R)ip route, (S)tatic


under "Add Static Routes for direct IP Connections" is

	
	Static Routes
	
	

	Your SpeedStream Gateway can set static routes to map connections from your home to the Internet directly.
	Currently Configured Static Routes
	
	
#	Destination	Net Mask	Next Hop	Interface	Edit	Delete
Static Route list is empty.
View the current routing table...

	Add Route
	
	
Destination	Net Mask	Next Hop	Interface
			

I am not sure as how to set this up.

I'll look for additional info if needed.

Got to get ready for work, Thanks.

---

### Post by windependence on 2008-06-30
You originally said:

> When I get into the DSL Speedstream modem/router, login as admin, I go to "Home Network" and select "Configure the Local Speedstream Gateway Server Ports", it shows three (3) Applications with it's respective Port #, HTTP - 80, FTP - 21 and Telnet - 23, I can change and save the port #, but I can't find how to add or delete from this table, and there is nowhere to add the server name or anything. No other options seem to be the Port redirect

This is the screen where you can configure your port forwarding. Let me see if I can find any info on how you add a custom entry to the table. I guess if you can change the port number it really doesn't matter what they call the application, but still there should be a way to add custom entries.

-Tim

---

### Post by CyberDean on 2008-06-30
> **windependence said:**
> You originally said:



This is the screen where you can configure your port forwarding. Let me see if I can find any info on how you add a custom entry to the table. I guess if you can change the port number it really doesn't matter what they call the application, but still there should be a way to add custom entries.

-Tim


Take a look at this web site, is this what I need to understand -

[http://portforward.com/english/routers/port_forwarding/Siemens/Speedstream-6520/eMule.htm](http://portforward.com/english/routers/port_forwarding/Siemens/Speedstream-6520/eMule.htm)

Thanks

---

### Post by windependence on 2008-06-30
That's exactly what you need to do except substitute your application for the emule entries and you ports you want to open. So, to recap you want to click on Add a bypass Entry, and follow the steps, but do one for port 443, you can call it https, and add one for ssh (there might be one in the table already) and use the IP address of your server where it says "redirect selected prtocol to IP address". Protocol should be TCP/IP Don't forget to save the config by hitting Apply.

-Tim

---

### Post by CyberDean on 2008-06-30
> **windependence said:**
> That's exactly what you need to do except substitute your application for the emule entries and you ports you want to open. So, to recap you want to click on Add a bypass Entry, and follow the steps, but do one for port 443, you can call it https, and add one for ssh (there might be one in the table already) and use the IP address of your server where it says "redirect selected prtocol to IP address". Protocol should be TCP/IP Don't forget to save the config by hitting Apply.

-Tim


Back again.  I'm in my Speedstream 6520 setting port forwarding, this box has very limited capabilities for forwarding, maybe one protocol can be used for multiple ports.  All it has is DNS (for domain), FTP, HTTP, Telnet, SNMP, SMTP and PPTP.

I setup for domain, UDP  DNS port 53; TGP  FTP port 21; and TCP HTTP port 80 for HTTPS port 443. Enabled all three, applied the changes and rebooted the router.

Be back later, terrible thunder storm just hit this area.

---

### Post by mrpeenut24 on 2008-06-30
If you click on "add a custom entry", you can add ...a custom entry... with the port you want.

---

### Post by CyberDean on 2008-06-30
Back after the storm, I have also enabled port 22 and 443 to my server only using protocol and port number on the router.  Everything applied and router rebooted.

Attempted to Putty into my server using the domain name and the connection timed out.  Using the server name failed also, service unknown.  But as always, using the IP address immediately gets in, I login and use Putty as a terminal access.  I'm getting the feeling that Putty only uses an IP address, is this true?

I need to do some more checks, be back soon.

Thanks to everyone.

---

### Post by windependence on 2008-07-01
No. PuTTY will use the server name or domain also. The problem is you are trying to access your server from your LAN, and you need to set up DNS on every machine on the LAN that you are trying to do this from. If you test this from outside your network I am pretty sure it will work no problem.

Now, let's fix your DNS problem so that you can access the server from the LAN first.

First, do:

```
sudo cat /etc/hosts 
```

On the box that you are puttying FROM, NOT the server and post the results here.

Also, se if you can ping the server by name from the computer you are puttying from.

```
ping servername
```
Post what happens.

-Tim

---

### Post by CyberDean on 2008-07-01
First, do:

```
sudo cat /etc/hosts 
```

On the box that you are puttying FROM, NOT the server and post the results here.

[B]holyspirit@holyspirit-desktop:~$ sudo cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	holyspirit-desktop 192.168.254.3

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
holyspirit@holyspirit-desktop:~$[/B] 


Also, se if you can ping the server by name from the computer you are puttying from.

```
ping servername
```
Post what happens.

[B]holyspirit@holyspirit-desktop:~$ ping ubuntursd
ping: unknown host ubuntursd[/B]


Off to work, back later.

Thanks

---

### Post by windependence on 2008-07-01
What is your **server's** local IP address on the LAN and I'll write a new hosts file for you to use.

-Tim

---

### Post by CyberDean on 2008-07-01
> **windependence said:**
> What is your **server's** local IP address on the LAN and I'll write a new hosts file for you to use.

-Tim

Server's name - ubuntursd
Server's domain name - romneysecuredata.com
server's static LAN IP - 192.168.254.4

Thanks Tim, Dean

---

### Post by mrpeenut24 on 2008-07-01
```
127.0.0.1    localhost
127.0.1.1    holyspirit-desktop 192.168.254.3[B]
192.168.254.4 romneysecuredata.com
192.168.254.4 ubuntursd[/B]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```Add those two bolded lines to the /etc/hosts file on each computer you wish to access the server from.

---

### Post by CyberDean on 2008-07-01
Thanks to all that have helped in this thread, I am now able to log into my server from my Ubuntu PC's on the LAN.  I have learned a lot and will use this to go further, and maybe soon I will be able to help someone else.

There is much more to do, and I will work on it.

THANKS - Dean

---

### Post by windependence on 2008-07-01
Good deal! I told ya we'd fix it. You're welcome.

-Tim

---

### Post by mrpeenut24 on 2008-07-01
Glad to have helped.

---

### Post by CyberDean on 2008-07-01
It has been a long day here.  I now grasp the concept of port forwarding on a router, whether it is a DSL router or not, but the DSL Speedstream 6520 that I have, as I said prior, does not have all the "services" listed to choose from when port forwarding.  As an example, SSH uses protocol TCP (my router does not have SSH or TCP/IP to choose from) but it is normally setup with port 22.  What I did was to choose TCP and port 22 for SSH operation. If I wanted to change the port for SSH to, say 722, do I choose TCP and port 722?  Or is there a better more correct way to change from the normal port? 

Thanks

---

### Post by mrpeenut24 on 2008-07-02
That's exactly right.  You may also be able to do what's called port triggering.  In this instance you would accept the incoming connection on port 722 and forward the connection to port 22.  That way you don't have to reconfigure the ssh daemon.  It looks like your speedstream doesn't accept this option, however, so doing what you were saying may be the best option.  What you *may* be able to do is, in the same place you were forwarding ports, configure it like so:

```

Protocol: TCP
Port: 722
Forward to ip address: 192.168.254.4:22

```

However, this is likely to not work.  Give it a try anyway, and let us know what happens.

---

### Post by CyberDean on 2008-07-02
Thanks so much mrpeenut24, a few days ago I was so confused and you all have helped but a lot of it together for me.

I am back at work and will install Putty on one of the windows PC's and try Puttying into my server from the internet, and when that works I will move on.  One thing at a time.  Last evening I was searching around the server and started finding the config files for  the software that uses the router, like ssh_config and how it is config to use port 22.

Thanks again, I'll let you all know how things go.

Have a great day.

---

### Post by mrpeenut24 on 2008-07-02
No problem!  Everyone here was once where you are.  It's people like you who are the future of linux.  I'm just doing my part to give back to a community that has done so much for me.  I'm sure everyone here is more than happy to help you however they can.  Keep up your inquisitive nature and feel free to ask for help along the way.

Let us know how it goes and if you need any more help with this.

---

### Post by CyberDean on 2008-07-02
Well, connecting to my server from the WWW appears not as easy as I thought.  No connection, time out.  Went home for lunch to check the IP address coming into the router from the WWW and now I'm trying to verify what IP address DynDNS has in thier database seeing that I'm using ddclient.  I also read somewhere if the router has DNS and connected to DynDNS the two of them could be in conflict.  Looked through the router setups, and yep, there it was, was cause I disabled it and rebooted the router to see if ddclient would update DynDNS.  Back at work and still can not log into my server using Putty, trying both IP address and domain name. 

I am also in contact with DynDNS to confirm my IP address on record there.

What else could it be?  I also looked for the log file for ddclient but could not find it, any ideas?

Thanks

Just confirmed the IP address at DynDNS was not the correct IP address, updated manually.  Now to give it time to go through the system, and by then my IP address will probably change.  But that shows me that ddclient was not updating DynDSN.  I will look at it this evening and confirm the DNS is turned off on the router.

What effect would the DNS software in Ubuntu 8.04 server software have on ddclient?

---

### Post by CyberDean on 2008-07-02
> **mrpeenut24 said:**
> That's exactly right.  You may also be able to do what's called port triggering.  In this instance you would accept the incoming connection on port 722 and forward the connection to port 22.  That way you don't have to reconfigure the ssh daemon.  It looks like your speedstream doesn't accept this option, however, so doing what you were saying may be the best option.  What you *may* be able to do is, in the same place you were forwarding ports, configure it like so:

```

Protocol: TCP
Port: 722
Forward to ip address: 192.168.254.4:22

```

However, this is likely to not work.  Give it a try anyway, and let us know what happens.

Hi mrpeenut24, while I was in my Speedstream 6520 this evening I looked at the IP setups for adding the port number after the IP address.  As it is setup, will not work due to an apparent maximum characters in the field for the IP address, b-u-t, there are also two (2) more IP address options to choose from.  One of the options the IP address starts at 10.0.0.0, only a total of 8 characters.  I realize it represents a total of 15 characters, but we are not talking about representing all of the characters, only using 8 in the IP field.  That gives me 7 characters I might be able to use to designate the port number.  That will be something to think about after I get this server, and myself, straight on what I'm trying to do, and have nothing else to do but play with the Speedstream, but not today. 

Have a great day.

---

