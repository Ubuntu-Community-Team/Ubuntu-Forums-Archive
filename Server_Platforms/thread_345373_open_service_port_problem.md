---
title: "open service port problem"
date: 2007-01-24
forum: Server Platforms
---

### Post by slo on 2007-01-24
I have installed a ubuntu server on my box
I just install a LAMP server, only start proftpd/mysqld/apache/openssh
I use X-scan to scan my ubuntu found some prot been opened:
pop3
smtp
nntp
......

I never install these services, Is there anybody know why ?
or someone can provide a ubuntu server security guide ?
how to close these ports or only open just I want open ports?

---

### Post by jtc on 2007-01-24
Strange.

Perhaps they've gotten installed as dependencies to some other service/program?

Run the following to find out what programs are listening on the ports in question.

```
sudo netstat -tlp
```

---

### Post by slo on 2007-01-24
root@Wolfpack:~# netstat  -ltp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:mysql         *:*                     LISTEN     20970/mysqld        
tcp        0      0 *:ftp                   *:*                     LISTEN     11813/proftpd: (acc 
tcp        0      0 *:ssh                   *:*                     LISTEN     3442/sshd

---

### Post by jtc on 2007-01-24
Yeah, what netstat reports sounds like what should be running. Then the question is why X-scan says what it does.

Running X-scan on the server in question, or from another computer?

---

### Post by slo on 2007-01-25
I run X-sacn another PC to sacn the ubuntu server.

---

### Post by az on 2007-01-25
> **slo said:**
> I have installed a ubuntu server on my box
I just install a LAMP server, only start proftpd/mysqld/apache/openssh
I use X-scan to scan my ubuntu found some prot been opened:
pop3
smtp
nntp
......

I never install these services, Is there anybody know why ?
or someone can provide a ubuntu server security guide ?
how to close these ports or only open just I want open ports?

It sounds like your scanner is broken.  You are saying that you have ftp and ssh running and the scan didn't even pick that up?  Did you scan the correct box?

---

