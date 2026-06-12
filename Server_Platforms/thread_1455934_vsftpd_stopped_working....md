---
title: "vsftpd stopped working..."
date: 2010-04-16
forum: Server Platforms
---

### Post by blackandwhitepandabear on 2010-04-16
Hi, I had vsftpd running fine (anonymous download only) on my Ubuntu 8.04 LTS machine and then after some point (after rebooting) this morning I cannot connect to this machine from a different computer. On this Ubuntu, I can type [ftp://servername](ftp://servername) in firefox and see my ftp directory but from my other computer, the connection times out. Port 21 is open; I can connect to this computer from the other one via ssh so it's not a network issue. I've tried sudo /etc/init.d/vsftp start (and restart) but to no avail. Any suggestions on what I might try next? Thanks all!

---

### Post by cdenley on 2010-04-16
From one computer it works, the other it doesn't? Can you post your server's IP? Can you connect on port 21?
```

nc -z -v -w 5 myserver 21

```
You aren't using SSL, right? Passive or active FTP?

---

### Post by blackandwhitepandabear on 2010-04-16
Thank you for your response!

```
$ nc -z -v -w 5 myserver 21

```
hangs but 
```
$ nc -z -v -w 5 myserver 22
Connection to myserver 22 port [tcp/ssh] succeeded!

```
works.

Not using SSL, but not sure whether passive or active - whatever the default for vsftpd? The vsftpd.conf file doesn't appear to give any indication. That could be the problem?

---

### Post by cdenley on 2010-04-16
> **blackandwhitepandabear said:**
> Thank you for your response!

```
$ nc -z -v -w 5 myserver 21

```
hangs but 
```
$ nc -z -v -w 5 myserver 22
Connection to myserver 22 port [tcp/ssh] succeeded!

```
works.

Not using SSL, but not sure whether passive or active - whatever the default for vsftpd? The vsftpd.conf file doesn't appear to give any indication. That could be the problem?

vsftpd supports active and passive by default. It is up to the client to choose. However, if you can't connect to port 21, then both will fail. You said you can connect to your FTP from somewhere else, though?

Run this on the server
```

sudo netstat -tlnp

```

By the way, the nc (netcat) command I gave won't "hang", it will wait 5 seconds for a response. Did it time out after 5 seconds?

---

### Post by blackandwhitepandabear on 2010-04-16
Oh, you're right, but it took much longer than 5 seconds (though I guess that's what -w 5 is for...
```

nc: connect to myserver port 21 (tcp) failed: Operation timed out

```

From the netstat command:
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3690            0.0.0.0:*               LISTEN      5913/svnserve   
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      8139/vsftpd     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5876/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      5823/sshd

```

I can only ftp to the Ubuntu machine running the ftp server using the server itself... but the ftp functionality seems to be working since I'm using an ftp client to connect to it rather than just looking at the directory contents in terminal. Come to think of it, the svn server isn't connecting either... but I can connect to this same machine remotely using ssh, which is puzzling...

---

### Post by cdenley on 2010-04-17
> **blackandwhitepandabear said:**
> Oh, you're right, but it took much longer than 5 seconds (though I guess that's what -w 5 is for...
```

nc: connect to myserver port 21 (tcp) failed: Operation timed out

```

From the netstat command:
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3690            0.0.0.0:*               LISTEN      5913/svnserve   
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      8139/vsftpd     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5876/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      5823/sshd

```

I can only ftp to the Ubuntu machine running the ftp server using the server itself... but the ftp functionality seems to be working since I'm using an ftp client to connect to it rather than just looking at the directory contents in terminal. Come to think of it, the svn server isn't connecting either... but I can connect to this same machine remotely using ssh, which is puzzling...

Well, you're server is listening for connections, so either your connection attempts are being filtered by a firewall, or they aren't being routed properly.

---

### Post by blackandwhitepandabear on 2010-04-17
Hmm... Thanks for your help! I'll try to mess around a bit more (turn off all firewalls, etc).

---

