---
title: "Setting up webserver behind linksys router"
date: 2005-02-16
forum: Server Platforms
---

### Post by dbwiddis on 2005-02-16
I'm a relative n00b to the Linux world, having converted my laptop a week ago (found Ubuntu on my third try at a stable distribution and love it!) and decided to take my old machine and turn it into a server, installing ubuntu on it as well.  I'm running into a few small problems, though.

Yes, I've read the other recent threads in this forum on the subject, and pondered adding my question to them, but call me selfish, I want my own thread. ;)  I **did** try the suggestions there, though...

My router is a Linksys WRT54G.  I've upgrated the firmware to HyperWRT 2.0b4 which adds a bit of functionality to the standard firmware, but is mostly compatible.  The machine which I want to use as a webserver is wired into the router.

Problem #1: Static IP.  Because the router's port forwarding rules require an IP to be specified, I want to make sure my webserver machine always has the same IP.  I tried using the System Tools > Networking > Network Settings, highlighting my eth0 card and seleting properties, and entering a manual IP.  However, it doesn't seem to "stick" or work... it remains at its DHCP-assigned address.  I tried releasing the DHCP address, entering the manual IP, and rebooting, but it went ahead and grabbed another DHCP address on reboot.  I'm guessing I'm doing something wrong but I can't figure out what.

I've looked at the router for places to assign static IP's.  There's a section where you can enter static IP's, but the documentation on how to use them is nonexistent.

Problem #2:  Linksys router.  Not necessarily an ubuntu problem, but... I've managed to get Port Forwarding to work correctly and connect to my server on several different ports (ssh, ftp) but it doesn't seem to work for port 80.  Other posts indicate it only works if I have it pass through a different address, and I've tried triggering it to go to 8080 (I have my Apache listening on both 80 and 8080.)  It works just fine if I connect to the webserver from my WLAN, but doesn't seem to work from the "rest of the world".  I can set up the webserver on just about any port other than 80, and it works... but I want a simple URL without adding port numbers!  (I'm using dyndns.org).  Has anyone had experience pointing the Linksys router to a server webpage?

---

### Post by Rottweiler on 2005-02-16
Any chance your ISP is blocking port 80? Many do.

---

### Post by dbwiddis on 2005-02-16
[QUOTE=Rottweiler]Any chance your ISP is blocking port 80? Many do.[/QUOTE]Hmm. Hadn't thought of that.  It's entirely possible... the question is how I would figure that out...

---

### Post by DJ_Max on 2005-02-16
Port 80 is the standard HTTPD port. So if you can visit this forums, you can access port 80.

---

### Post by alastair on 2005-02-16
For doing a manual/static IP, the file you might want to check is :

/etc/network/interfaces

For eth0 static - something like :

-----------------------------------------------------
iface eth0 inet static
        address 192.168.1.X
        netmask 255.255.255.0
        gateway 192.168.1.X
 
auto eth0
-----------------------------------------------------

and then :

sudo ifdown eth0
sudo ifup eth0

(get rid of any DHCP definition for eth0 e.g. "iface eth0 inet dhcp")

You can also turn off DHCP at the router if you don't want it - I don't own the router but a users guide is here :

[ftp://ftp.linksys.com/pdf/wrt54g_ug.pdf](ftp://ftp.linksys.com/pdf/wrt54g_ug.pdf)

As for port forwarding - check any firewall/filtering on the router - else, as said above, make sure port 80 is passed by your ISP ...

---

### Post by Rottweiler on 2005-02-16
[QUOTE=DJ_Max]Port 80 is the standard HTTPD port. So if you can visit this forums, you can access port 80.[/QUOTE]No. He's talking about *inbound* access to port 80. Being able to view this forum only proves he has *outbound* access. It's not at all unusual for ISPs to block inbound access to "server" ports like 80 as their TOS probably say you can't run servers.
 
 Dunno if that's what's happening here or not. You might just call your ISP or check their support pages.
 
 But if you can access port 80 on the LAN and the LinkSys has 80 forwarded to it but you can't see it from outside I'd say there is a pretty good chance they're blocking it.

---

