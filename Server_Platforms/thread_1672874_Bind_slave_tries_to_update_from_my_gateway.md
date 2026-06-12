---
title: "Bind slave tries to update from my gateway"
date: 2011-01-21
forum: Server Platforms
---

### Post by diablorick on 2011-01-21
I have 2 nameservers setup, a master and a slave. when I first setup the slave, I restarted bind9 and all of the zone records propagated just fine. Today, I updated one of the records on the master (no problems), but when I restarted bind9 on the slave it gave me a FAILED message. I checked the log and it was trying to receive notify's from my gateway address (192.168.10.1), and got "Failed to update from non-master". I did some research and found several people having a similar problem, but their slaves were trying to update from their own IP, not from the gateway IP. I tried their solution (allow-notify { 192.168.10.1; })
but all that did was allow the slave to restart bind without errors, it still doesn't update the records. It says "zone is up to date" but it's not.
IP's are:
Gateway  192.168.10.1
Master     192.168.10.200
Slave      192.168.10.201

All of my zone records have the masters statement set to 192.168.10.200
I don't know how it even came up with the gateway address
Any help would be greatly appreciated!!!!

---

### Post by SeijiSensei on 2011-01-21
It sounds as though the gateway is doing network address translation for addresses on your LAN.  Is this an off-the-shelf router or a box you built?  If the latter, check your iptables rules to make sure traffic within 192.168.10.0/24 isn't being NAT'ted. You should have a FORWARD rule for internal traffic ahead of any MASQUERADE rules.

---

### Post by diablorick on 2011-01-21
Thanks for the quick response. 
I have a Watchgard firebox x750e core. In the watchgard, I have the public IP's for the nameservers NAT'd to the private IP's

---

### Post by diablorick on 2011-01-21
I just added a new zone and it went to .200 and transferred the file just fine. It only goes to .1 if it's looking for notify's.
now, if I restart bind9, it will go to .1 to find updates for the sites. 
I think I need to change something in Bind9, but i'm not sure what

---

