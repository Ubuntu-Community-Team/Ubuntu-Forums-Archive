---
title: "two machine server setup help"
date: 2012-04-01
forum: Server Platforms
---

### Post by KMatsumari on 2012-04-01
***
UPDATE:
I am closing this thread now as it has been inactive for too long, and I have abandoned this setup as of now until I get off of my dynamic DSL connection. See my other thread as I have the same existing problem and I am in desperate need to fix it (my only other thread, so search for threads created by me). I will mark this SOLVED, but technically it isn't.

NOTE: Using the newly aquired ISPConfig 3 Manual, I have discovered how to do this properly, but my mail system is still being persistently retarded. See my other thread on this issue.
***

I originally tried to make my server be that "all-in-one" perfect server from the howto.sourceforge site, but it seems that my mail server was the only thing not working. I have decided to stray away from that type of setup, and go with a second machine as my mail server, and the rest on the main domain host. Here is what's up:

Host system runs Oracle VirtualBox 4.1.8, runs on eth0 DHCP.
 - VM "main" is the domain web, ftp, and ISPConfig3 server
 - VM "mail" is the domain mail server

My host system is Ubuntu 11.04 Oneiric Ocelot Desktop (GUI) x86.
My VM servers are Ubuntu 10.04 Lucid Lynx Server x86.

NETWORK

Modem has built-in router, so no options besides DMZ for all port forwarding. I can handle specific limitations and port security myself. Also using a second router because there are multiple other devices on my network.
ROUTER 1
 - NIC 1: DHCP to Second Router
 - NIC 2: [DMZ] Static IP to "main" on Host eth1
 - NIC 3: DHCP to "home" PC
 - NIC 4: UNUSED
 - INTERNET: Direct DSL to ISP (modem built-in)

ROUTER 2
 - NIC 1: DHCP to Host system running VBox on eth0
 - NIC 2: [DMZ] Static IP to "mail" on Host eth2
 - NIC 3: DHCP to XBOX
 - NIC 4: UNUSED
 - INTERNET: DHCP to ROUTER 1

On my "main" VM, I am going to have basically everything from the "perfect ubuntu server" tutorial at [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3) with the exception of the mail server parts. The mail server pieces will go on my "mail" VM, which I want to be operated by ISPConfig3 on my "main" system.

The Website I am using is kelina-enterprises.com. This domain name is registered by me, and I already have DNS services for my public IP address and ez-ipupdate in daemon with a personal script that updates my DSL IP address from my "main".

I want my "main" server to host the web server at my domain, and I want my "mail" server to run as the subdomain mail.kelina-enterprises.com. I want the squirrelmail login php page to run from this point. As you can see, my "mail server will not be directly accessible from outside the network as it will be on the second router and not on the first, so it will not interfere with "main" having the public IP as its own. I need ISPConfig3 to operate "mail" as the entire domain mail server.

The mail server will have squirrelmail, courier, and will also be its own IMAP and POP3 host. However, I want ALL email accounts on mail.kelina-enterprises.com to be @kelina-enterprises.com, not @mail.kelina-enterprises.com.

So there you have it, everything I am trying to fix and setup. I am very familiar with the setup process and such for the single machine, but I need a few pointers on how I should go about making this version of my server system work properly.

I am not sure whether or not I am supposed to make all host names in the server system the FQDN, or simply the host names I put in double quotes here ("main" and "mail"). replies should tell me which one to use from this list:

1. "main" server hostname as MAIN, "mail" server hostname as MAIL
2. "main" server hostname as main.kelina-enterprises.com, "mail" server hostname as mail.kelina-enterprises.com
3. "main" server hostname as kelina-enterprises.com, "mail" server hostname as MAIL

Again, I am not quite sure what is necessary for my setup.

In ISP Config 3, should I make the subdomain "mail.kelina-enterprises.com" and the host of that subdomain is the LAN IP address of "mail"? Or is there another way to make "mail" a proper working subdomain?

Lastly, Since my ftp server is hosted on "main", how can I make the ftp access separate from the main domain (i.e. ftp.domain.com as opposed to domain.com/ftp)?

All help is appreciated, and I hope to have this system up and running soon as it is my business that is hurting while it is down. **NO I WILL NOT PAY FOR HOSTED SERVICES!** That's why I chose Ubuntu in the first place. Free is free.

---

### Post by volkswagner on 2012-04-01
Why not put both servers on router two?  Set Router two as the DMZ from Router one.  I think this will give you more port forward flexibility.

---

### Post by KMatsumari on 2012-04-04
My second router is an older linksys B-series, and it doesn't allow me to forward its DMZ statically for some reason (there are no firmware updates available, unfortunately). However, devices can have a static IP to this router simply by setting up their own NIC with the static information (unlike my first router, which must have a static IP entry on the router AND in the device's NIC settings). But my problem is not how to setup my server on a router (I did that already, many times), it is how I should more or less configure the actual server installation (using the terminal in my server), because I just seem to run into a tiny problem here or there that halts the whole thing, and once fixed, another problem comes up.

with my single machine server I had put together previously, I had everything online and running, except for my mail server. Now I decided that I want my mail server to be a second machine, but I want this machine to be controlled by my ISPConfig3 installation on my main server machine. I also want my mail server to be both of the following:
 - located at [http://mail.kelina-enterprises.com](http://mail.kelina-enterprises.com)
 - collect mail for the entire domain, all accounts being @kelina-enterprises.com (not @mail.kelina-enterprises.com)

As a note for some of you guys who jump to answer before reading all that I have taken the time to write (a couple of you have done it to me already on the launchpad), I already have my domain name registered (kelina-enterprises.com) and I have DNS services for my domain name, all through easydns.com. Do not tell me that my site is not accessible and that is what my problem is. I took it down because my mail server isn't working, and I am in the process of starting over from scratch right now.

I need some guidance from anyone who has installed and setup an ubuntu server system (non-GUI) using 2 machines (two ubuntu server installations) and ISPConfig3. Again, my questions regarding the setup of the hostnames is necessary before I can start the process, and I do not have the time or extra space right now to try all three choices, I need the correct one and quick.

---

