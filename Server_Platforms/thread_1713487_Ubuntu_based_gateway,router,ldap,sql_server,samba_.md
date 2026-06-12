---
title: "Ubuntu based gateway,router,ldap,sql server,samba distros"
date: 2011-03-24
forum: Server Platforms
---

### Post by lindevox on 2011-03-24
Hi, does anybody knows any server distro based on ubuntu that has gateway/router,ldap,sql-server,samba,etc function integrated in it and support TP-LINK WN821N (Atheros AR9170usb wifi)?

What I mean is like ClearOS. Kinda like it because I don't have to separately install each package mention above manually.

The only problem I had with ClearOS is that during the installation process, I wasn't able to set it up as gateway mode because it didn't recognize or support usb wifi as network interface for my Internet connection.

Here is my network diagram:

internet (ISP) <-> ADSL <-lan cable> WR #1 <-> USB WIFI <-> SERVER <-lan cable/eth0-> WR #2 <-> WR#3 <->Client PC's

ADSL = Linksys AM300, Static IP: 192.168.1.1/24) the ADSL Modem gets its internet IP address from ISP DHCP.
WR#1 = Linksys WRT350N (IP: 192.168.1.2/24, DHCP).
USB WIFI = TP-LINK WN821N (Chipset: Atheros AR9170) NOT WORKING/RECOGNIZED BY COS !
SERVER = USB WIFI IP: Assign by WR#1 (DHCP), eth0 : 192.168.2.1/24, running DHCP on eth0.
WR#2 = TP-LINK WR1043ND (Static IP: 192.168.2.5/24, Gateway IP: 192.168.2.1) running on WDS mode to link to WR#3.
WR#3 = TP-LINK WR1043ND (Static IP: 192.168.2.6/24, Gateway IP: 192.168.2.1)

my server has only 1 lan port, and the ADSL modem was quite far away from the server, so cable connection from the server to the ADSL is not the option.
That's why I got to connect the ADSL Modem to WR#1 and relay it to the server's USB WIFI plugged on the server.

I ever install UBUNTU 10.04 Server and set it up as Router/Gateway and it works Great ! Clients from WR#2 and WR#3 connected to Server and Internet. But I was stuck on setting up the LDAP and SSO, firewall, samba, SSO, etc...... (infact, I've done many readings and trying to get those stuff work but to no avail).
 
So, could anybody help Please??? I urgently need to get my server up and running those stuff. 

Any help would be appreciate

---

### Post by mips on 2011-03-24
> **lindevox said:**
> 
The only problem I had with ClearOS is that during the installation process, I wasn't able to set it up as gateway mode because it didn't recognize or support usb wifi as network interface for my Internet connection.

Why don't you install it and setup as you like and afterwards get the wireless going and then setup the gateway.

---

### Post by Dragonbite on 2011-03-24
You could always try [[COLOR="Blue"]Zentyal[/COLOR]]("http://www.zentyal.org/"). It is Ubuntu Server with the eBox web-based interface for setting up everything!  

Look through their website and you should find what packages they include as to whether this will help you or not.

eBox (or Zentyal) can also be installed on top of an existing Ubuntu Server, but you may have to hunt a bit for those instructions.

Or another alternative is openSUSE for which Yast2 is available via the command line if you want it to be a headless server (handy being abne to SSH into it and running Yast2 through that).  I think they are working on a web-based interface too, but I haven't heard they have completed that yet.

---

