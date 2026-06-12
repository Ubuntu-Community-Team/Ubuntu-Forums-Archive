---
title: "What does your home network look like?"
date: 2008-03-16
forum: Server Platforms
---

### Post by Uaine on 2008-03-16
I'm trying to get a good idea for how to structure my home network. I currently have a system that is kind of a jack of all trades.  It's basically:

Internet
 |
[gateway-firewall-webserver-mailserver-fileserver]
 |
PCs

I have a feeling this isn't very secure, even with my decent iptables rules.  I'm considering splitting the functionality up among 3 machines.  Something like:
```

      Internet
           |
  [gateway-firewall] --[webserver-mailserver]
          |
    [switch]
   |      |
 PCs     [fileserver]

```

Basically, I'm looking for some inspiration here.  What does your network look like?  Do you have different machines serving different purposes?  And what kind of hardware (hubs, switches, etc.) do you have between them?

Also, if you have any good links/books on this subject to point me to, I'd be grateful.

---

### Post by koenn on 2008-03-16
```




			internet
			   |
			   |
			gateway / fw
			  |  | 
		-----------  ------------------------------------
		|						|
(LAN)		|						|
   -----------------------------------			     server (DMZ)
     |	|     |		|	     |				- dns 
   ...	PC   PC ...   server	   server			- proxy
			-dns	  (VMware host)				-squid  
			-dhcp						-aptproxy
			-filesrv
			-httpd
			-...
			-...	



```
Maybe a bit over the top for a small home network, but it was also an exercise to see how it could be done. Besides the physical layout, as above, there's a logical design behind it :
The main idea was that only the DMZ server would contact the internet. The LAN hosts use the proxies on the DMZ server.
For DNS : the LAN dns serves the LAN  hosts and knows the names/adresses on the LAN, it forwards other queries to the DMZ DNS, which quiries public DNS servers and caches. 

apart from saving some bandwith, this design makes firewalling easy : you only need rules for traffic between internet and DMZ ; traffic from LAN to DMZ and replies from DMZ to LAN are allowed, the rest can be blocked.
At least in theory : to be complete, the DMZ would also need a mail relay and a sollution for other internet services (torrents, ....)

If I"d plan to run publically accessible services (eg a public http or ftp server, it'd have to be in the DMZ so access from the internet always goes to DMZ, never to LAN. 

An alternative but similar design is to run the DMZ services on the gateway machine. Downside : you need to allow traffic from the untrusted internet TO the gateway (in stead of  THROUGH) so a compromised service on the gateway may compromise the entire gateway, including routing and firewall.

---

### Post by Uaine on 2008-03-16
koenn,
Thanks for the picture!  I've seen some similar designs in my researching. I like the suggestion to have the gateway/firewall machine operating independant from other purposes, and I've been doing some more reading about the DMZ concept.

What does your gateway/firewall look like?  More specifically, is it a dedicated machine rather than a well-configured router from linksys, netgear, etc.?

