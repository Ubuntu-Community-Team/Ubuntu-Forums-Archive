---
title: "Need help on MySql connection delay with Windows Machines"
date: 2011-03-09
forum: Server Platforms
---

### Post by finito on 2011-03-09
At first I thought the Delay was normal.

After looking around it seems that it's not true.

I made a post [here]("http://forums.devshed.com/mysql-help-4/linux-server-windows-clients-delay-in-connection-793936.html").

The Problem seems to be related to DNS.

The Server in Question is not Online (as in on the web), all machines are on local ethernet.

From What I understand DNS is to mask the IP like a named variable for each IP.

I am still figuring out the ins and outs of a linux server. DNS is something I have little or no grasp over.

So I need help in setting up the DNS for this scenario case. All guides I have seen seem to be for web servers which is where I stop reading and look for other guides. 

I have webmin and Bind9 installed on the server.

It is a 10.04 64-bit machine.

Any help is greatly appreciated.

Peace.

---

### Post by SeijiSensei on 2011-03-09
The Domain Name Service is like "directory assistance."  You tell the browser you want to go to ubuntuforums.org, and your machine's DNS client points the browser at the corresponding IP address, 91.189.94.12.

You can avoid using DNS entirely by using IP addresses instead. Give the MySQL server a fixed IP address and enter that in the hostname field of the ODBC driver instead of a name.

DNS is not just a Linux thing.  It's a fundamental protocol on the Internet.  For clients, it's rarely an issue, but if you start to deploy servers and want to refer to them with human-readable names, you may find you need to set up a DNS server as well.

---

### Post by finito on 2011-03-09
I am aware DNS is OS independant, It's a Network protocol.

I am using the .net connector not the ODBC connector.

But I will try changing the connection string.

Thanks for the tip.

But could you point me or tell me how to set it up?

Peace.

---

### Post by finito on 2011-03-10
My connection string:

```
SERVER=192.168.1.2;DATABASE=XXXX;UID=YYYY;PASSWORD=ZZZZ;
```

This was the connection string So I don't think it's a DNS issue anymore.

I am thinking of implementing ODBC Now.

Does anyone else know what it could be.

Peace.

---

### Post by finito on 2011-03-10
Tried adding me Name instead of IP same result.

Require Help.

Peace.

---

### Post by SeijiSensei on 2011-03-11
I connect nearly instantaneously to a machine hundreds of miles away over the Internet using Access with ODBC.  I've done this with both MySQL and, more commonly, PostgreSQL.  I know nothing about .Net so I can't help you there.

If all the DSN's have IP addresses and not symbolic hostnames, it can't be a DNS problem.

---

### Post by finito on 2011-03-12
I am recoding everything to OBDC to see if that solves it.

I will let you know if it worked.

Peace.

---

### Post by finito on 2011-03-14
Solved Posted fix in the above link.

Peace.

---

