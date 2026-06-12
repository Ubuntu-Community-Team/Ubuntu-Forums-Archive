---
title: "dhcpd3 static MACs"
date: 2013-02-18
forum: Server Platforms
---

### Post by ke5sfy on 2013-02-18
The situation:  I'm attempting to install an Ubuntu 12.04 64bit server with Linux Terminal Server and TFTP that will host simple PXE boot kiosks.  The kiosks are PXE enabled and will retrieve an image from the LTS server I have set up.  The server is configured with 2 NICs, one connects to our office network (private class A) and the other connects to a private class C network.  I am able to boot the Wyse box, get an IP address and load an image from the LTS server.

The problem:  The dhcpd3 server is handing out 192.168.200.x addresses to clients on our main network at 10.x.x.x which has disastrous results.  The only way to prevent that is put all the Wyse clients on a separate network segment.  This is not feasible for our location. 

1 Logical process:  I want to configure static mac to IP addresses in the dhcpd3 config file for the Wyse clients and only respond to dhcp requests originating from these MAC addresses.  Our main dhcp server (windows 08 DC) can handle the bulk of the 350 computers.  Handing a class C IP to any machine not connecting to the LTS is detrimental to my R&D work and possibly my job.  :eek:

That's where I'm at.  Looking for ways to configure dhcpd3.  There very well may be a better alternative.  

Thanks in advance for any help.

KE5SFY

---

### Post by SeijiSensei on 2013-02-18
Take a look at this [example dhcpd.conf]("http://pic.dhe.ibm.com/infocenter/tivihelp/v3r1/index.jsp?topic=%2Fcom.ibm.tivoli.tpm.osdimg.doc%2Finstall%2Frosd_dhcpdconfexample.html") file.  Scroll about halfway down until you see the entries that use the "hardware ethernet" directive.  This enables you to assign a fixed IP address to a MAC.  I think you only need "hardware ethernet" and "fixed address" at a minimum.

---