I did find a good tutorial for this design philosophy ([http://www.linuxjournal.com/article/4415](http://www.linuxjournal.com/article/4415)), but it's a bit dated and doesn't seem to get into the lower level of implementation details.  Still, it's well worth a quick read through.

One question I have for anyone who has experience with a similar setup to this: My fileserver is full of music, which I am eager to serve up through Ampache. This would necessitate a publicly available webserver, which would be located in the DMZ; but where would the fileserver ideally go?  Both the PCs in my home local network and the webserver would want access to the fileserver.

---

### Post by koenn on 2008-03-16
> **Uaine said:**
> 
What does your gateway/firewall look like?  More specifically, is it a dedicated machine rather than a well-configured router from linksys, netgear, .
It's not necessarily a good idea to disclose details about ones network design and security measures, but since it's not information one can easily hide from nmap, here goes :

It's an old Pentium  PC (133 mhz CPU, 64 or 128 mb ram, don't remember exactly)  in which I put 3 NICs and installed debian + iptables.

---

### Post by Uaine on 2008-03-16
> **koenn said:**
> It's not necessarily a good idea to disclose details about ones network design and security measures, but since it's not information one can easily hide from nmap, here goes :

Thanks.  I'm just trying to get a feel for how other people do this.  I'm very new to implementing a firewall that is any more complex than a purchased router.

I've got lots of old NICs laying around to use for this kind of thing, so I'll look into finding either a very lightweight, quiet chassis to put them in, or just buy a standalone firewall.

---

### Post by koenn on 2008-03-16
> **Uaine said:**
> 
One question I have for anyone who has experience with a similar setup to this: My fileserver is full of music, which I am eager to serve up through Ampache. This would necessitate a publicly available webserver, which would be located in the DMZ; but where would the fileserver ideally go?  Both the PCs in my home local network and the webserver would want access to the fileserver.

I don't have any experience in web servers, and I have no idea how connections between web servers and their back-ends (eg databases, or in your case, a file server) are usually implemented. 
I can think of a couple of ways to do what you're thinking of.
Ideally your file server would be in DMZ, which is fine if it only contains files your making public through your web server anyway. That means you need a separate file server in LAN in case you want to share other files as well. 

I've seen designs where you have two identical servers, one in LAN to serve the LAN, one in DMZ to serve the internet. The content would be synchronized (eg with rsync) but so that changes go from LAN to DMZ, never the other way around.

---

### Post by Uaine on 2008-03-16
> **koenn said:**
> 
I've seen designs where you have two identical servers, one in LAN to serve the LAN, one in DMZ to serve the internet. The content would be synchronized (eg with rsync) but so that changes go from LAN to DMZ, never the other way around.

I've considered that as an option.  Of course, I've been trying to find any possible alternative, as I don't look forward to buying enough hard drives to mirror my fileserver :P

One thing I'm considering, and looking into, is setting up firewall rules on the fileserver, and allowing both the DMZ and internal network to access it.  The DMZ would be very restricted in its access to the server, being allowed read-only permissions; the internal PCs could have less restricted access.

---

### Post by koenn on 2008-03-16
> **Uaine said:**
> 
One thing I'm considering, and looking into, is setting up firewall rules on the fileserver, and allowing both the DMZ and internal network to access it.  The DMZ would be very restricted in its access to the server, being allowed read-only permissions; the internal PCs could have less restricted access.
I was thinking along those lines as well. Downside is that you"d be allowing DMZ connections into your LAN, eg coming from the web server. If the webserver is compromised, you potentially have a problem - being aware of that, as you obviously are - and taking measures (like the read-only access if you can implement it) makes it less problematic, I think. 

I wonder how professional webserver admins do this. They should have the same problem : they probably have a database as a backend to a webserver - would that be on the same machine ? in DMZ ? in LAN ? in yet another network ? And what would their traffic rules be like ?

---

### Post by netlogic on 2008-03-16
very simple
=================
```

			internet
			   |
			   |
			gateway / fw
			  |  | 
		--------------------------------------------------------------------
		     |						        |
(LAN)		|						   |
   ------------------------------		    	 server (DMZ)
     |		     |	            |	     			       - http/ftp
   ..laptop	PC ...   server	   			    - vmware
			-dns	  				          - dapper  
			-dhcp					         - gutsy
			-filesrv				          - XP
			-vpn					          - 2008
								             - 2003
								              - OS/2
								              - FreeBSD
								              - Debian
								              - Arch

```

---

### Post by Spartan.II.117 on 2008-03-17
one option is to use something like sshfs and only open port 22 inbound, thatway you can login as an unprivliged user and limit access to certain files depending on group membership.

---

### Post by mozetti on 2008-03-17
Here's mine:

```
                                   Intar-tubes
                                     |        |
                                     |        | - -see, it's a tube like Sen. Stevens said!
                                     --------
                                         |
               --------- WRT54G w/DD-WRT (WDS Host)
               |              %           |
               |              %           |
               |              %           |
              PC              %        MyBook World 1TB NAS<---USB-->MyBook 500GB
                              %
                   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
                        %              %                        %
                        %              %                        %
                  Laptop               %                  WRT54G w/DD-WRT (WDS Client)
                                       %                                        |
                      SMC EZ Stream Multimedia Receiver                         |
                                                                                |
                                                                            Xbox360

```

>  | - CAT5
% - WiFi
Basically, I set up the WDS with 2 WRT54G routers so I didn't have to snake a CAT5 cable from the Xbox360 to the original router. My PC does the normal PC things, plus I'll be serving multimedia from it to the Xbox360 and the SMC EZStream. I just hooked up the MyBook World NAS over the weekend, enabled SSH access and will be setting up an rsync server for backup, vsftpd to serve up files to my friends/give me access, and probably install CUPS so it can act as a printserver for my USB printer.

I'm buying a house this summer, and the eventual plan to to have a robust home network and media delivery system with a fileserver. I'm just building it out slowly right now.

---

### Post by Tomatz on 2008-03-17
Setting up more than a private wlan network just goes woosh over the top of my head.  But if you pm me your email i have some great ebooks on the subject.

---

### Post by Tomatz on 2008-03-17
[PHP]                                            [Cable modem]
                                                  |
                                                  |
                                      [802.11g router/firewall]
                                                  |
                ---------------------------------------------------------------------
               |                                                                     |
             [lan]                                                              [wilan]
               |                                                                     |
      [ubuntu 7.10/xp]                                                          [eeepc]
[/PHP]

Bit basic but you get the idea :lolflag:

---

### Post by TheAddict on 2008-03-26
I feel kind of simple now.

```

                   Wireless modem/router
                          ||
                          ||
                          ||
                          ||
                          ||
                          ||
   ----------------------------------------------
   |		      /		         |		     |
   |		      \		         |		     |
   |		      /		         |		     |
Desktop	      Laptop	   File Server       XBMC


```

I am planning on chucking away the XBMC (figuratively), adding a tv tuner or two to the server, installing a Myth backend on it, and building a couple of myth frontends. Controlling it all through a PDA with VNC into the frontends for control with the telly off (if possible)

---

### Post by daanemanz on 2008-04-07
I don't know whether this is possible, but hey, just want to give it a try! Could anyone give me some advice about this setup? Note: it's not like this yet, but I'd like to try...

```

                                ISP
                                 |
                                 |
                              eth0
                      Server (web/proxy/dns/dhcp)
                              eth1
                                 |
                                 |
                          FON wifi router
                                %
                                %
               %%%%%%%%%%%%%%%%%%%%%%%%%%%%%
              %                              %
              %                              %
        Laptop                                    PC

Note: | = Cat5, % = WiFi

```

As you can see, I'd like to use my Server as some kind of access point. Do I need to bridge the two NICs in my server (eth0 and eth1)? 

Every help or advice offered will be much appreciated!

---

### Post by jcostom on 2008-04-07
Put simply, without giving up too much, mine is divided into security zones.  There are 3 behind the fw:
[LIST]
[*]Trusted - my work system, desktop PC and server connect here.
[*]Family - our macs and our wii connect here.
[*]Visitors - our guests can connect here.
[/LIST]

The firewall has built-in wifi and allows multiple SSIDs, which can be bound to different zones.  There are varying degrees of authentication and encryption in place, escalating from the lowest on the Visitor zone to the highest on the Trusted zone.

Visitor and Family can talk to the Internet, but not to Trusted, other than DNS queries.  Family can also talk to a couple of other ports on a couple of other devices in Trusted too.  There's web filtering done on all web traffic, regardless of Zone.

No inbound access from the outside, unless you're connecting with an IPsec client.  AES again, Certificates, Xauth too.

Just realize, when you build a network like this, you've got a lot to think about in terms of what traffic flows need to look like, and configure firewall rules appropriately.

---

### Post by Dr Small on 2008-04-07
Here is our home network setup:
```

              _
-------------| |
    MODEM    | |-----------
             |_|          |
                          | 
                          ||------------------------
                      ____||____                   |
             ((((((((|__________|))))))))          |
		    WIRELESS ROUTER                |
                      192.168.0.1                  |     _
                                                   |----| |
 _|                                                     | | DEN
| |               _|                                    |_| 192.168.0.100
| | MYCROFT      | |               _|
|_| 192.168.0.70 | | DARKGHOST    | |               _|
                 |_| 192.168.0.16 | | FIREFOXWIZ   | |
                                  |_| 192.168.0.14 | | LAPTOP
                                                   |_| 192.168.0.101
```

---

### Post by Mithrilhall on 2008-04-07
Internet <--->Cisco Router<--->Packet Shaper<--->Cisco Switch<--->Computers

---

### Post by Cancerkazoo on 2008-04-07
[img]http://home.comcast.net/~cancerkazoo/images/pc/network.jpg[/img]

---

### Post by garfonzo on 2008-04-07
At what point did this thread become less about our home networks and more about making sweet ASCII art!?

---

### Post by netlogic on 2008-04-07
> **garfonzo said:**
> At what point did this thread become less about our home networks and more about making sweet ASCII art!?

Very good point. LOL. I suck at ASCII art.

---

