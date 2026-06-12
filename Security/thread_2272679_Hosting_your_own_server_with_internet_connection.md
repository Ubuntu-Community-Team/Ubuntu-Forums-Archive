---
title: "Hosting your own server with internet connection"
date: 2015-04-08
forum: Security
---

### Post by Drenriza on 2015-04-08
Hi all

I am currently looking into making a Debian Raspberry Tomcat server with a connection to the internet (WAN) from my home.
My question in this regard is "**what dangers do you need to attend when putting a home server on the internet**".

My home connection is a business connection, for faster support if the physical connection goes down outside my apartment in the ISP's network.
Like a cable that gets cut with more.

I use a Cisco router with a WIC card for WAN access, 100% managable through the CLI.

I am setting up a Debian Raspberry (unless their is a better solution single board and image wise) with RJ-45 and USB -> RJ-45 as a firewall between my router and internal network.
Segmenting my network with a DMZ zone for the Tomcat server.

Looking here for a running start with iptables [http://www.thegeekstuff.com/2011/06/iptables-rules-examples/](http://www.thegeekstuff.com/2011/06/iptables-rules-examples/)

If anyone have any advice on other area's / dangers i should be aware of or can share your experience with similiar projects, than i am very interested in hearing these.

Thanks on advance
Kind regards

---

### Post by coldraven on 2015-04-08
I'm no expert in servers but from what I've read one danger is people trying to brute-force their way in.
Install fail2ban and use SSH to login to your server.

[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

