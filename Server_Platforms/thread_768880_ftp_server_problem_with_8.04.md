---
title: "ftp server problem with 8.04"
date: 2008-04-26
forum: Server Platforms
---

### Post by drejto on 2008-04-26
Hi,

I've installed 8.04 LTS Server Edition and pure-ftpd.
My problem is that I can connect to the FTP server locally (telnet localhost 21), but not remotely (telnet IP 21). When I try to connect remotely I get 'Connected to IP' but no welcome message, nothing.

Firewall is not set up (basic config), but even with firewall and FTP enabled, I encounter the same error.

Does anyone else have similar problems with the new distro?
How could I solve this?

Thanks,
David

---

### Post by Monicker on 2008-04-26
I would check to see if the ftp daemon is only listening on localhost, instead of a remotely accessible ip address.

```
netstat -anltp | grep LISTEN
```

---

### Post by drejto on 2008-04-26
Thanks for your fast response.

Here is the output of the command you suggested:
```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4656/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4862/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      19774/pure-ftpd (SE
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      4789/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4862/apache2
tcp6       0      0 :::21                   :::*                    LISTEN      19774/pure-ftpd (SE
tcp6       0      0 :::22                   :::*                    LISTEN      4558/sshd

```

---

### Post by Monicker on 2008-04-26
Its definitely listening on all ip address.  I did not notice earlier your mention of the connect message so it seems to be trying.

Is there a firewall between the external client and the ftp server?  Is the client using passive or not for the connection?

---

### Post by drejto on 2008-04-26
There shouldn't be any firewall.
I did a clean install with some server applications (iptables -L lists nothing).
After it did not work, I installed ubuntu-firewall and enabled FTP.

The FTP client is using passive connection.

Here are two attempts from the local machine:
```

telnet localhost 21
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220----------....

telnet 192.168.1.158 21
Trying 192.168.1.158...
Connected to 192.168.1.158.
Escape character is '^]'.
Connection closed by foreign host.
```

---

### Post by Monicker on 2008-04-26
Hrmm.  Dunno then.

I would run tcpdump or wireshark on the ftp server, and see what that shows.  Is there nothing in the ftp server logs?  You may have to turn up the logging level.

---

### Post by freebeer on 2008-04-26
if the server is behind a router, you'll need to forward the ports to the server.

---

### Post by drejto on 2008-04-27
Looks like I have the problem solved:
Machine got IP via DHCP and 127.0.0.1 was set for its hostname's IP in /etc/hosts; changed that to the IP and it works now :)

Thanks for your help Monicker, freebeer!

---

### Post by kinemagician on 2008-06-16
> **drejto said:**
> Looks like I have the problem solved:
Machine got IP via DHCP and 127.0.0.1 was set for its hostname's IP in /etc/hosts; changed that to the IP and it works now :)

Thanks for your help Monicker, freebeer!
I had exactly the same problem!  It's a very subtle problem. However, your solution worked. Thanks, Ettore

---

