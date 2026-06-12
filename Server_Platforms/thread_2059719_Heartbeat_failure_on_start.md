---
title: "Heartbeat failure on start"
date: 2012-09-18
forum: Server Platforms
---

### Post by ckoble on 2012-09-18
I am currently trying to set up heartbeat/pacemaker on (2) 10.04.4 vm's in VirtualBox. Neither are running apache or anything special, just base installs at the moment. eth2 is set up as a static ip on both machines with VB network adapter set to bridged. I added the hostname/ip to each machines list, and verified I can connect to the other machine using the hostname.

My ha.cf for both nodes is as follows:

autojoin none
bcast eth2
auto_failback on
warntime 3
deadtime 6
initdead 60
keepalive 1
node Auth0 Auth1
crm yes
respawn

When I run heartbeat start I get the following error:
Starting High-Availability services:  Heartbeat failure [rc=6]. Failed.

heartbeat[16408]: 2012/09/18_13:33:11 info: Version 2 support: yes
heartbeat[16408]: 2012/09/18_13:33:11 ERROR: Invalid uid [] specified for client child
heartbeat[16408]: 2012/09/18_13:33:11 ERROR: Heartbeat not started: configuration error.
heartbeat[16408]: 2012/09/18_13:33:11 ERROR: Configuration error, heartbeat not started.

Google searching has yielded no help on the problem :(

---

### Post by darkod on 2012-09-18
This is part of something else, but it has very exact and short instructions for heartbeat. Just focus on the content of the three config files as posted in the middle of the article. I have used it, it works. Give it a shot. I didn't add any content to the three config files except what's in the article.
[http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html](http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html)

---

### Post by opensshd on 2012-09-18
"You have to create haclient and hacluster users and groups before
installing/compiling Linux-HA"

Re: [http://comments.gmane.org/gmane.linux.highavailability.user/11570](http://comments.gmane.org/gmane.linux.highavailability.user/11570)

Maybe helpful?

---

### Post by ckoble on 2012-09-18
Checked and both are already added

---

### Post by ckoble on 2012-09-18
Yeah, I've messed with the config a million times. Is it possible that my networking is incorrect? The only eth setup on the machines is eth2, which is the bridged connection through virtual box. if I try to add the mcast with an ip it always gives the error:
 ERROR: glib: mcast [eth2] bad addr [192.168.0.202] (tried multiple addresses here)
Other than that the setup is exactly as described.

---

### Post by darkod on 2012-09-18
If it's bridged you should be fine. I use it like that in VBox for testing too. If you used the same subnet as your LAN and bridged connection, you should be fine.

Use eth2 in the config file.

PS. If you are unsure post your /etc/network/interfaces.

---

### Post by ckoble on 2012-09-18
/etc/network/interfaces are like this:
---------------------------
Auth1:

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 192.168.0.198
netmask 255.255.255.0
gateway 192.168.0.1

---------------------------
Auth0:

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 192.168.0.197
netmask 255.255.255.0
gateway 192.168.0.1

---

### Post by darkod on 2012-09-18
So, you're trying to set up 192.168.0.202 on the heartbeat, right?

In that case the file haresources should say something like:
Auth0 IPaddr::192.168.0.202/24/eth2/192.168.0.255

Is that how you have it?

PS. And in ha.cf try to separate the nodes in different lines like:
node Auth0
node Auth1

---

### Post by ckoble on 2012-09-19
Yeah, the only thing is that its going to be used along with pacemaker, so I set crm to true in ha.cf, and when I run heartbeat start it states:
heartbeat[17808]: 2012/09/19_09:29:48 info: Version 2 support: yes
heartbeat[17808]: 2012/09/19_09:29:48 WARN: File /etc/ha.d//haresources exists.
heartbeat[17808]: 2012/09/19_09:29:48 WARN: This file is not used because crm is enabled

---

### Post by darkod on 2012-09-19
I don't know how it works together with pacemaker. The error in config might be on the pacemaker side. I guess you can check if you disable crm temporarily, if only heartbeat will start and work fine. Delete all entries in the config files that are related to pacemaker.

If that works, then continue working on a configuration for pacemaker.

---

### Post by ckoble on 2012-09-19
Alright, removed the crm yes so its reading from haresources, set that up exactly like you specified, and moved the node Auth 0 Auth1 to separate lines. The haresources is coming back stating heartbeat is not started on that node, which is expected I guess but the same invalid uid error is showing afterwards

---

### Post by darkod on 2012-09-19
I don't know what the uid is complaining about, but it says client child which should mean the slave server. So, you need to double check the configuration (heartbeat and networking) on the slave server.

Are the heartbeat files (the three files) identical on both servers? They need to be.

Is it possible that the servers consider the network adapter as eth0 like it's usually named? I'm not sure you can simply call it eth2 if the machine is considering it to be eth0. Have you checked network connectivity? Do the servers have working internet access for example through your home router?

---

### Post by ckoble on 2012-09-19
I copied the main server files over to the slave so they match exactly, checked internet config on both and both have outside access to the web

---

