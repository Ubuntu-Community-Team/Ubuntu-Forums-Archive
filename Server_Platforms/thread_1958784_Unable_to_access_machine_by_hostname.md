---
title: "Unable to access machine by hostname"
date: 2012-04-14
forum: Server Platforms
---

### Post by Scrumps on 2012-04-14
I recently switched from Kubuntu to Ubuntu as an update that kept coming down onto my machine would screw up my ability to automatically mount drives.

Thinking that it would resolve it, I installed Ubuntu. It didn't. Which is fine, I can work around the annoyance. 

Anyways, now, with Ubuntu I am left with a machine that can't advertise it's own hostname on a network. 
```


C:\Users\Andrew>ping dataslum

Pinging Dataslum [fe80::383a:b85:f5f5:f503%12] with 32 bytes of data:
Reply from fe80::383a:b85:f5f5:f503%12: time<1ms
Reply from fe80::383a:b85:f5f5:f503%12: time<1ms
Reply from fe80::383a:b85:f5f5:f503%12: time<1ms
Reply from fe80::383a:b85:f5f5:f503%12: time<1ms

Ping statistics for fe80::383a:b85:f5f5:f503%12:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Users\Andrew>

C:\Users\Andrew>ping netslum

Pinging NETSLUM [10.10.10.223] with 32 bytes of data:
Reply from 10.10.10.223: bytes=32 time<1ms TTL=128
Reply from 10.10.10.223: bytes=32 time<1ms TTL=128
Reply from 10.10.10.223: bytes=32 time<1ms TTL=128
Reply from 10.10.10.223: bytes=32 time<1ms TTL=128

Ping statistics for 10.10.10.223:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Users\Andrew>nslookup server
Server:  UnKnown
Address:  10.10.10.254

Non-authoritative answer:
Name:    server
Address:  67.215.65.132


C:\Users\Andrew>nslookup netslum
Server:  UnKnown
Address:  10.10.10.254

*** UnKnown can't find netslum: Non-existent domain

C:\Users\Andrew>ping server
Ping request could not find host server. Please check the name and try again.

C:\Users\Andrew>

```

I googled this issue, and I noticed that the massive amounts of response was to either add an entry to every computer's host file pointing to the machine. This is not feasible, I have too many machines.

I also found the answer to setting up bind9. I already had bind9 installed on my machine, however, all of the guides I have found are to configure bind9 for Domain's, since I am not a part of a domain, I don't quite understand how it will be applied. 

I would appreciate some help with getting this solved. 
hosts file
```

127.0.0.1	localhost
127.0.1.1 	server

```

---

### Post by sj1410 on 2012-04-15
You have to configure netbios ip to name mapping in your samba server. nmbd is the daemon which responds to netbios queries. Edit /etc/samba/lmhosts

For more information have a look at 

[http://manpages.ubuntu.com/manpages/intrepid/man5/lmhosts.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/lmhosts.5.html)

[http://manpages.ubuntu.com/manpages/intrepid/man8/nmbd.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/nmbd.8.html)

---

### Post by Jose Catre-Vandis on 2012-04-15
Yep, I found the only way to do this was to use the samba server (netbios name) to dish up a name.

---

### Post by rubylaser on 2012-04-15
Or, just make a host entry on your DNS server for that hostname.

---

