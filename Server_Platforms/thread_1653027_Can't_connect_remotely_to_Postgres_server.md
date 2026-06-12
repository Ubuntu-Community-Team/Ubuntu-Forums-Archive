---
title: "Can't connect remotely to Postgres server"
date: 2010-12-26
forum: Server Platforms
---

### Post by mattwl on 2010-12-26
I've been trying to fix this for a couple of days now, and have no idea what the problem is... posting this query as a last resort... thanks for any help. 

I keep getting this error trying to connect to newly installed postgres server on Amazon EC2 running Ubuntu Maverick Meerkat....

> could not connect to server: Operation timed out Is the server running on host "....ap-southeast-1.compute.amazonaws.com" and accepting TCP/IP connections on port 5432? 

I've updated config files, as follows...

pg_hba.conf
added
> host    all    all         124.168.242.0/24       trust
where 124.168.242.0 is the IP range of my ISP

postgresql.conf
> listen_addresses = '*'   
port = 5432

Any ideas what I am missing here? THanks.

PS.  I am attempting to connect with pgAdmin 3 client. I don't think the problem is the client.

Matt

---

### Post by furlabs on 2010-12-26
Are you forwarding port 5432 from your firewall/router to the postgres server?

Also, when you say 124.168.242.0 is the IP range of the ISP, I assume you mean the ISP at the client end?

---

### Post by koenn on 2010-12-26
> **furlabs said:**
> Are you forwarding port 5432 from your firewall/router to the postgres server 
Assuming he's running his database on an Amazon cloud server rather than, say, on a laptop in his bedroom, what ports exactly do you suggest need to be forwarded where ?

---

### Post by koenn on 2010-12-26
> **mattwl said:**
> 
Any ideas what I am missing here? THanks.


check network connectivity first :

is that ip address reachable from your PC ? (ping, traceroute, hping, nmap, ...)

is the server reachable by name ? (ping, ... as above, but by FQDN i.s.o. IP addr)


is anything listening on that port (nmap portscan, telnet addr portnr, ... )


If that all works, at least you know your problem is not caused by network issues. Then you can start diagnosing/debugging the applications
I don't know postgres so i wouldn't know what to look for except stuff like the things you posted (listen addr, port, ... ; allow/deny lists, ... ) but if all else fails you can run a packet sniffer (wireshark, tcpdump) and see what your client and the posgres daemon are saying to each other

---

### Post by mattwl on 2010-12-26
This is going to sound foolish, but for those that might come across this problem in the future...

I forgot to allow access to port 5432 on Amazon EC2 :/ 

Go to 'Security Profiles' in the EC2 control panel. 

Thanks everybody for the help!

---

### Post by koenn on 2010-12-26
cool

---

### Post by furlabs on 2010-12-26
> **koenn said:**
> Assuming he's running his database on an Amazon cloud server rather than, say, on a laptop in his bedroom, what ports exactly do you suggest need to be forwarded where ?

Sorry, didn't know what was meant by Amazon EC2 so I ignored it :P

---

