---
title: "Apache - Connection Timed Out"
date: 2012-01-12
forum: Server Platforms
---

### Post by Nexusx6 on 2012-01-12
After hours of googling and debugging I'm at a loss as what to do next. I have just recently updated my servers hardware and installed 11.10 on it (was previously running 10.04). I installed LAMP from taskel, and forwarded port 80 on my router. The problem I'm having is that when I browse the server on its LAN IP I get the default Apache index.html just find, however, if I attempt the same from the external IP I simply get a "Connection has timed out" error and I cannot figure out why.

Neither access.log nor error.log show anything
ShieldsUp confirms that 80 is open

```
 $ netstat -ntpl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      14242/dovecot   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      11404/mysqld    
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      14242/dovecot   
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      14242/dovecot   
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      24826/apache2   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      14697/sshd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      11979/master    
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      14242/dovecot   
tcp6       0      0 :::995                  :::*                    LISTEN      14242/dovecot   
tcp6       0      0 :::110                  :::*                    LISTEN      14242/dovecot   
tcp6       0      0 :::143                  :::*                    LISTEN      14242/dovecot   
tcp6       0      0 :::22                   :::*                    LISTEN      14697/sshd      
tcp6       0      0 :::993                  :::*                    LISTEN      14242/dovecot   

```

Apache Access Log
```
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [11/Jan/2012:23:56:01 -0800] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.20 (Ubuntu) (internal dummy connection)"
192.168.11.3 - - [12/Jan/2012:00:07:43 -0800] "GET / HTTP/1.1" 304 209 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:9.0.1) Gecko/20100101 Firefox/9.0.1"
192.168.11.3 - - [12/Jan/2012:00:07:47 -0800] "GET / HTTP/1.1" 304 208 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:9.0.1) Gecko/20100101 Firefox/9.0.1"
192.168.11.3 - - [12/Jan/2012:00:07:48 -0800] "GET / HTTP/1.1" 304 208 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:9.0.1) Gecko/20100101 Firefox/9.
```

Help would be greatly appreciated, I use this server heavily during the semester :(

---

### Post by lisati on 2012-01-12
Do you have a dynamic IP address that might have changed?

---

### Post by Azdour on 2012-01-12
Hi,

The computer you are using to 'browse the server on its LAN IP' is this the same computer you are trying to access the server via its external IP.

If so then it will not work unless you go through a proxy site. From what I understand you cannot access the external IP if you are on the same LAN as the server.

I've had this problem before and for testing purposes I go through proxy websites to check that the website is up and running.

Hope that helps.

---

### Post by Nexusx6 on 2012-01-12
@Azdour: That worked! Oh man, I've been at it for something like 10 hours over the past two days and this whole time it was actually working. What a strange glitch, I didn't have to do that before, I wonder why it is now. Thank you for your help :)

---

### Post by Azdour on 2012-01-12
Hi,

Glad that sorted it.

See post #7 for an explanation on this thread:

[http://ubuntuforums.org/showthread.php?t=1798673](http://ubuntuforums.org/showthread.php?t=1798673)

Not sure why it would have worked for you before, I've always had this.

BTW:

> Always mark your solved problems with [SOLVED] in your subject line...

I think you need to actually use the thread tools (up by the 'Search this Thread' link) to mark something as solved otherwise it will not show correctly if you just alter the subject line.

---

### Post by Nexusx6 on 2012-01-12
How interesting. Yeah I can't explain ethier why it was working before then, I have the same router still. Weird. Well I'm glad you were browsing the forums today!

> I think you need to actually use the thread tools (up by the 'Search this Thread' link) to mark something as solved otherwise it will not show correctly if you just alter the subject line. 

Whoops, thanks. When I made that sig the forums didn't have half the features they do now and its been a while since I've been back; thank you for catching that. Geeze I really have to update that sig...

---

