---
title: "ProFtpd...Unbindable port 21"
date: 2008-06-08
forum: Server Platforms
---

### Post by jbcurtin on 2008-06-08
Hey all,

  I am having an issue, I am running the amd64 8.04 server version of ubuntu.

```
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at main.c:2257
Jun 08 14:06:38 mandy proftpd[4611] mandy: deleting existing scoreboard '/var/ruu[8;1Hn/proftpd/proftpd.scoreboard'
Jun 08 14:06:38 mandy proftpd[4611] mandy: opening scoreboard '/var/run/proftpd//[10;1Hproftpd.scoreboard'
Jun 08 14:06:38 mandy proftpd[4611] mandy: RELINQUISH PRIVS at main.c:2283
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at mod_ctrls_admin.c:1092
Jun 08 14:06:38 mandy proftpd[4611] mandy: opening scoreboard '/var/run/proftpd//[14;1Hproftpd.scoreboard'
Jun 08 14:06:38 mandy proftpd[4611] mandy: RELINQUISH PRIVS at mod_ctrls_admin.cc[16;1H:1094
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at inet.c:343
Jun 08 14:06:38 mandy proftpd[4611] mandy: RELINQUISH PRIVS at inet.c:387
**Jun 08 14:06:38 mandy proftpd[4611] mandy: Failed binding to ::, port 21: Address[20;1Hs already in use**
Jun 08 14:06:38 mandy proftpd[4611] mandy: Check the ServerType directive to enss[22;1Hure you are configured correctly.
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at mod_delay.c:1095[1;1H[?12l[?25h[?25l[27m[m[H[2J[1;1HJun 08 14:06:38 mandy proftpd[4611] mandy: Check the ServerType directive to enss[2;1Hure you are configured correctly.
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at mod_delay.c:1095
Jun 08 14:06:38 mandy proftpd[4611] mandy: RELINQUISH PRIVS at mod_delay.c:1097
Jun 08 14:06:38 mandy proftpd[4611] mandy: ROOT PRIVS at mod_ban.c:1582
Jun 08 14:06:38 mandy proftpd[4611] mandy: RELINQUISH PRIVS at mod_ban.c:1584
Jun 08 14:06:38 mandy proftpd[4611] mandy: mod_ban/0.5.1: error removing shm -1::[8;1H No such file or directory
```

The odd thing is:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      4436/smbd       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      4436/smbd       
**tcp6       0      0 :::21                   :::*                    LISTEN      4477/proftpd: (acce**
tcp6       0      0 :::22                   :::*                    LISTEN      4416/sshd       
tcp6       0      0 192.168.0.100:22        192.168.0.115:2437      ESTABLISHED 4673/0   
```

I am somewhat of a newb, so bear with me on this one. Any idea though? Its starting to wear on me.

Thanks in advance.

---

### Post by jbcurtin on 2008-06-08
So I have been looking into the error message, and it seems that it is not just for proftpd.

Here is the problem that I think is being created, the server is active and listening for connections, however when it hears a connection it is accepting it and trying to bind the port yet again. Any ideas on this one fokes? 

As of right now, I think I am going to remove it and use a rpm from a later date.

---

### Post by twgray on 2008-06-08
I'm also a big newb with the server edition...how did you get the second listing showing all connections?

---

### Post by Prospero2006 on 2008-06-08
do this before starting proftpd
```

sudo apt-get install nmap

```

then
```

nmap localhost

```

nmap shows what ports are listening on your machine. If it shows port 21 before starting proftpd, something else is active there.

---

### Post by jbcurtin on 2008-06-08
```
Not shown: 1710 filtered ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 8.934 seconds
```

Which suggests that the ftp is already running, then trys to run yet again. Not sure what to do from this point, how would i configure proftpd so that it wouldn't try to re-bind?



twgray
```
ps -axuw
```

---

### Post by jombeewoof on 2008-06-08
> **jbcurtin said:**
> 
how would i configure proftpd so that it wouldn't try to re-bind?


wouldn't 
```

sudo /etc/init.d/proftpd restart

```

do what you want?

---

### Post by jbcurtin on 2008-06-08
that was the second thing i tried.

---

### Post by Prospero2006 on 2008-06-09
Let's find out what is running.
Try this
ps -ax | grep ftp

---

### Post by jbcurtin on 2008-06-10
I ended up fixing it...but i am not going to share why because...well its pretty embarrassing...

---

### Post by nix4me on 2008-06-10
Share anyway.  I guarantee someone will do the same thing in the future and this thread might help them.  No one will criticize.

---

### Post by Pjukern on 2008-10-18
I have the same problem now, something is listening on port 21, but Im unable to figure out what.

proftpd log:
```

Oct 17 19:59:09 sirius proftpd[1696] sirius: Failed binding to ::, port 21: Address already in use
Oct 17 19:59:09 sirius proftpd[1696] sirius: Check the ServerType directive to ensure you are configured$

```

nmap:
```

PORT      STATE SERVICE     VERSION
21/tcp    open  tcpwrapped

```
netstat:
```
espen@sirius:/etc$ netstat -a -e --numeric-ports | grep :21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      root       8593050

```

---

### Post by lykwydchykyn on 2008-10-18
Can you share your config file? /etc/proftpd/proftpd.conf, I think.  It may just be /etc/proftpd.conf.

Also, if you run:
```

invoke-rc.d proftpd stop

```
Is there still a service bound to port 21?

---

### Post by dvirdc on 2009-09-01
well... whats next? 
did you solve it?
i'm having the same problem and i cant seem to find the solution.
root's got the 21 opened and proftpd can't use it.

what should i do?

much thx

---

### Post by kinglear333 on 2009-12-25
> **jbcurtin said:**
> I ended up fixing it...but i am not going to share why because...well its pretty embarrassing...

Sorry if this goes against forum etiquette but people like jbcurtin are a disgrace to the community.

I figured out why it doesn't bind to port 21. Because ProFTPd was probably installed as xinetd service before and later switched to standalone. What hasn't changed, however, is xinet still reserving ProFTPd from...

To fix, just do this:

1) Open up the xinet config:
# sudo nano -w /etc/inetd.conf

2) Comment the FTP line

3) Save file

4) Restart ProFTPD:
# sudo /etc/init.d/proftpd restart


Hope this helps the next person!

---

### Post by rezyn8 on 2010-05-04
I was having the same issue after initially installing ProFTPd under xinetd. The unfortunate thing was that when commenting out the line in inetd.conf and restarting proftpd, the port was not being released to ProFTPd as expected.

In order to fix this I had to find what application/pid was using port 21 and kill it so that ProFTPd could then use it.

```
# netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      3841/inetd

# kill 3841

# netstat -a -e --numeric-ports | grep :21

# /etc/init.d/proftpd start
 * Starting ftp server proftpd [ OK ]

# netstat -a -e --numeric-ports | grep :21
tcp6       0      0 :::21                   :::*                    LISTEN      proftpd    406014
```

---

