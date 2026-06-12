---
title: "Jackalope Server - Am I trying the impossible?"
date: 2009-08-11
forum: Server Platforms
---

### Post by fidgaf on 2009-08-11
I have a spare PC and wanted to make it into a server serving everything I could make it do - Mainly as a web server for Apache, PHP and MySQL plus mail (static IP to come later).

What I have:
[LIST]
[*]ubuntu-9.04-server-i386.iso burned to CD and checked as OK
[*]Orange Livebox-1808 wireless router
[*]Windows XP Pro SP3 connected by wire to Livebox (Main PC)
[*]Second PC ready for Ubuntu Server connected both by ethernet to main PC and wireless connection available (USB dongle).
[*][http://www.unix-tutorials.com/go.php?id=4053](http://www.unix-tutorials.com/go.php?id=4053) - The Perfect Server - Not helping
[/LIST]

I have installed 9.04 server once on a dedicated harddrive (wiping an existing Ubuntu that worked and connected just fine as does the duel boot XP also on another dedicated harddrive). I have asked it to install everything it can; DNS server, LAMP server, Mail server, OpenSSH server, PostgreSQL database, Print server, Samba file server, Tomcat Java server, Virtual machine host and Manual package selection.

When installing I cannot get it to connect to Livebox either by wire or wireless.

I have the WEP (tried with and without spaces), Livebox is set to "pairing" mode (lasts 10 minutes)and I also have access to all the system info live from Livebox

> System Information

Information page.

The information on these pages is not transmitted on the Internet, it originates from your Livebox's internal web server.
These pages have been optimized and tested with these browsers : Internet Explorer 7 and Firefox 2.
INVENTEL version : v5.10
Livebox-1808 (XXXXXXXXX)
ADSL  Wireless  Security  Port Forwarding - NAT  Network  Interfaces  Livebox  Dynamic DNS  USB Host Port 	 Firmware status  

ADSL    Top   Refresh
ADSL firmware version :	A2pBT009c1.d17d
Connection mode :	ADSL2+
Type :	Fast
Noise margin (dB) :	27.3
Attenuation (dB) :	6.5
Attainable download rate (kbps) :	18099
ADSL status :	Connected [0]
 
 	Downstream	Upstream
Rate (kbps)	8061	605
 
WAN IP address :	XXXXXXXXX
Gateway :	XXXXXXXXX
Primary DNS server :	XXXXXXXXX
Secondary DNS server :	XXXXXXXXX
 
Internet protocol :	pppoa
Encapsulation :	VC-Mux
VP :	0
VC :	38
Broadband Username :	XXXXXXXXX
Mode :	Permanent [1--1]

Wireless    Top  Refresh 

Enable Wireless LAN :	Enabled
Device address :	 XXXXXXXXX
Card type :	 bcm
Channel number :	 1
Maximum pairing time (minutes) :	 10
Livebox Name : :	 Livebox-1808
WEP Security Key :	 XXXXXXXXXXXXXXXXXXXXXXXXXXX
Easy pairing state :	 Enabled

Devices connected to your network
Device address
XXXXXXXXX
XXXXXXXXX
XXXXXXXXX
XXXXXXXXX

Security   Top Refresh
Firewall :	Medium (default)
Maximum pairing time (minutes) :	 10
Your computer's IP address :	XXXXXXXXX
DMZ :	
UPnP :	Enabled

UPnP router table
Protocol	External port	Internal port	Server IP address

Port Forwarding - NAT    Top  Refresh
Service	Protocol	External port	Internal port	Server IP address

Network    Top  Refresh
Enable DHCP server :	Enabled
LAN IP address:	XXXXXXXXX
Broadcast LAN IP address:	XXXXXXXXX
Subnet mask:	255.255.255.0
DHCP start address:	XXXXXXXXX
DHCP server end address:	XXXXXXXXX

Interfaces    Top  Refresh
Yellow Ethernet interface:	Cable disconnected
Red Ethernet interface:	Connected
USB interface:	Cable disconnected

Interface	RX (KB)	TX (KB)
eth0	0	9950
eth1	2699845	2774177
usb0	0	0
br0	2556600	2950604
br1	0	0
wl0	10133	240755
nas3	0	0
ppp0	2735897	88232

Livebox    Top  Refresh
Digital TV	Automatic
Orange Broadband Talk Status:	Registered
Talk service Phone Number:	XXXXXXXXX

Dynamic DNS    Top  Refresh
Server status:	Off

USB Host Port    Top  Refresh 

USB Peripherals

No device connected to the USB host port.

Firmware status    Top  Refresh
Firmware identification:	v5.10.7-uk
Firmware status	Full

I have installed the server again but cancelled the connection option. I now have an installed jaunty server and a prompt, I'm sudo su and ready to go.

What can I do to get this beast running?

Should I give up (knowledge is limited and a steep learning curve ahead but I can use vi and can muddle around a command line?

Would installing Apache, php, MySQL etc on a vanilla Ubuntu Jaunty be more sensible -  even though I really want a dedicated Ubuntu server?

Thanks.


PS - Orange "support" claim that the Livebox does not use DHCP (despite it being listed in the specs). When asked what protocol Livebox need for devices to acquire configuration information they insisted it was IPv4. Personally I think this is BS.  
I thought IPv4 is just the protocol for IP addresses (which it uses) but not in any way instrumental in transferring configuration information - but I could be wrong.

PPS - If I can get connected would trying The Perfect Server (above) again be a good idea or do you know a better tutorial?

---

### Post by fidgaf on 2009-08-11
Just finished another attempt. No joy. :confused:

---

### Post by hessiess on 2009-08-11
Don't run servers on a wireless network, they are nowhere near reliable enough. I have a network with a livebox, but everything is wired, works perfectly. And do NOT use WEP to secure a wireless network, it is trivial to crack. WPA is much better.

I recommend that you get a switch and connect up your network with regular cat5 cables.

You should also disable UPNP, it has the potential to be a massive security risk if the Windows machine ever gets infected by a worm or virus.

---

### Post by fidgaf on 2009-08-12
Thanks for the tips.

There is to be nothing of any value on the server or other computers connected. My main security protection would probably be boring an attacker to death. :)

Seriously, I'll take your suggestions on board and look at upgrading security. I do understand that it's not just the data stored that is attractive to an attacker. Once up and running I think it will be sensible to make all a secure as I can as I never know where it will all go in the future.

Wiring the Ubuntu PC to the Livebox is not a problem (other than some serious furniture moving) but this would leave me with my main (fastest) PC switched to wireless. Would that slow its connection down?

Although not as reliable I would still like to try to connect wirelessly first, if I can.

---

### Post by fidgaf on 2009-09-08
I take it that from no response wireless is bad and ethernet to my XP PC is impossible.

It's just sat there unused.

Where can I go to get information on how to get the thing doing something, anything, with my existing setup for a newbie that isn't a hardened network admin but would like to learn to be?

---

### Post by hessiess on 2009-09-08
> 
but this would leave me with my main (fastest) PC switched to wireless. Would that slow its connection down?


Maby, depending on if you are using a B,G or N network, however you are unlickly to notice any slowdowns.

> 
Where can I go to get information on how to get the thing doing something, anything, with my existing setup for a newbie that isn't a hardened network admin but would like to learn to be?


Just play with it, try stuff out and do research. For sccurity related topics I recomend listing to the Security Now podcast, its absolutely packed with information [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)

If you have the time, listen to the whole 212 episodes, skip the windows spasific ones tho.

---

### Post by cariboo on 2009-09-08
> **fidgaf said:**
> Thanks for the tips.

**There is to be nothing of any value on the server or other computers connected. My main security protection would probably be boring an attacker to death. :)**

Seriously, I'll take your suggestions on board and look at upgrading security. I do understand that it's not just the data stored that is attractive to an attacker. Once up and running I think it will be sensible to make all a secure as I can as I never know where it will all go in the future.

Wiring the Ubuntu PC to the Livebox is not a problem (other than some serious furniture moving) but this would leave me with my main (fastest) PC switched to wireless. Would that slow its connection down?

Although not as reliable I would still like to try to connect wirelessly first, if I can.

Crackers don't care what you have on your system, they are more than likely going to setup a bot of some sort.

If you want help, with getting wireless working, how about pasting the output of:

```
sudo lshw -C network > network.txt
```  

in your next post. The above command creates a text file of the details of your networking devices, you should be able to transfer the file to a system with a working internet connection via sneaker net :), use a usb thumb drive or a floppy, whatever works best for you.

---

