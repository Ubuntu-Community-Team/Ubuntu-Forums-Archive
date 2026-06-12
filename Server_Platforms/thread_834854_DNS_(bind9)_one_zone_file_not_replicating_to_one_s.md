---
title: "DNS (bind9) one zone file not replicating to one slave server"
date: 2008-06-19
forum: Server Platforms
---

### Post by aussie2008 on 2008-06-19
DNS (bind9) one zone file not replicating to one slave server. One Master server two slave server(A,B) all zone transfer to two slave server are working fine. All Zone tranfer fyn, except one zone file not transfering from master to slave A. same zone file transfering okay from master to slave B there is not zone file syntax issue. bind9 congfig file is okay on slave B because it is transfering all other zone files. master server in logs it is saying transfer start, transfer end. SlaveB server in logs it is saying, connected to master server: Give up: time out., transfer end.:)

---

### Post by RealPSL on 2008-06-19
There should be an indicated in /var/log/messages on why the transfer is failing. Can you take a look and share that? I would check both the master and the slave.

---

### Post by aussie2008 on 2008-06-19
> **RealPSL said:**
> There should be an indicated in /var/log/messages on why the transfer is failing. Can you take a look and share that? I would check both the master and the slave.

slave logs:  
Jun 20 12:10:04 localhost named[5265]: transfer of 'example.com.au/IN' from 192.168.1.20#53: connected using 192.168.1.21#60550
Jun 20 13:10:04 localhost named[5265]: transfer of 'example.com.au/IN' from 192.168.1.20#53: giving up: timed out
Jun 20 13:10:04 localhost named[5265]: transfer of 'example.com.au/IN' from 192.168.1.20#53: end of transfer

master logs:
Jun 20 13:10:49 dns1 named[28857]: client 192.168.1.21 #60038: transfer of 'example.com.au/IN': AXFR-style IXFR started
Jun 20 13:10:49 dns1 named[28857]: client 192.168.1.21#60038: transfer of 'example.com.au/IN': AXFR-style IXFR ended

---

### Post by RealPSL on 2008-06-23
I assume the master DNS server is working. Did u enable a firewall on either server? If yes please make sure that port 53/udp and 53/tcp are enabled. Based on the messages it does not seem to be a configuration issue because the master does not deny the slave access. I also assume that the configuration on the master for that zone is valid and available.

---

### Post by aussie2008 on 2008-06-27
Primary DNS server and one slave DNS server in DMZ zone. and one slave NAT on router. I have already checked that 53 TCP/UDP are opened for this server because all other zones are transfering fine except one zone to the one slave NAT on router.

---

### Post by RealPSL on 2008-07-03
Is there any change we can see the configuration and the zone file.

---

### Post by aussie2008 on 2008-07-03
I have compared the configuration named.conf and zone file with other slave. everything is the same on both slaves. 

on slave having problem. showing 
#rndc status

number of zones: 32
debug level: 0
xfers running: 1
xfers deferred: 0
soa queries in progress: 1
query logging is OFF
recursive clients: 0/1000
tcp clients: 0/100
server is up and running

:confused::(

---

### Post by RealPSL on 2008-07-06
Aussie,

Are you writing the zone that is not replicating to the same directory as the others? Is apparmor enabled on your host?

---

### Post by aussie2008 on 2008-07-06
apparmor is not enabled to the host. Yes, 

I am writting to the zone that is not replicating to the same directory as the others.

---

### Post by RealPSL on 2008-07-10
Okay you almost have me stumped. I need you to test one last think for me. Use nslookup on your slave server as follows

```
$ nslookup
> server address_of_master
> ls domain

```

You should get a full listing of the domain we are trying to transfer. If not hopefully there is some kind of error message. If not we are going to have to start some debugging to figure this out.

---

### Post by aussie2008 on 2008-07-11
> ls domain
The 'ls' command is not implemented.

i got this error message

---

### Post by RealPSL on 2008-07-16
Sorry about that. That was dropped in bind 9. I am out of ideas :(

---

### Post by PraysToPan on 2008-07-17
> **aussie2008 said:**
> > ls domain
The 'ls' command is not implemented.

i got this error message

dig has superseded most of nslookup.  From your secondary try:

dig axfr @primary.server.address domain.to.transfer

Jon

---

