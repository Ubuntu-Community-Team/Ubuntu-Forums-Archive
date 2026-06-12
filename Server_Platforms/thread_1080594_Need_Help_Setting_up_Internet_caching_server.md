---
title: "Need Help Setting up Internet caching server"
date: 2009-02-25
forum: Server Platforms
---

### Post by Difranco1911 on 2009-02-25
I recently moved to a new house where the only highspeed internet available is satellite at 1.5Mbs downstream.  I have a Compaq Armada E500 Laptop with a P500Mhz, 512MB ram & a 40GB hard disk drive.   

I have installed Xubuntu 8.10 on it which seems to run very well.  So I would like to setup this laptop/server between my Satellite Modem and Wireless router to cache the internet and hopefully save on bandwidth.   This would be the physical layout:

{MODEM ETHERNET}-->{NIC1_LAPTOP_NIC2}<--{WANPORT_LINKSYS_ROUTER}

It seems that Squid is the standard in this area; however, I have been unsuccessful at adding the source ([deb http://http.us.debian.org/debian lenny main]("http://packages.debian.org/lenny/i386/squid3/download")) to Synaptic for Install.  Is there something better I can use?  

Also I would need to configure the xubuntu laptop to pass all traffic inbetween the NICs.


Can someone outline the steps for me to accomplish this task?

---

### Post by HermanAB on 2009-02-25
Squid-cache and Dan's Guardian is the standard nowadays.  Installing it is a bit of a chore.  (If you are lazy, then you need to use Mandriva Linux 2009 and click the wizard to set it all up for you.)  Otherwise, here is a guide for installing Squid-cache with Squidguard manually: [http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

### Post by Difranco1911 on 2009-03-01
I have Squid and Dansguardian installed on my XUbuntu Laptop.  Now I just need to figure out how to configure the laptop to route traffic, cache internet and filter the internet as requests are sent to Linksys router thru the Laptop and out the satellite modem.  

Is there a way I can do this?

---

### Post by Adina on 2009-03-02
Take a look at the iptables rules in this tutorial 

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)


I used this tutorial to forward internet connection from the wireless nic on my laptop to eth0 and connected another laptop to eth0 to share internet. I'm not sure but I think the iptable rules might work for you. Just be sure to have the two nics on separate subnets.

---

