---
title: "Howto: Set up Ubuntu as a firewall/gateway router with webmin"
date: 2008-09-21
forum: Tutorials
---

### Post by sammydee on 2008-09-21
[COLOR="Red"][SIZE="5"]**_Intro_**[/SIZE][/COLOR]

Hi all.

This guide will cover how to set up a standard Ubuntu pc as a drop in replacement for a normal consumer router, but far more powerful and with considerably more functionality. It will also touch on some QOS filtering to help improve latency and network speed. If you get into any difficulties, rescue and recovery commands that can help are listed at the end. Also listed are instructions on how to completely revert all changes made in this tutorial.


I'm writing this howto because I wanted to set my Ubuntu server up as a router, and due to the lack of other up-to-date and easy to follow howtos on the subject I had to figure it all out myself. I wanted to document what I'd learned so I could save other people a whole lot of time and effort.

I'm assuming that if you are reading this you do have a basic working knowledge of what an internet gateway/router actually DOES, what NAT is and the basics of ip networking. If not, I suggest you read and digest the following links, then come back ;-) :

[http://en.wikipedia.org/wiki/Internet_Protocol](http://en.wikipedia.org/wiki/Internet_Protocol)
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)
[http://en.wikipedia.org/wiki/Gateway_(telecommunications)](http://en.wikipedia.org/wiki/Gateway_(telecommunications))

You will need a terminal up on the machine you are setting this up on. I do not recommend doing this over ssh unless you also have physical access to the pc, it is far too easy to get a firewall rule wrong and lock yourself out of the system.

[COLOR="Red"]**_[SIZE="5"]Basic setup (the bare minimum required to get a functioning and secure NAT router)[/SIZE]_**[/COLOR]


[COLOR="Blue"][SIZE="4"]**_Requirements_**[/SIZE][/COLOR]


**_Hardware_**

Ok, to do this you need a spare pc with Ubuntu on it and two network cards. It doesn't need very impressive specs at all. I run my gateway on a P3 600mhz with 512mb of ram but I think you could easily do it on anything better than a 200mhz P2 and 128mb of ram. Any edition of Ubuntu will work, desktop or server edition. The only real difference is that server edition has no gui. This isn't a problem, we will only be using the command line anyway.

**_Software_**

This guide uses webmin as a web interface to configure the necessary iptables rules and servers. I like using webmin instead of scripts because webmin is nicer to look at and easier to comprehend than a script with the same functionality, which results in less confusion, less bugs and a better understanding of what you are actually doing. Open a terminal and run the commands below to install all necessary software:

```
sudo aptitude install bind9 dhcp3-server perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

You can find the latest version of webmin here as a debian package:

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

The latest version at the time of writing this guide is 1.430, to install this version execute the following command:

```
cd ~ && wget http://prdownloads.sourceforge.net/webadmin/webmin_1.430_all.deb && sudo dpkg -i webmin_1.430_all.deb
```

**IMPORTANT NOTE: It is an EXTREMELY bad idea to leave webmin open to the outside world. Only your user password stands between a remote hacker and complete control of your pc. This is very insecure, DO NOT DO IT. If you really need to access webmin remotely, I assume you know what you are doing, and know how to use ssh tunnelling :-).**

You can now access webmin from the local pc by going to [https://localhost:10000](https://localhost:10000). If you are using firefox you will need to add a security exception. This isn't at all insecure, it is just because you are using a self signed certicate. Once you have logged in you should see a splash screen like this:

**_[COLOR="Red"][SCREENSHOT: Webmin splash screen](http://img412.imageshack.us/my.php?image=webminsplashjp3.png)[/COLOR]_**

All configuration pages are accessed through the main menu on the left.

For security reasons, the first thing you should do after you have logged in with your username and password is to disable all remote access to webmin. Click "Webmin" in the control panel on the left and go to "Webmin Configuration". Now click ip access control. Change the radio button to say "Only allow from listed addresses" and add the value "127.0.0.1" (without inverted commas) to the text box. Click save.

**_[COLOR="Red"][SCREENSHOT: Ip access restriction screen](http://img184.imageshack.us/my.php?image=iprestrictaccessin9.png)[/COLOR]_**

Webmin is now set up and ready to use!


[COLOR="Blue"][SIZE="4"]**_Configuring the network cards_**[/SIZE][/COLOR]


Seeing as you want to use this computer as a router, you should already have two network cards. You need to find out what their names are and decide which one should be internet facing and which one should be connected to the local network. To find out what network cards you have in your system, run the command:

```
ifconfig -a
```

You might see quite a few interfaces here depending on your system, the only ones you need to worry about are the ethernet interfaces (the ones called something like ethXX). They will usually be labelled eth0 and eth1 but might be any numbers, so I will from now on refer to them as eth_BAD and eth_SAFE. eth_BAD is the internet facing adapter, eth_SAFE is the local network adapter. It is a good idea to write down which one is which because you will be referring to it often.

We will set up routing first using the very powerful and flexible linux firewall, iptables.

It is important to note that if you make a mistake here you could completely disable all networking, which would cut off your access to the internet and also stop you from accessing webmin to fix the problem. If you run into difficulties, there are some commands at the end of this guide which you can use to fix the problem.

Ok, now we need to enable packet forwarding, otherwise NAT will not work. You can do this by editing the following file:

```
sudo cp /etc/sysctl.conf /etc/sysctl.conf.bak && sudo nano /etc/sysctl.conf
```

Hit ctrl+w to search, type net.ipv4.ip_forward then press enter. Make sure the line says net.ipv4.ip_forward = 1 and is uncommented. It should now look like this:

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

Press ctrl+o to save and ctrl+x to exit. **Now reboot to turn on packet forwarding.**

At this stage, your new server/gateway should be getting it's internet access through eth_BAD. If your internet doesn't work through eth_BAD, go make it work, then come back again when you have :-).

Now go back to the webmin page and click "Networking" then "Network Configuration" on the left. Go to "Network Interfaces".  We now need to set a static ip address for our local network on eth_SAFE.

I will use 192.168.0.0/24 for the purposes of this guide. This is the standard ip range to use for local home networks. Go to the "Interfaces Activated at Boot Time" tab and click eth_SAFE to configure it if it is there already. If it isn't there already (it probably isn't) then click "Add a new interface". Enter the following details:
[I]
"Name" - Enter the device name, probably eth0, eth1 or similar.
"IP Address" - Make sure the "Static" radio button is checked, and enter 192.168.0.1 into the text box.
"Netmask" - Should be 255.255.255.0
"Broadcast" - 192.168.0.255
"Activate at boot?" - Set to yes[/I]

**_[COLOR="Red"][SCREENSHOT: Configuring eth_SAFE](http://img502.imageshack.us/my.php?image=configuringethsafemv2.png)[/COLOR]_**

Then click "Create". Check the radio button next to the new interface you created and click "Apply" to activate those settings. Great! The two network interfaces are now totally configured.


[COLOR="Blue"][SIZE="4"]**_Setting up the local network_**[/SIZE][/COLOR]


Giving eth_SAFE a static ip address is only part of what we need to do to set up a local network on that socket. We also need to provide a caching DNS server and a DHCP server to tell clients necessary information about the local network and how to resolve domain names.

**_Configuring DHCP_**

We will set up DHCP first. Go to the "Servers" tab on the left in webmin, and click "DHCP Server". In the subnets section at the top, click "Add a new subnet". Enter details as follows:
[I]
"Subnet description" - A name for your subnet, I used "Local network on eth_SAFE"
"Network address" - 192.168.0.0
"Netmask" - 255.255.255.0
"Address ranges" - this can be anything you like, 192.168.0.100 - 192.168.200 should cover it.[/I]

**_[COLOR="Red"][SCREENSHOT: Configuring DHCP subnet](http://img511.imageshack.us/my.php?image=dhcpsubnetal8.png)[/COLOR]_**

Leave all the other options alone and click "Create". Now a new icon should have appeared called 192.168.0.0. Click this icon, you will be returned to a screen similar to the one you just left except it has some new buttons at the bottom. Click the one that says "Edit Client Options".
[I]
"Subnet mask" - 255.255.255.0
"Default routers" - 192.168.0.1
"Broadcast address" - 192.168.0.255
"DNS servers" - 192.168.0.1[/I]

**_[SCREENSHOT: Configuring DHCP client options](http://img261.imageshack.us/my.php?image=dhcpclientconfigyw5.png)_**

Click "Save" and then "Save" again. One last thing to do on this page - scroll down and click "Edit Network Interface". Select eth_SAFE from the list and click "Save".

_**[COLOR="Red"][SCREENSHOT: Configuring DHCP interfaces](http://img524.imageshack.us/my.php?image=dhcpinterfacesja8.png)[/COLOR]**_

The DHCP server is now set up. Click the "Start Server" button at the bottom of the page, the server should start with no errors. If it gives errors, you've done something wrong :-).

Ok, all done! On to...

**_Configuring the DNS server_**

The DNS server works out of the box, it doesn't actually NEED any additional configuration.


[COLOR="Blue"][SIZE="4"]_**Configuring the firewall (or "Why I stopped worrying and learned to love IPtables")**_[/SIZE][/COLOR]


**_Setting up ip masquerading (routing)_**

Now we get to the "fun" part where we dive into iptables. From now on you can completely screw up your networking if you aren't careful, so make sure you know how to recover if it all goes horrible wrong.

On the left hand side, click "Linux Firewall". Check the radio button for "Do network address translation" and select eth_BAD as the interface to do it on. Check the box "Enable firewall at boot time" and click "Setup Firewall". Click "Apply Configuration".

**_[COLOR="Red"][SCREENSHOT: Setting up the firewall](http://img88.imageshack.us/my.php?image=setupfirewallna1.png)[/COLOR]_**

**_Setting up the firewall_**

At this point your server is configured as a working router/dns/dhcp server. It should work ok in this setup for everything you need it to do but it isn't properly secured. We need to define some rules that say who can make connections to our pc. We don't want just anybody from the big bad internet tapping into our home file shares for example. We do this by using iptables filtering.

The linux firewall works with three IP tables: MANGLE, PREROUTING and FILTER. The actual firewalling bit is done with FILTER, so in the "Linux Firewall" section of webmin, change the IPtable drop down box to the "Packet Filtering (filter)" IPtable.

**_[COLOR="Red"][SCREENSHOT: IPtables FILTER table](http://img91.imageshack.us/my.php?image=iptablespageig7.png)[/COLOR]_**

There are three "chains" listed here. Each chain defines what to do with a packet depending on where it is going. The three chains here are INPUT, FORWARD and OUTPUT. For each chain you can add rules that tell the firewall what to do for packets that meet certain defined criteria. You will probably want to blacklist all INPUT and FORWARD packets by default, then enable the ones you need. Change the default action on both INPUT and FORWARD to "Drop".

To add a rule, just click the "Add Rule" button and fill in the packet criteria and action to take as necessary.

Here is the bare minimum of rules that you NEED for your network to function properly:

[I]INPUT

Accept if protocol is ICMP (note: This allows your server to respond to pings. It isn't strictly necessary, but it doesn't really pose a security risk and makes network troubleshooting a LOT easier. If you're extremely paranoid, feel free not to bother with this option)
Accept if input interface is lo
Accept if input interface is eth_SAFE
Accept if input interface is eth_BAD and state of connection is ESTABLISHED,RELATED

FORWARD

Accept if input interface is eth_SAFE and output interface is eth_BAD
Accept if input interface is eth_BAD and output interface is eth_SAFE and state of connection is ESTABLISHED,RELATED[/I]

The above rules implement a very simple firewall that allows absolutely nothing in from the outside world unless it is part of an established connection. It also assumes the internal network is completely trusted and allows unfettered access to the server and outside world from the internal network. This is the default setting for pretty much every NAT device ever.

At this point you are effectively finished. You can just leave your server as a simple router with no other rules at the point. It is very secure and will work fine for most purposes. If, however, you want to run publicly accessible server, QOS filtering or if the internal network isn't completely trustworthy, you need to add some extra rules. Read on...

For reference, my INPUT and FORWARD tables look like this. I have added extra rules to mine to allow some servers to be accessable to the outside world:

**_[COLOR="Red"][SCREENSHOT: My INPUT rules](http://img441.imageshack.us/my.php?image=someinputrulesjl6.png)[/COLOR]_**

**_[COLOR="Red"][SCREENSHOT: My OUTPUT rules](http://img265.imageshack.us/my.php?image=someforwardrulesfm5.png)[/COLOR]_**

[COLOR="Red"]**_[SIZE="5"]Beyond the basics (more advanced tasks)[/SIZE]_**[/COLOR]


[COLOR="Blue"][SIZE="4"]**_More fun with IPtables_**[/SIZE][/COLOR]


If you are actually going to start using IPtables properly, you need to understand what it is, how it works and in what order the tables are applied. I suggest you read the wikipedia article and reference the diagram below to help give you a better understanding of the linux network stack:

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
[http://jengelh.medozas.de/images/nf-packet-flow.png](http://jengelh.medozas.de/images/nf-packet-flow.png)


It is important to note at this point that IPtables will apply your rules to each and every packet in order from top to bottom. Each rule is compared to your packet. As soon as an ACCEPT or DROP rule is found that matches your packet type, this action will be taken. If a packet gets to the end of a rule list without matching anything, the default action is taken. Here are two example scenarios:

Ruleset:
ACCEPT if input interface is eth1
DROP if port is 22

Any incoming packets on eth1 will be allowed through, EVEN IF the port is 22.

Ruleset:
DROP if port is 22
ACCEPT if input interface is eth1

Now incoming packets will be allowed on eth1 except if the port is 22.

**_Servers running on the router itself_**

If you want to run a server on your router (eg web server or ssh server) you need to open these ports to the outside world. This is easy to do by adding a rule to the INPUT filter explicitly allowing the incoming connection. Simply click "Add Rule" and accept packets with the packet type and destination port that are required by the server. Eg an ssh server might run on port 22 and accepts TCP packets so the rule would look like:

Accept if protocol is TCP and destination port is 22.

**_Giving a pc/server present in the lan a static ip address_**

This is necessary if you want to run a server on a pc inside the lan and need a port forwarded, for example a web server or bittorrent client.

This is quite a bit more complicated than for services running on the router itself, but still not too much of a challenge. First you have to set up the pc in the lan that runs the server (referred to from here on as the "host") with a static ip address. Because the ip addresses are allocated with DHCP, a host might be given a different ip address each time it connects to the network. You can easily give it a static ip address by telling the DHCP server to give it the same ip address each time.

Go into webmin and click the "Servers" section and select the DHCP server. In the hosts section click "Add a new host". Fill the details as shown:

[I]"Host description" - Whatever you want, this is just to help you remember which host it is
"Host name" - Set this to the hostname of the host. This can be found by executing hostname on the host pc. 
"Hardware Address" - This is the mac address of the host. This can be found be executing ifconfig on the host machine and looking at the mac address of the appropriate network card.
"Fixed IP address" - This is the ip address you want to give the host. This ip address should be in your local lan and should not be included in the group of ip addresses you already told the dhcp server to hand out dynamically. If you have been following this guide, it should be 192.168.0.X where X is a number from 2 to 99 inclusive.[/I]
"Host assigned to" - You can set this option to a subnet in order to use ip addresses within the dhcp dynamic allocation pool.

**_[COLOR="Red"][SCREENSHOT: DHCP static ip configuration](http://img523.imageshack.us/my.php?image=dhcpstaticipzk7.png)[/COLOR]_**

When you are finished, you can click "Save". To apply the settings, you need to delete the current DHCP lease by clicking the "List Active Leases" button at the bottom and clicking the current lease for the particular host. Then go back to the main dhcp server screen again and click "Start Server" to apply all settings. Next time the host reconnects to the network it will receive the new static ip address.

**_Port forwarding_**

Now the host in the lan has the same ip address all the time, the router can send packets to that same ip address each time and it will reach the right host.

This part can be a bit of a pain because you actually have to do TWO things. Firstly you have to set a rule in PREROUTING to tell IPtables where to route the incoming packets, but you also need to explicitly allow these packets in FORWARD otherwise they will be blocked by the filter. This is perfectly logical but sometimes can cause major headaches if you forget to set one or the other.

In webmin, click "Networking" and then "Linux Firewall". Change the IP table in the drop down box to "Network address translation (nat)". In the PREROUTING chain at the top, click add rule. Fill in the details as listed below:

[I]"Action to take" - Check the "Destination nat" radio button
"IPs and ports for DNAT" - Put the lan ip of the host and the port you want clients to connect to from the outside here
"Network protocol" - You have to specify udp or tcp (if you actually have need to use some other protocol this guide can't help very much :-) )
"Destination TCP or UDP port" - The port that the server is actually listening on on the host (note: this doesn't HAVE to be the same as the port external clients connect to)[/I]

**_[COLOR="Red"][SCREENSHOT: Example: Port 2222 from outside forwaded to port 22 inside lan](http://img217.imageshack.us/my.php?image=portforwardpreroutingqi8.png)[[IMG]http://img217.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/COLOR]_**

Then click "Save". Now change the IP table in the drop down box to "Packet filtering (filter)". In the FORWARD chain, add a rule like this:

[I]"Action to take" - Accept
"Network protocol" - set this to tcp or udp depending on what kind of service you are running. Some services (eg most bit torrent clients) need both tcp AND udp forwarded. In this case you may need to define two separate rules, one for tcp and one for udp.
"Destination TCP or UDP port" - set this to the incoming port used by the client when connecting from outside the lan.[/I]

**_[COLOR="Red"][SCREENSHOT: Example: Port 2222 forwarding explicitly allowed](http://img140.imageshack.us/my.php?image=portforwardforwardcv6.png)[[IMG]http://img140.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/COLOR]_**

Now you can just hit "Apply configuration" and you're done! That was easy wasn't it?


[COLOR="Red"]**_[SIZE="5"]What to do if it all goes pear shaped[/SIZE]_**[/COLOR]

If you do manage to lock yourself out of webmin, don't panic. Running the following command will flush all iptables rules, which should give you webmin access back again so you can fix the problem:

```
sudo iptables -F
```

**Warning: The above command will totally disable the firewall - your router and possibly the lan behind it will be wide open to the whole internet.**

To totally revert all changes made in this tutorial, run this command:

```
sudo aptitude purge webmin bind9 dhcp3-server && sudo cp /etc/sysctl.conf.bak /etc/sysctl.conf
```

After a reboot, everything should be totally back to normal again.


[COLOR="Red"]**_[SIZE="5"]The End[/SIZE]_**[/COLOR]


TODO:

QOS with wondershaper
Setting up a static external ip/dns settings

---

### Post by bluebear on 2008-09-28
Excellent howto, exactly what I have been looking for.  

Having some trouble with IP-forwarding. Changed the sysctl.conf file to enable IPv4. 
Then tried:  sudo echo 1 > /proc/sys/net/ipv4/ip_forward
Reply: -bash: /proc/sys/net/ipv4/ip_forward: Permission denied

Turned it on and off hoping the ip-forwarding would start, but no. Any hints. My second computer receives a dhcp IP, so its ok. 

The firewall works like a charm though, managed to totally block me out. Had to manually open the webmin port, forgot to turn it on as I´m currently outside my testbed setup. left it wide open but still no contact with outside/or router from second computer.

---

### Post by AKviking on 2008-09-28
Wow, this is amazingly what I needed this weekend.  As I have totally trashed my somewhat working network into a better one with Ubuntu as my firewall and web proxy.

(my wife thinks i was trying to fix what wasn't broke, however we know it's making better what was just adequate).  :D


However, I have the same problem as BlueBear regarding the "permission denied" while trying the "sudo echo 1 > /proc/sys/net/ipv4/ip_forward" command.

I can hit the internet off my Ubuntu machine, but my other PC(s) cannot.  I can successfully ping both network interfaces on the Ubuntu box, but cannot go anywhere outside.  Am not sure if I'm missing something with DNS or what.

I'm bookmarking this excellent tutorial for further configuration.

---

### Post by sammydee on 2008-09-28
> **AKviking said:**
> However, I have the same problem as BlueBear regarding the "permission denied" while trying the "sudo echo 1 > /proc/sys/net/ipv4/ip_forward" command.

This doesn't actually matter, as long as you change the appropriate line in the configuration file and then reboot.

Sam

---

### Post by bluebear on 2008-09-30
> This doesn't actually matter, as long as you change the appropriate line in the configuration file and then reboot.

That was what I tried in the first place after I had permission denied. Still no go and identical all other aspects as AKviking. 

My Ubuntu router can ping outside. 
My second computer hooked to the Ubuntu Router receives IP ok, but cannot ping router or outside. I must have missed something, and thought it must be IP forwarding as it corresponds to the problem.

EDIT:
No its not IP forwarding that is the problem. Its set as should.
You can try with: 
sysctl net.ipv4.ip_forward
It should reply following, if correct setup. 
net.ipv4.ip_forward = 1

---

### Post by sammydee on 2008-10-01
> **bluebear said:**
> That was what I tried in the first place after I had permission denied. Still no go and identical all other aspects as AKviking. 

My Ubuntu router can ping outside. 
My second computer hooked to the Ubuntu Router receives IP ok, but cannot ping router or outside. I must have missed something, and thought it must be IP forwarding as it corresponds to the problem.


Are you sure your firewall rules are set up properly and have been applied?

Sam

---

### Post by bluebear on 2008-10-01
Well, at the moment I flushed all rules and set default to always accept. If it doesn´t work like this, it wouldn´t work with rules setup. Hmm, still no clue why. Masquerade should handle the rest right?

EDIT:
Found IT! mixed up the IP settings for my eth_safe card. In stead of: 192.168.1.1, I had put 192.168.1.0 which don´t make much sense at all. Now I only have to setup my firewall and its all good to go. A big thanks for your howto sammydee.

---

### Post by ions on 2008-10-11
I have a dlink switch connected to eth1, PCs connected to that are getting IPs but can not surf the net.  I can ssh between boxes connected on the switch.  It's entirely possible I missed something but I've now gone through this howto 4 times from beginning to end attempting to solve this.

---

### Post by ions on 2008-10-11
The XP box connected to the same switch works perfectly.  It was not touched.  :(

---

### Post by ions on 2008-10-11
It's now working.  I deleted the IPs from Webmin and restarted the two Ubuntu machines and now they're working well.  No idea what that was about as I had restarted the machines nearly a dozen times already.  

Any chance somebody knows of a thorough howto on adding IPtable rules in Webmin?  I'm staring at a page full of fields and buttons and no idea what to do with them.

---

### Post by bluebear on 2008-10-15
Hi! My setup is up and running now, including portforwarding. 
Well I agree, its not that intuitive and there are some hurdles. 
I´m not sure where to start or if it´s necssary, since the howto is pretty straightforward. Shout otherwise I´m glad to help if I can.

---

### Post by sammydee on 2008-10-18
> **ions said:**
> It's now working.  I deleted the IPs from Webmin and restarted the two Ubuntu machines and now they're working well.  No idea what that was about as I had restarted the machines nearly a dozen times already.  

Any chance somebody knows of a thorough howto on adding IPtable rules in Webmin?  I'm staring at a page full of fields and buttons and no idea what to do with them.

The easiest way to configure iptables is to just learn how it works.

Read the wikipedia page on it and maybe the man pages, and make sure you understand what chains, tables and rules are. Also look at the big diagram linked in the howto. Once you actually understand iptables, configuring it is easy.

Sam

---

### Post by destructogus on 2008-10-23
Hi all,
first of all, thanks Sammydee for a great guide.
I followed it, right up until setting the rules for NAT (i am behind a modem/router which provides me with firewall.

So, i enabled the firewall, and left all the rules blank, with default to 'accept'.

Everything seems to be working peachy except one thing. I can't seem to access my ubuntu machine from the eth_BAD interface.

my network is set up like this

ADSL Modem/Router
   - PC 1
   - Ubuntu PC (Router)
              -PC 2 (via switch)

Where pc1 and Ubuntu pc are plugged directly into the adsl modem/router, and PC 2 is behind the Ubuntu Router.  I can access external websites and servers running on the ubuntuPC, so I know it's doing it's routing job fine, but when i try to access the servers running on the ubuntuPC from pc1, it just keeps timing out.

... oh.. and to make matters more interesting...
I was trying (previously) to access the ubuntPC directly (i.e. ssh 192.168.0.73)... no luck
but if i do it through the dyndns i've registered, w/ port forwarding on my modem/router.... it works.

argh!

Any ideas?

---

### Post by destructogus on 2008-10-23
also fyi
i've noticed i can't seem to connect to an external website from within the router (e.g using apt-get)

my error is: 
```
Err http://au.archive.ubuntu.com hardy/main lynx 2.8.6-2ubuntu2
  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.comubuntu/pool/main/l/lyn..... 
```

```
 $ping www.google.com
 ping: unknown host www.google.com
```  
... so yeah.. i just find this odd.

to summarize... I have NAT turned on (no rules, allow all) and this is what I network reponse
From behind my Ubuntu Router, everything seems to be working fine
From within my router, I cannot access the outside world 
From outside router, PC 1 (which is the same 'level' as the ubuntu router) cannot access the UbuntuRouter on Eth_BAD (192.168.0.73, as assigned by the modem/router's DHCP)

---

### Post by sammydee on 2008-10-24
Makes sure every rule in every chain is set to allow by default.

Can you ping 4.2.2.1? It might be a dns issue...

Sam

---

### Post by destructogus on 2008-10-26
I just checked my webmin thingo, NAT, Packet Filter and Packet Alteration were all defaulting to 'accept'... so I don't think that's the problem.

i did a ping 4.2.2.1 from webmin...
```
> ping -c 3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=52 time=197 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=52 time=197 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=52 time=197 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 197.279/197.617/197.910/0.259 ms
```

I'm not exactly sure what server I pinged, but that was the result.
Oh.. and just incase it helps here's my /etc/network/interfaces
```
> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
	post-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet static
	address 192.168.0.1
	netmask 255.255.255.0
	broadcast 192.168.0.255
	network 192.168.0.0

```

And results from ifconfig

```
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:10:1b:0c  
          inet addr:192.168.0.73  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe10:1b0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3328 errors:0 dropped:3251036199 overruns:0 frame:0
          TX packets:1301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:281793 (275.1 KB)  TX bytes:679978 (664.0 KB)
          Interrupt:221 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:12:ad:03  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4470 (4.3 KB)  TX bytes:4470 (4.3 KB)
```

I'm not sure if it's useful or not, but .... yeah.... it'd be cool to get this working.
Thanks Sammydee

---

### Post by sykostig on 2008-11-02
Great guide!
But I ran into some problems:

```
 * Starting DHCP server dhcpd3                                     [COLOR="Red"]  [fail] [/COLOR]
```

I think it have something to do with this:
```

No subnet declaration for eth2:avahi (0.0.0.0).
** Ignoring requests on eth2:avahi.  If this is not what
 you want, please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface eth2:avahi is attached. **
```

eth2:avahi is my card that I connect to my switch.

This is the second day I use Linux btw :)

Thanks again!

---

### Post by sammydee on 2008-11-03
> **destructogus said:**
> I just checked my webmin thingo, NAT, Packet Filter and Packet Alteration were all defaulting to 'accept'... so I don't think that's the problem.

i did a ping 4.2.2.1 from webmin...
```
> ping -c 3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=52 time=197 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=52 time=197 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=52 time=197 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 197.279/197.617/197.910/0.259 ms
```



Internet connectivity is working fine, you just have no dns server set up.

You need to go into webmin, then networking, network configuration and click hostname and dns client.

You need to tell it some dns servers, best to use the dns servers your isp gve you. If you don't use these, you can use opendns, or I like to use the level3 dns servers 4.2.2.1 and 4.2.2.2. These are anycast and are always very fast and accurate. This should fix your dns problem on the router.

As for your other problem, what network service are you trying to connect to? It may be bound to a specific ethernet device?

Sam

---

### Post by sammydee on 2008-11-03
> **sykostig said:**
> Great guide!
But I ran into some problems:

```
 * Starting DHCP server dhcpd3                                     [COLOR="Red"]  [fail] [/COLOR]
```

I think it have something to do with this:
```

No subnet declaration for eth2:avahi (0.0.0.0).
** Ignoring requests on eth2:avahi.  If this is not what
 you want, please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface eth2:avahi is attached. **
```

eth2:avahi is my card that I connect to my switch.

This is the second day I use Linux btw :)

Thanks again!

From the looks of things you have failed to specify which subnet the dhcp server should broadcast on. Follow through the dhcp section of my howto again making sure you fill in every box. Try looking at the screenshots and checking that your configuration matches.

Sam

---

### Post by termat on 2008-12-03
Hey there, thank you so much for the guide!

I have followed every step exactly, save for the part in the command prompt at the beginning, when you said to press "ctrl + O" in order to save it.  This was not the option for me, instead it was to overwrite it.   I just decided to exit, unable to find the save feature, could this be why I have not found success?  

I am trying to use this Ubuntu based pc to authenticate my school's network, then pass the internet onto my wireless router.  

I have tried to test the connection by plugging my second network adapter (usb linksys) directly into my laptop (vista).  I seemt o connect to the network w/o a problem, (it is called "linksys 3"), but it is local only.  I can't seem to see the ubuntu PC either.  No luck plugging to into the internet port on my router either.

Any suggestions would be awesome, I really appreciate it!


- Matt

---

### Post by sammydee on 2009-01-12
> **termat said:**
> Hey there, thank you so much for the guide!

I have followed every step exactly, save for the part in the command prompt at the beginning, when you said to press "ctrl + O" in order to save it.  This was not the option for me, instead it was to overwrite it.   I just decided to exit, unable to find the save feature, could this be why I have not found success?

Yes, you absolutely must overwrite this file or it will not work.

Sam

---

### Post by michaelgilch on 2009-01-15
Is there a way to still access Webmin without a gui? I am using Ubuntu 8.10 Server Edition.

---

### Post by pandamoniumcomputers on 2009-01-15
Wow! So far so good. Very well put together guide. I am currently using this setup at a big time international company and it is almost ready to go. I had been working on a Linux router for some time now. I have tried smoothwall, monowall and a few others but this actually worked thanks.

---

### Post by sammydee on 2009-01-17
> **michaelgilch said:**
> Is there a way to still access Webmin without a gui? I am using Ubuntu 8.10 Server Edition.

Well, webmin is a web server so you can connect to it from any computer with a web browser. You don't need a gui on the computer you set it up on.

Sam

---

### Post by leonix on 2009-02-03
After how many days of goggling howto's like this, i've finally found at last and made it working 90%, thanks sammydee to this useful howto's.

I had just this problem, the dhcp client workstation behind my ubuntu router can't resolve/ping using public hostname, only it can resolve the IP Address.

any idea on possible reconfiguration...thanks.

---

### Post by sammydee on 2009-02-22
> **leonix said:**
> After how many days of goggling howto's like this, i've finally found at last and made it working 90%, thanks sammydee to this useful howto's.

I had just this problem, the dhcp client workstation behind my ubuntu router can't resolve/ping using public hostname, only it can resolve the IP Address.

any idea on possible reconfiguration...thanks.

Sounds like a dns issue. Make sure your router is handing out a valid dns server address to clients.

Sam

---

### Post by mittwit on 2009-03-04
Great Howto.
I started with a clean install of 8.10 desktop and my eth_BAD is a USB wireless 3G which shows as ppp0.
I followed the directions to the end of setting up the basic firewall and now I can share my wireless internet with the other computers on my lan.
One thing I noticed when setting webadmin access to local only it wouldn't accept 127.0.0.1 as the local connection. Webadmin thought my ip was 127.0.1.1 so I just put 127.0.0.1 and 127.0.1.1. When I checked ifconfig gave 127.0.0.1 so not sure about that.
Anyway it works which is great. Thanks for the clear instructions.
Peter Cook.

---

### Post by leonix on 2009-03-04
yes, you're right...i'd messed up on putting correct dns address for my dhcp client subnet.
and now, its working 100%...thanks again
I still have another problem, although this is not a big deal one and I know this was resolved before, just no time to find solutions.
I can't ping my ubuntu routers' hostname from windows client, only IP address works.

---

### Post by sammydee on 2009-03-05
> **leonix said:**
> yes, you're right...i'd messed up on putting correct dns address for my dhcp client subnet.
and now, its working 100%...thanks again
I still have another problem, although this is not a big deal one and I know this was resolved before, just no time to find solutions.
I can't ping my ubuntu routers' hostname from windows client, only IP address works.

This is because windows is crap and doesn't support zeroconf. Blame microsoft for this and ask them to pretty please implement zeroconf for windows.

Sam

---

### Post by Navje on 2009-06-19
After some trouble, I finally made it work like a charm!

Two things I want to mention, could be useful for some people:

1. IP Tables are really effective. My router-pc is connected with the internet with a PPPOE connection and connected to a huge network in our student campus through eth2. Both are physically on the same network card. I have configured both separatley via IP Table rules, so i have added rules for eth2 and ppp0 separatley. I've also masqueraded both. Now my laptop (which is connected to eth0 on my router-pc) is a complete ghost on both the network as on internet :) Without masquerading and correct IP rules, I wouldn't have been able to connect to the internet and/or the student network. Just one of them would have worked. But now everything works fine!

2. I really recommend completely uninstalling UFW (Ubuntu Firewall) BEFORE doing anything with webmin! It caused me a pain in the *** when I didn't! I think it did a lot of interfering with the IP Table rules. I learned my lesson!

---

### Post by preston777 on 2009-06-22
Great howto

I'm almost there but I can't seem to access the internet from my lan. All my pc's get an ip and can talk to each other as well as the server/router. The server has internet access but for some reason I can't get it to forward internet traffic from my lan I've tried dns and ip's nothing gets out. By the way most of my lan consists of windows pc's if that makes a difference. Any help or ideas will be greatly appreciated.
     

Thx Preston

---

### Post by squalle0707 on 2009-09-14
good day sir sammydee....

thank you sir for this tutorial on how to set up ubuntu as a firewall/gateway router with webmin cause it fits my needs to set up a ubuntu as router for my home network connection....

but how to connect this ubuntu as router to windows clients,  i set to automatically obtain setting on my network connection and i use crossover cable to connect 2 pc's...

i greatly appreciated your help...

god bless...

---

### Post by slackjawed on 2009-10-03
Hi

Thank for the guide but i am in a world of difficulties!!! Got past the 127.0.1.1 thing. Sorted out the missing DHCP server module... but I am now stuck fast.

I can't get the DHCP server to run. I have followed the instructions to the letter but all I get is bad range address 192.168.0.100 is not in subnet 192.168.0.0 netmask 255.255.255.0.

Could you tell me what I'm doing wrong? Because I'm obviously doing something!

I want to get this working!!!

Cheers

Slackjawed knuckledragger

---

### Post by slackjawed on 2009-10-04
Hi

Got up this morning and finally got it sorted!

I edited out the range and just left    [blank] - 182.168.0.254 and it works now!

Now on to the fun bit :(

Cheers

Slackjaw

---

### Post by bigt89 on 2009-10-09
Hi, i followed your howto and it works perfectly.
But, iam trying to get xbox live to work but it fails on a MTU check. The MTU actually is high enough but there seems to be a problem with the router not handling ICMP xbox wants it to.

Anyone got a clue what i can do about it?

( I opened up a topic to but it seems more logical to post it here.

---

### Post by thexteam on 2009-12-21
Thanks for this tutorial - it works without any question.

One point to note for all users who are moving from Windows is to make sure that you don't experiment this within the network that has the ISA firewall. It doesn't work - I think - because the address translation gets blocked at the ISA level - just connect the eth_BAD to the broadband connection and that's it.

I also would suggest you switch off all the windows clients and any linux clients so that they all get fresh IPs. If you'd like the linux machines to be available on windows - just share a folder using samba and it works...

---

### Post by kevinthecomputerguy on 2010-02-06
sammydee, i added a little bit to your how-to :- )
[http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf](http://t3.woodel.com/my-linux-how-to/debian_howto_start_to_finish_using_webmin.pdf)
 
thanks for teaching me how to do the router setup, i use it all the time. Its flawless

---

### Post by JeffersonDavis33 on 2010-02-10
Thanks a million for this thread, as it has worked perfectly.  However, during a recent snow storm we lost power and after I got all machines back up and running, the router doesn't seem to be handing out IP addresses to the network.

The router can connect to the internet, but the network cannot connect to the router.  I deletes most of the components created by this tutorial then re-started the tutorial from the beginning and everything seems to go fine, but Im still not issuing  ip addresses to the network.  

In Webmin under Others, Server Status monitoring shows the BIND DNS and DHCP servers as down, and if I start them, I do not get errors, but the monitors still show them as down.

My next step is to replace my network facing network adapter, but other than that I'm stuck.

Any help would be greatly appreciated.

Thanks

---

### Post by userkiller on 2010-02-10
What's the benefit of this, a regular firewall just cause 20 dollars

---

### Post by userkiller on 2010-02-10
Sorry i double post how do i delte?

---

### Post by santiago79830 on 2010-02-21
Something else that should probably be saved before starting this procedure is the file /etc/network/interfaces. That is,

sudo cp /etc/network/interfaces /etc/network/interfaces.bak

This file sets up your network at boot time, and webmin modifies it. I foolishly agreed to changing the address of my external interface, which changed this file, telling it the external interface had a static address, when in fact the internet supplier gave me a dynamic address.

This totally shut down the network when I next rebooted. I stumbled on to the fact that the above file had been changed, and of course, couldn't talk to the outside world.

This is a pretty good tutorial, and the only one that's worked for me. It's a bit dated, though, and needs to be updated for ubuntu 9.10. I'd do it, but a networking specialist I am not.

---

### Post by adyraw on 2010-03-05
Great post.
It worked for me, had some problems changing sysctl.conf (permision denied), solved and it's ok.
Thanks.

---

### Post by kevinthecomputerguy on 2010-05-03
thanks again Sammy! I gave you some Props in my guide i am making, you were a ton of help.
[http://woodel.com](http://woodel.com)

---

### Post by Corsari on 2010-06-30
Hi sammydee,
I thank you for a different reason,

in few simple examples and words you gave me a better and sharper idea of the iptables logic.

Cheers
Robert

---

### Post by Abhi Kalyan on 2010-07-13
Fantastic HOWTO
Thank you

---

### Post by sinkincaffein on 2011-10-28
Thnaks for all de documentation! :D! Ill start from here. Very usefull! :)!

---

### Post by Rihoj on 2012-01-09
At the beginning you said that 2 network cards are needed. I am new to a lot of networking ideas. So my question is as follows: 1 my desktop has the lan port on the motherboard, and then has a NIC installed. Will this work as the two network cards or, do they both actually have to be cards? 2. My desktops and laptops are currently windows, will this throw up any issue with setting up a ubuntu firewall?

---

### Post by mongoose1927 on 2012-10-16
> **Rihoj said:**
> At the beginning you said that 2 network cards are needed. I am new to a lot of networking ideas. So my question is as follows: 1 my desktop has the lan port on the motherboard, and then has a NIC installed. Will this work as the two network cards or, do they both actually have to be cards? 2. My desktops and laptops are currently windows, will this throw up any issue with setting up a ubuntu firewall?
Rihoj, of course your built-in motherboard lan is counted as network cards. i used same setup in my router-server (i used 4 card thought). well, for the windows issue, your desktop need to be reinstalled with ubuntu server. i never know of a successful of a headless router-server using windows.

windows should be used to for ventilation. not for an OS. lol.

---

### Post by c-m on 2012-12-28
The DCHP part of the guide doesn't work any more.

In ubuntu 12.04 the DCHP webadmin module isn't correctly configured. 

Have some of the paths/names changed?

The DCHP module works if you set the following paths:
```

DHCP server config file	- /etc/dhcp/dhcpd.conf 
DHCP server executable	- /usr/sbin/dhcpd
Command to start DHCP server - /etc/init.d/isc-dhcp-server start
Command to apply configuration	-  /etc/init.d/isc-dhcp-server restart
Command to stop DHCP server	- /etc/init.d/isc-dhcp-server stop
Path to DHCP server PID file	- /var/run/dhcp-server/dhcpd.pid 
DHCP server lease file	- /var/lib/dhcp/dhcpd.leases

```

The problem i'm getting is that I follow all the steps to create the subnet and can even see in the logs that I created a subnet, yet the module says "No subnets or shared networks have been defined.
"

---

### Post by tellme on 2013-04-01
Thank you Sammydee, you saved me a lot of headache !!! great tutorial

---

### Post by Badhon_raj on 2013-05-23
Hello @sammydee, Thanks for your nice howto. But I'm stuck at Configuring DHCP client options.
eth0 and eth1 not listed! how do I select it?

[IMG]http://i.minus.com/ii6cewFvLjFoM.png[/IMG]

[IMG]http://i.minus.com/iNuRDs2o8WFLD.png[/IMG]

```
mint@mint ~ $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:2b:34:7c:5e:3f  
          inet6 addr: fe80::922b:34ff:fe7c:5e3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:639741 (639.7 KB)  TX bytes:258 (258.0 B)

eth1      Link encap:Ethernet  HWaddr 00:05:5d:42:ba:97  
          inet6 addr: fe80::205:5dff:fe42:ba97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35396 errors:0 dropped:265 overruns:0 frame:0
          TX packets:9699 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10886166 (10.8 MB)  TX bytes:1311228 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:544253 (544.2 KB)  TX bytes:544253 (544.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.44.51.68  P-t-P:20.20.230.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:8495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:7598052 (7.5 MB)  TX bytes:1085412 (1.0 MB)
```

---

### Post by rsriram22 on 2013-12-15
great tutorial - quick question. i am planning on setting this up inside a vm (virtualbox) on windoze box. i plan to disable the IPV4 and V6 stacks in the host. ..too, i d like to add a wireless card and have this whole setup simulate a wireless router...am looking at buying the following mobo that has 802.11ac inbuilt [FONT=arial]GIGABYTE GA-F2A88XN-WIFI[/FONT][FONT=arial] [/FONT]

1) So how do I make use of a loopback adapter so that the host box gets an IP on the LAN and also has access to the internet
2) have the wireless clients get LAN IPs as well?

thanks in advance!

---

### Post by mouse on 2014-01-02
> **sammydee said:**
> 

**_Configuring DHCP_**

We will set up DHCP first. Go to the "Servers" tab on the left in webmin, and click "DHCP Server". In the subnets section at the top, click "Add a new subnet". Enter details as follows:
[I]
"Subnet description" - A name for your subnet, I used "Local network on eth_SAFE"
"Network address" - 192.168.0.0
"Netmask" - 255.255.255.0
"Address ranges" - this can be anything you like, 192.168.0.100 - 192.168.200 should cover it.[/I]

Leave all the other options alone and click "Create". Now a new icon should have appeared called 192.168.0.0. Click this icon, you will be returned to a screen similar to the one you just left except it has some new buttons at the bottom. Click the one that says "Edit Client Options".
[I]
"Subnet mask" - 255.255.255.0
"Default routers" - 192.168.0.1
"Broadcast address" - 192.168.0.255
"DNS servers" - 192.168.0.1[/I]

Click "Save" and then "Save" again. One last thing to do on this page - scroll down and click "Edit Network Interface". Select eth_SAFE from the list and click "Save".

The DHCP server is now set up. Click the "Start Server" button at the bottom of the page, the server should start with no errors. If it gives errors, you've done something wrong :-).

Ok, all done! On to...

**_Configuring the DNS server_**

The DNS server works out of the box, it doesn't actually NEED any additional configuration.

Thanks. This worked out great. I knew it should be simple, but I always had trouble and had to start over so many times before I found your guide. But now, I'm up and running! I have one question that I hope someone can help me with. When I set the "DNS Servers" to 192.168.0.1 (The address of the router), I cannot not connect to the internet. If I leave the setting as default, I cannot connect to the internet. But, if I set the address to 8.8.8.8, everything seems to work great! What's up?

Thanks.

---

### Post by anton-ptv on 2014-01-21
Hi mouse,

Check if DNS server is installed.
To check log into webmin, and look under **Servers** list, there should be *BIND DNS Server*. If it is not there, you can install it through webmin, and reboot the server, after that all should be OK - DNS server will work out of the box :)
I had the  same issue i.e. I could not connect to internet until DNS server was  installed.

Let me know if this helped.

---

### Post by anton-ptv on 2014-01-22
Hi there,

First, **THANK YOU,** sammydee, **HUGE THANK YOU** for this how to!!! All is up and running :)

Also I wanted to add a couple of things to watch out for, while putting all pieces of the router together:

**1. **after intalling Webmin and changing its password with command ```
sudo /usr/share/webmin/changepass.pl /etc/webmin root NEW_PASSWORD
``` the command and the **new password!** will be stored in *.bash_history* file in your home directory. I did not really like the idea that my password is stored somewhere. So, just in case you are also paranoid like me :) edit the file with ```
nano /home/USER_NAME/.bash_history
``` and delete/change the entry, just to be safe :)

**2.** DHCP server. At the time of installation the current ubuntu server version was 12.04.3, and it has slightly different DHCP server [**isc-dhcp-server** ]("https://help.ubuntu.com/community/isc-dhcp-server")
To install it: ```
sudo apt-get install isc-dhcp-server 
```
The problem was, however, that Webmin (at the time of installation it was version 1.660) did not see this DHCP server, and a small operation required to return its sight. In Webmin go to **Servers - DHCP Server** and there click on **Module Config.** Then check the following parameters:
    a. DHCP server config file - */etc/dhcp/dhcpd.conf*
    b. DHCP server executable - */usr/sbin/dhcpd*
    c. Command to start DHCP server - *service isc-dhcp-server start*
    d. Command to apply configuration - *service isc-dhcp-server restart*
    e. Command to stop DHCP server - *service isc-dhcp-server stop*
    f. Path to DHCP server PID file - */var/run/dhcp-server//dhcpd.pid*
    g. DHCP server lease file - */var/lib/dhcp/dhcpd.leases*

Change, if they are different. Other options should be left as is, save changes, you might need to log out and log back into webmin, now it should see DCHP server.
 
**3.** When setting up IP tables, in Network Address Translation (NAT) table of IP tables under packets after routing (POSTROUTING) should be:

[B]Masquerade if output interfase is eth_BAD
Default action = accept[/B]

i.e. all ip packets that go into the internet from LAN will be masked, otherwise computers from local network will not have access to the internet. To be completely honest I have a hunch, that that option was there by default, and I "accidentally" ... it while playing with different settings.:p





One of the reasons I bothered setting up the router from a computer in the first place was that I needed control over the internet traffic. My problem was that I had 30 Gb of data (download + upload) from my ISP every month, and sometimes all internet would suddenly be gone before even the middle of the current month, because _someone_ downloaded/watched to many videos/skyped too much :evil:
 So, all I really wanted is a simple control over the *overall* traffic - if it exeeds 2 Gb of data per day, then bandwidth should be slowed to ~50 Kb/s till the end of that day (and restored with the start of a new day at midnight). And I also wanted the router to send me a warning e-mail when the limit was reached, and speed was slowed. Note, that I did not care who actually overused the internet, nor about any other fancy and elaborated way to torture individual users.
And in addition to this, traffic control should work without GUI, as I did not want to add any GUI to a headless server.

So a bit of research showed that:
**1. **[Wondershaper]("http://manpages.ubuntu.com/manpages/lucid/man8/wondershaper.8.html") will be good for the job to restrict the max up/down speed for an interface. 
**2.** The only problem was that wondershaper cannot keep any records of daily usage, and cannot dynamically change up/down speed depending on the total daily traffic all by itself as I wanted. And wondershaper will not send me any e-mails either. However, the wondershaper will do what it was created for - the main part - restrict speed, the rest will be done by a special script.
**3.** All more advanced ways of traffic control through IP tables and [advanced  network configuration]("http://http://www.tldp.org/HOWTO/NET3-4-HOWTO-5.html") were (well, actually, why *were?* they still *are!)* like a rocket science to me.:grin:
 

**Traffic control.**
Purpose: to restrict bandwidth speed of an internet interface if daily traffic through it reaches 2 Gb. There are several files apart from the main script.

**0. **First things first, you need to install wondershaper: ```
sudo apt-get install wondershaper
```
**1. trcontr.sh **file &#8211; main script file that does the job. Assigned as a cron job in webmin, executed every minute as *root,* because wondershaper requires root access to set up/down speed.
**2. dailytr.log** file &#8211; logges how many bytes were used
**3. sl_int_msg.txt** &#8211; text of e-mail message that will be sent in case limit was reached
**4. rsl.sh** &#8211; extra script that resets daily usage and removes any speed restrictions. Executed manually when needed :)
**5. rsl_boot.sh** &#8211; extra script, executed as a cron job on start-up only, if/when server re/boots to zero all statistics.

Main script uses **eth1** as internet interface, e.g. **eth1 = eth_BAD,** and assumes that the script and all files are located in */home/USER_NAME/Scripts*

If you need any assisstance on how to make a script executable, or assign a cron job in webmin, or set up ssmtp to send e-mails, check out [this how-to,]("http://www.havetheknowhow.com") in particular [how to assign cron jobs]("http://www.havetheknowhow.com/Configure-the-server/Monitor-server-temperatures.html") and [how to set-up ssmtp]("http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html").



**trcontr.sh**
```
#!/bin/bash 

#read RX and TX statistics for eth1 (internet) interface, and sum it up: 
R1=`cat /sys/class/net/eth1/statistics/rx_bytes` 
T1=`cat /sys/class/net/eth1/statistics/tx_bytes` 
TXRX=`expr $T1 + $R1` 

#read today's date and leave month and day only: 
t_date=$(date) 
sh_t_date=${t_date:4:6} 

#read start date, start RX/TX and current RX/TX from log file: 
start_date=$(sed -n '2p' /home/USER_NAME/Scripts/dailytr.log) 
start_RX_TX=$(sed -n '4p' /home/USER_NAME/Scripts/dailytr.log) 
current_RX_TX=$(sed -n '6p' /home/USER_NAME/Scripts/dailytr.log) 

#calculate how much was used today and set up daily limit: 
used_today=`expr $current_RX_TX - $start_RX_TX` 
daily_limit=2000000000 


echo "================================" 
echo "Start Date= "$start_date 
echo "Start RX/TX= "$start_RX_TX 
echo "Current RX/TX= "$current_RX_TX 
echo "Used today= "$used_today 

#check if this is a new day: 
  if [ "$sh_t_date" != "$start_date" ] 
  then 
    echo "Start date is different from current date, shall start a new day" 
    #update Start date in the log: 
    sed -i "2 c${sh_t_date}" /home/USER_NAME/Scripts/dailytr.log 
    #start RX/TX and current RX/TX = current RX/TX: 
    sed -i "4 c${current_RX_TX}" /home/USER_NAME/Scripts/dailytr.log 
    sed -i "6 c${current_RX_TX}" /home/USER_NAME/Scripts/dailytr.log 

    #remove any speed restrictions from internet 
    /sbin/wondershaper clear eth1 

    # remove "email sent" flag 
    sed -i "6 c0" /home/tony-s/Scripts/sl_int_msg.txt 

  else 
#The same day. Update current RX/TX in the log: 
    echo "This is still the same day, continue logging" 
    sed -i "6 c${TXRX}" /home/tony-s/Scripts/dailytr.log 

#Check if used amount reached daily limit: 
    if [ $used_today -ge $daily_limit ] 
    then 
     echo "Daily limit reached!" 
       #check if e-mail was already sent and speed restricitons applied: 
       if [ $(sed -n '6p' /home/USER_NAME/Scripts/sl_int_msg.txt) -ne 1 ] 
       then 
         echo "This is first time limit was reached today, will send e-mail and slow down the internet" 

         #update "email was sent" flag, send it and slow down the internet 
         sed -i "6 c1" /home/USER_NAME/Scripts/sl_int_msg.txt 

         /usr/sbin/ssmtp YOUR_MAIL@gmail.com </home/USER_NAME/Scripts/sl_int_msg.txt 

       #wait for 20 seconds, while e-mail is being sent, otherwise speed restrictions will be applied and it will take too much time to send the message
         sleep 20 

         /sbin/wondershaper eth1 50 50 
       else 
         echo "This is not the first time limit was reached today, e-mail was already sent, and restrictions applied, will do nothing" 
       fi 
    else 
     echo "Daily limit was not reached, enjoy fast internet (while you can :)" 
    fi 

  fi 

exit
```


**rsl.sh**
```
#!/bin/bash 


echo "====================" 
echo "Ineternet daily limit will be reset, any speed restrictions removed" 

#reset statistics: "start RX/TX" and "current RX/TX" = "current RX/TX": 
current_RX_TX=$(sed -n '6p' /home/USER_NAME/Scripts/dailytr.log) 
sed -i "4 c${current_RX_TX}" /home/USER_NAME/Scripts/dailytr.log 

#remove any restrictions from internet 
/sbin/wondershaper clear eth1 

# remove "email sent" flag 
sed -i "6 c0" /home/USER_NAME/Scripts/sl_int_msg.txt 

exit 
```


**dailytr.log**
```
#Start date: 
Dec 29 
#Start RX_TX: 
587706007 
#Current RX_TX: 
616832747
```


**sl_int_msg.txt**
```
From: [EMAIL="YOUR_MAIL@gmail.com"]YOUR_MAIL@gmail.com[/EMAIL] 
Subject: Daily limit reached 

Daily internet limit was reached, connection speed was slowed down. 

0 
```
**zero** at the end of *sl_int_msg.txt* is **very important,** and must be in line #6!


**rsl_boot.sh**
```
#!/bin/bash 

# this script will be run at start-up, in case server reboots to zero all statistics in log files 
echo "====================" 
echo "Ineternet daily limit will be reset, any speed restrictions removed" 

#reset statistics: "start RX/TX" and "current RX/TX" = "current RX/TX": 
sed -i "4 c0" /home/USER_NAME/Scripts/dailytr.log 
sed -i "6 c0" /home/USER_NAME/Scripts/dailytr.log 

#remove any restrictions from internet 
/sbin/wondershaper clear eth1 

# remove "email sent" flag 
sed -i "6 c0" /home/USER_NAME/Scripts/sl_int_msg.txt 

exit
```

That's it! :cool:

---

