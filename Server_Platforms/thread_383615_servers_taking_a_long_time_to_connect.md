---
title: "servers taking a long time to connect"
date: 2007-03-13
forum: Server Platforms
---

### Post by Coogan on 2007-03-13
I don't know if this is a server problem or just a general problem, but I noticed this a while back.  I've got a Dapper box running both SSH and ProFTP servers, and the initial connection time is always SLOW.  By that I mean it may take 7-10 seconds to establish the connection.  It's not a real problem with SSH; once I connect, it's fine.  It's not like I'm getting lag or any other kind of network problem.  But when I'm transferring many small files via passive FTP, it can literally take about 12 seconds to transfer a single small file (like a modest JPG image), with 10 seconds spent just being making the connection.

It happens no matter what the system load.  It's not a major problem, but when FTPing many files, it can turn what should be a 8-10 minute job into one that can take over 30.  Any settings or tips would be greatly appreciated.

Coog

---

### Post by lloyd_b on 2007-03-13
Are you connecting to the servers by name or by IP address?  If by name, try using their IP address instead, and see if that resolves the problem.

DNS issues are one thing that can cause exceptionally long connect times.

Lloyd B.

---

### Post by Coogan on 2007-03-13
No DNS lookups involved.  Both SSH and FTP are connected to by IP, not domain name.

Coog

---

### Post by Brazen on 2007-03-13
try running ```
sudo top
```to see the load on the server.  Is this a virtual machine?

---

### Post by Mr. C. on 2007-03-13
Please show some ethernet stats and info:

```
ifconfig -a
netstat -s

```

Let's see if anything is suspicious.
MrC

---

### Post by MJN on 2007-03-13
> **Coogan said:**
> No DNS lookups involved.  Both SSH and FTP are connected to by IP, not domain name.

Coog

On the client you're right, however many server applications perform reverse lookups when logging initial client access hence the delay you're seeing could be the DNS timeout of the (failed) lookup.

A quick-proof solution would be to put the IP address (and name) of your client in the /etc/hosts file on the server - this will get checked before the DNS and eliminate any such delay.

This might not be the case here, but I think it's worth mentioning nevertheless.

Mathew

---

### Post by Coogan on 2007-03-15
> **Brazen said:**
> try running ```
sudo top
```to see the load on the server.  Is this a virtual machine?


I'll check, but I'm pretty sure it's not a server load issue.  Currently the system is running these servers: MySQL, Apache, ProFTP, DNS, and SSH.  Occasionally I'll run the Folding@Home client, which does use 99% of the CPU, but the connection delays are there whether it's running or not.  

Now that I think about it, the last server I put on the system was BIND, as a simple caching server, and it seems the delay started around that time.  I definitely know it didn't always take so long to connected.

I'll do the stuff everybody's suggested and post back later.  Thanks for the help.

Coog

---

### Post by PetePete on 2007-03-15
i have the same problem... connecting takes for ages over ssh (10+ seconds)
but it seems to only happen when connecting from my home laptop. When connecting from other locations it doesn't happen.

maybe the problem lies on your client side?

let me know if you resolve it. 
Thanks :)

---

### Post by d.j.schroeder on 2007-03-27
I have the same problem.  Server is basically idle, doesn't matter where I connect from FTP connections are terribly slow, 10-15 seconds.  Transfers after you have established a connection are ok.  I'm using proftp.

---

### Post by MJN on 2007-03-28
And you've tried the hosts file modification?

Mathew

---

### Post by galileon on 2007-04-01
same pb, gonna try:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

someone said it helps in another thread...

---

### Post by galileon on 2007-04-01
tried a few things to disable ipv6 but none worked...:(

---

### Post by d.j.schroeder on 2007-04-03
Is this the same as the host mod that MJN mentioned earlier?

---

