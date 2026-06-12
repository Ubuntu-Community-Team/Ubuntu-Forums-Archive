---
title: "Fail to telnet localhost 25"
date: 2006-11-21
forum: Server Platforms
---

### Post by satimis on 2006-11-21
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

I followed Section "11 Postfix With SMTP-AUTH And TLS" on
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5)

to config LAMP server.  Encountered problem on running;
$ sudo telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.example.com ESMTP Postfix (Ubuntu)

(hanging here sometimes - then popup)

421 server1.example.com Error: timeout exceeded
Connection closed by foreign host.

```

Please advise how to fix the problem.

TIA


B.R.
satimis

---

### Post by mssever on 2006-11-22
My apologies if you've already done this, but after doing telnet localhost 25 (you shouldn't need sudo, by the way) and getting the 220 message, type ```
ehlo localhost
``` **You probably won't get a prompt,** and you might not even see the characters you type. I'm getting this from the page you linked to; I've never messed with mail servers before.

---

### Post by satimis on 2006-11-22
Hi mssever,

> if you've already done this, but after doing telnet localhost 25 (you shouldn't need sudo, by the way) and getting the 220 message, type ```
ehlo localhost
``` You probably won't get a prompt, and you might not even see the characters you type. I'm getting this from the page you linked to; I've never messed with mail servers before.
No, haven't run "ehlo localhost"


Just retried with PC rebooted.

$ sudo /etc/init.d/saslauthd start```

Starting SASL Authentication Daemon: /usr/sbin/saslauthd already running.
```

$ telnet localhost 25 (without sudo)```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.example.com ESMTP Postfix (Ubuntu)

(hanging here)

```

Also tried with "sudo telnet localhost 25".  Result was the same, only haning on console screen.


Again;
$ cd /etc/postfix/ssl/
satimis@ubuntu:/etc/postfix/ssl$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.example.com ESMTP Postfix (Ubuntu)
(Still hanging here)

```


B.R.
satimis

---

### Post by bikeboy on 2006-11-22
Try a netstat to see if your server is listening on port 25, that might give you a start on where to look.
```
netstat -l | grep tcp
```

That's a little "L" above, stands for listen.

---

### Post by satimis on 2006-11-22
Hi bikeboy

