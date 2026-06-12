---
title: "Ubuntu &amp; Ports"
date: 2010-07-23
forum: Server Platforms
---

### Post by ash369 on 2010-07-23
I'm trying to run a game server on the dedicated server i recently purchased. I have downloaded the server files and started the game server on port 27015 but it does not appear on the internet. I cannot connect to it.

How do i open the port so that i can find it on the game server list?

---

### Post by arrrghhh on 2010-07-23
2 Choices (since you're not running a DE)

[UFW](https://help.ubuntu.com/community/UFW) (much easier) or [Iptables](https://help.ubuntu.com/community/IptablesHowTo) (very powerful, but somewhat difficult to use...)

Pick your poison.  I don't do anything fancy, so I just stick with UFW.  For what you describe, UFW would be fine.

After a hole is punched there, you need to open the port on your router/hardware firewall.

---

### Post by ash369 on 2010-07-23
I don't understand this. I'm on a dedicated server so shouldn't the ports already be opened? The firewall on the server by default is off, i think. So why can't i see the server on the game server list? Weird ...

---

### Post by cdenley on 2010-07-23
What is a "game server list"? Are you sure you only need an accessible server in order to be added to that list instantly? Can you post your IP so we can see if it is accepting connections on that TCP port? The server is connected directly to the internet with your publicly accessible IP address assigned to a network interface? No router or LAN?

---

### Post by arrrghhh on 2010-07-23
Well... there is no firewall enabled on Ubuntu by default, you are correct.  There also are not any open listening ports by default as well.  If you're running a service that listens on a port, you should probably setup a firewall.  Certainly not required... but I like having control over my system.

As for the other piece, cdenley hit the nail on the head.  Are you on a router/LAN or do you just have your server connected directly to the internet?

---

### Post by ash369 on 2010-07-23
Really i'm not sure. I bought the server, they set it up and gave me access. Thats it. I have no idea whats installed or anything.

These are the IP's which are currently set-up on the server

```
88.208.222.129
88.208.222.130
```

Private LAN is disabled.

Pinging the server works, so its on the internet.

---

### Post by cdenley on 2010-07-23
There doesn't appear to be anything listening on TCP port 27015. Your web server, FTP server, and SSH server seem to be working fine, so I don't think it is a networking problem.

This command will list all listening processes.
```

sudo netstat -tulnp

```

---

### Post by arrrghhh on 2010-07-23
Oh so this is a hosted setup?  I wrongly assumed you were providing the server internet access...

Well then that changes things.  You may want to talk to your provider if that's the case...  You could try running a site like shieldsup.com on the machine to see what ports are open/listening/stealth'd.

Forget that last part, we can probe the address for ya.  cdenley has been kind enough to do so :D

---

### Post by ash369 on 2010-07-23
Thanks guys for your help :)

Here is the output

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1930/portmap
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      23620/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      21407/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      13735/sshd
tcp        0      0 0.0.0.0:45946           0.0.0.0:*               LISTEN      1948/rpc.statd
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      23620/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      13735/sshd
udp        0      0 0.0.0.0:35520           0.0.0.0:*                           1948/rpc.statd
udp        0      0 0.0.0.0:852             0.0.0.0:*                           1948/rpc.statd
udp        0      0 0.0.0.0:111             0.0.0.0:*                           1930/portmap
udp        0      0 88.208.222.130:123      0.0.0.0:*                           13929/ntpd
udp        0      0 88.208.222.129:123      0.0.0.0:*                           13929/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           13929/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           13929/ntpd
udp6       0      0 fe80::219:99ff:fe7f:123 :::*                                13929/ntpd
udp6       0      0 ::1:123                 :::*                                13929/ntpd
udp6       0      0 :::123                  :::*                                13929/ntpd
```

---

### Post by cdenley on 2010-07-23
As I suspected, nothing listening on port 27015. Are you sure your game server is running?

---

### Post by ash369 on 2010-07-23
Really weird but i just started it and its working now! :O

---

### Post by arrrghhh on 2010-07-23
> **ash369 said:**
> Really weird but i just started it and its working now! :O

Glad to hear it.  Please mark this thread [SOLVED] using the thread tools drop-down menu!

---

### Post by ash369 on 2010-07-23
Thanks a bunch! :)

---

