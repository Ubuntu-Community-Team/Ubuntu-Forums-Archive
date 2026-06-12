---
title: "Virtualbox host to guest networking with NAT"
date: 2010-07-10
forum: Virtualisation
---

### Post by Thyagaraj on 2010-07-10
I've guest ubuntu operating systems installed in oracle virtualbox. I've  a ubuntu 10.04 host operating system with static public ip address. 
I could access internet on guest os only if I select the NAT as network mode  in virtual box settings and this is fine, but host to guest networking is not possible.

I want to connect my guest os from host via ssh.

Plz need step by step guide...

---

### Post by Thyagaraj on 2010-07-21
Please anyone help me...

---

### Post by roni21 on 2010-07-21
[http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux](http://www.linuxjournal.com/content/using-windows-xp-virtualbox-linux)

hope that helps..

---

### Post by Nerflander on 2010-07-22
cant you just use 2 network adapters virtual ? I made a virtual webserver with a host and nat adaptar. Host only for the webserver and nat for the internet.


might be helpfull :)

---

### Post by Thyagaraj on 2010-09-10
No, even after adding one more interface it is not working. Any more idea?

---

### Post by Thyagaraj on 2010-09-12
Please any one simply put an end to this issue.

---

### Post by TheFu on 2010-09-12
> **Thyagaraj said:**
> Please any one simply put an end to this issue.
I didn't have any issue, but I use bridged networking, not NAT.  Also verify that you haven't firewalled any external connections.

I use a manually created brdige - `brctl` on the host.

Sorry, this isn't much help.

---

### Post by Kurtosis on 2010-09-13
I use Bridged Adapter too, though my host doesn't have a static IP.  Everything is on the LAN behind a router/firewall, and I can both access the Internet from my guest OS, and ssh/ftp both host->guest and guest->host using their LAN IPs (192.168.2.x).

Are you sure you couldn't access the Internet from your guest using Bridged Adapter?  Try that again just to make sure:

Settings -> Network -> Attached To: Bridged Adapter.  The default name eth0 should be fine.

---

