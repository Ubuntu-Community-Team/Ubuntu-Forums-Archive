---
title: "All in one server"
date: 2006-09-05
forum: Server Platforms
---

### Post by traacer on 2006-09-05
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 
I'm running ubuntu 6.06 server with the ubuntu desktop. I want to run apache2, vsftp, promail, and bind. I have a static ip, and registered domain name. I've been trying to get it all to run on 1 machine, but with no luck. When it comes to bind, i have no idea what i'm doing. the machine is a amd athlon 3000, 512mb ddr, msi kt6v mobo. with a addon ide card, and additonal network card. The onboard ethernet has the static ip, the add on card is for the internal network. I have an external ip of 71.241.102.71, that i want to use as the domain traacer.org. The internal is 192.168.1.96. I have samba already running and sharing files internally. Currently i have the settings up at dnspark.com. I plan on running all the servers from my 1 machine, but don't know how to setup the iptables, and such.  This is the first complete server i'm setting up and am driving myself crazy with it. I'm using verizon dsl in pennsylvania if that makes a difference in anyway.

Network topology:

DSL IN -> WESTEL VERSALINK 327W (router/modem) ->
SERVER(192.168.1.96 - ETH0)(71.241.102.71 - ETH1)
then also from the router i have a line run to my main machine and my wifes, wireless turned off.

Thanks for the help!

---

### Post by zitch on 2006-09-05
Have you looked into this: [The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)?

I've installed using the Debian 3.1 version of this guide, and with the ISPConfig control panel, I've found managing multiple web domains and email accounts to be quite simple.

The only different from what you're trying to do is that the guide uses postfix for the email server and proftpd for the FTP server.

---

### Post by traacer on 2006-09-06
Correction to my ips. I called my isp and found out i can't get a static ip.  so i'm dealing with a dynamic ip on eth0 that will change to whatever ip my router gets when it refreshes, and 192.168.1.96 on eth1.  I still want to host traacer.org on my machine, but don't want to shell out any cash to use some domain forwarding site.  Any ideas?

---

### Post by chrisfay on 2006-09-07
If you're not stuck on running your own DNS then try setting up a free zoneedit account at [http://zoneedit.com](http://zoneedit.com). Then just create a zone with some records pointing to your server, add the name servers they give you to your registrar and you're good to go. 

Since you're on a dynamic IP, you'll probably want to download a dynamic dns client to update your zoneedit zones automatically that way if your IP changes, zoneedit will get that new ip and everyone can still access your servers without you doing anything.

---

