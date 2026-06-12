---
title: "Unusual port (8081) is open?"
date: 2010-07-03
forum: Security
---

### Post by Sepiraph on 2010-07-03
I did a port scan on my own network and found the following port open on my Ubuntu:

PORT      STATE SERVICE
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
2000/tcp  open  cisco-sccp
2001/tcp  open  dc
2004/tcp  open  mailbox
3000/tcp  open  ppp
5900/tcp  open  vnc
7200/tcp  open  fodms
7201/tcp  open  dlip
8080/tcp  open  http-proxy
8081/tcp  open  blackice-icecap
24800/tcp open  unknown


Particularly, I have no idea what/why the following is open:

8081/tcp  open  blackice-icecap

Quick google search didn't reveal anything particularly useful, anyone else want to chime in?

---

### Post by CharlesA on 2010-07-03
How did you scan the host? Run nmap on the localhost or from another machine?

Try running this from a terminal and posting the output:

```
sudo netstat -tulnp
```

---

### Post by unspawn on 2010-07-03
> **Sepiraph said:**
> I have no idea what/why the following is open:
8081/tcp  open  blackice-icecap
On a GNU/Linux system 'getent services 8081' (the system-wide static service database /etc/services) may return "tproxy 8081/tcp". The equivalent Nmap uses is its own static service database "nmap-services". As you can see arbitrary-named non-IANA port assignments can cause confusion and since they're static listings they don't say anything about the actual process. Running 'netstat|grep' is kind of old-school, 'lsof -Pwni :8081' or 'fuser -vn tcp 8081' more efficient.

---

### Post by Sepiraph on 2010-07-05
> **CharlesA said:**
> How did you scan the host? Run nmap on the localhost or from another machine?

I ran nmap on the localhost (actually I specify the local subnet range).

> Try running this from a terminal and posting the output:

```
sudo netstat -tulnp
```

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3307            0.0.0.0:*               LISTEN      1642/mysqld.bin 
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      1952/.python.bin
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN      1989/.python.bin
tcp        0      0 0.0.0.0:8789            0.0.0.0:*               LISTEN      1989/.python.bin
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1554/cupsd      
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      1457/ntop       
tcp        0      0 0.0.0.0:24800           0.0.0.0:*               LISTEN      1757/synergys   
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               LISTEN      1920/.python.bin
tcp6       0      0 :::139                  :::*                    LISTEN      1024/smbd       
tcp6       0      0 :::5900                 :::*                    LISTEN      1744/vino-server
tcp6       0      0 ::1:631                 :::*                    LISTEN      1554/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      1024/smbd       
udp        0      0 0.0.0.0:162             0.0.0.0:*                           2275/.python.bin
udp        0      0 0.0.0.0:56413           0.0.0.0:*                           1065/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1065/avahi-daemon: 
udp        0      0 0.0.0.0:514             0.0.0.0:*                           2163/.python.bin
udp        0      0 192.168.1.3:137         0.0.0.0:*                           1943/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1943/nmbd       
udp        0      0 192.168.1.3:138         0.0.0.0:*                           1943/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1943/nmbd
```    

Actually I just figured out that the 8081 port is opened because I installed zenoss (a NMS) and it uses 8081 as a server port.

---

### Post by stderr on 2010-07-05
For future reference, when you find an open port that looks dodgy, I have found running the script nikto.pl from [here]("http://cirt.net/nikto2") to provide invaluable information:

```
./nikto.pl -host localhost -port <PORT_NUMBER>
```

---