[quoteTry a netstat to see if your server is listening on port 25, that might give you a start on where to look.
```
netstat -l | grep tcp
```

That's a little "L" above, stands for listen.[/QUOTE]
$ sudo netstat -l | grep tcp```

Password:
tcp        0      0 *:896                   *:*                     LISTEN
tcp        0      0 *:nfs                   *:*                     LISTEN
tcp        0      0 *:708                   *:*                     LISTEN
tcp        0      0 *:714                   *:*                     LISTEN
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN
tcp        0      0 localhost.locald:sunrpc *:*                     LISTEN
tcp        0      0 *:x11                   *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 n219079145039.ne:domain *:*                     LISTEN
tcp        0      0 localhost.locald:domain *:*                     LISTEN
tcp        0      0 *:55702                 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 *:8888                  *:*                     LISTEN
tcp        0      0 localhost.localdo:37848 *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 localhost.localdo:51001 *:*                     LISTEN
tcp        0      0 localhost.localdoma:953 *:*                     LISTEN
tcp6       0      0 *:imaps                 *:*                     LISTEN
tcp6       0      0 *:pop3s                 *:*                     LISTEN
tcp6       0      0 *:44                    *:*                     LISTEN
tcp6       0      0 *:2222                  *:*                     LISTEN
tcp6       0      0 *:pop3                  *:*                     LISTEN
tcp6       0      0 *:imap2                 *:*                     LISTEN
tcp6       0      0 *:x11                   *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:smtp                  *:*                     LISTEN
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN

```

$ sudo netstat -l | grep 25```

unix  2      [ ACC ]     STREAM     LISTENING     13159    /tmp/orbit-satimis/linc-15a9-0-1239b39addd25

```

Tks.


B.R.
satimis

---

### Post by bikeboy on 2006-11-22
Ok the 2nd bottom line where it says *:smtp indicates it's listening on port 25 so that's a start.

Actually looking closer, and trying it on my server, it looks like this
> matt@vickersf:~$ telnet localhost.localdomain 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 vickersf.dyndns.org ESMTP Postfix (Ubuntu)
ehlo localhost
250-vickersf.dyndns.org
250-PIPELINING
250-SIZE 5242880
250-VRFY
250-ETRN
250 8BITMIME

After the 220 it looked like it wasn't responding, but I tried typing thr ehlo localhost and it worked. Does yours let you type?

---

### Post by satimis on 2006-11-22
Hi bikeboy,

> After the 220 it looked like it wasn't responding, but I tried typing thr ehlo localhost and it worked. Does yours let you type?

I got it.  It was wasting for my input.

$ sudo /etc/init.d/saslauthd restart
Password:```

Stopping SASL Authentication Daemon: saslauthd.
Starting SASL Authentication Daemon: saslauthd.

```

$ sudo telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.example.com ESMTP Postfix (Ubuntu)

(it was waiting here.  Then I typed)
ehlo localhost
250-server1.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME

(it was further waiting here.  Then I typed)
quit
221 Bye
Connection closed by foreign host.

```

Tks.


B.R.
satimis

---

### Post by Alpha_omega16 on 2006-11-29
I am having a similar problem only when i user telnet the prompt stops one line early and gives no response to any commands.
```
telnet localhost 25
   Trying 127.0.0.1...
   connected to localhost.
   Escape character is '^]'.

<stops there>
```
tried to ehlo localhost no difference.

I did a netstat -l | grep tcp
```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 ubuntu:domain           *:*                     LISTEN
tcp        0      0 localhost:domain        *:*                     LISTEN
tcp        0      0 *:telnet                *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:imaps                 *:*                     LISTEN
tcp6       0      0 *:pop3s                 *:*                     LISTEN
tcp6       0      0 *:pop3                   *:*                     LISTEN
tcp6       0      0 *:imap2                 *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:smtp                  *:*                     LISTEN

```
Then did sudo netstat -l | grep 25
```
udp6        0        0 *:1025             *:*
```

What would cause it to hang up at that point?
Any help would be great.

Jason

---

### Post by mssever on 2006-11-29
> **Alpha_omega16 said:**
> I am having a similar problem only when i user telnet the prompt stops one line early and gives no response to any commands.
```
telnet localhost 25
   Trying 127.0.0.1...
   connected to localhost.
   Escape character is '^]'.

<stops there>
```tried to ehlo localhost no difference.

I did a netstat -l | grep tcp
```

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 ubuntu:domain           *:*                     LISTEN
tcp        0      0 localhost:domain        *:*                     LISTEN
tcp        0      0 *:telnet                *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp6       0      0 *:imaps                 *:*                     LISTEN
tcp6       0      0 *:pop3s                 *:*                     LISTEN
tcp6       0      0 *:pop3                   *:*                     LISTEN
tcp6       0      0 *:imap2                 *:*                     LISTEN
tcp6       0      0 *:www                   *:*                     LISTEN
tcp6       0      0 *:smtp                  *:*                     LISTEN

```Then did sudo netstat -l | grep 25
```
udp6        0        0 *:1025             *:*
```What would cause it to hang up at that point?
Any help would be great.

Jason

You need to use the --numeric-ports option to netstat to see the actual ports in use: ```
netstat -l --numeric-ports | grep :25
``` I don't know enough about mail servers to be able to tell if it was listening for sure. On the other hand, if nothing was listening, then telnet probably wouldn't be able to connect.

So, check your config. Look for errors in your mail server's logs (and in /var/log/messages and /var/log/daemon if your server doesn't log separately).

---

### Post by Alpha_omega16 on 2006-11-30
Well I found the problem. My main.cf file had a problem in it. Don't know what the problem was but reloaded the default and worked fine

---

### Post by Fíona on 2007-02-21
Pity you don't mention what the problem in your main.cf file was. I'm having a similar problem having followed the ubuntu server guide-email services.
The insight into what you did incorrectly may have been helpful.

---

