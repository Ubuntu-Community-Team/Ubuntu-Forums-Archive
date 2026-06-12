---
title: "ubuntu will not retrieve ip from windows dhcp server"
date: 2010-07-11
forum: Virtualisation
---

### Post by Robotuner on 2010-07-11
Hi:
I have a my own windows dns and dhcp server (windows2003 server) which is pretty basic.  my dns server is 192.168.111.2, Its gateway is 192.168.111.1 and my dhcp (also on 192.168.111.2) assigns ip addresses to any windows machine that connects to the network with an ip above 192.168.111.2.

I also have my own domain, so all windows machines on my network have a "domain", not a "workgroup" identification.  

I just installed Ubunto desktop (version 10.04) in a Virtual Box running on a Windows7 machine.  How do I get the ubuntu machine to join my domain and get an IP from my dhcp server in the proper range?

Currently when I run ifconfig on my ubuntu box I get eth0 inet addr of 10.0.2.15 and a local loopback ip of 127.0.0.1

For my Auto eth0 IPv4 Settings,I have the method set at Automatic DHCP and my DHCP Client ID: 192.168.111.2

My networking seems to be OK, or at least I can find my windows network and mount the different windows machines and get files, etc.  I also have internet access, . . . so the Ubuntu box appears to be able to functioning properly as a standalone machine, but that really isn't good enough.  

As a virtual machine (Virtual Box) I want to be able to get to it from my other machines via an IP address because I want to install MySql server on it so that, . . .  applications on my windows network can find the MySql server.

Any help would be appreciated.
Thanks.

---

### Post by dmizer on 2010-07-11
I have moved your request to the Virtualization section of the forums because this is a problem with how you've configured the virtual machine in VirtualBox rather than a problem with Ubuntu networking.

In VirtualBox, you'll need to change Ubuntu's network settings to "bridged" and make sure the "name" is pointed to your Windows computer's ethernet adapter.

Hope that helps! :)

---

### Post by HermanAB on 2010-07-12
Hmm, it sounds like you have multiple DHCP servers on your network.  Kill all but one.

---

