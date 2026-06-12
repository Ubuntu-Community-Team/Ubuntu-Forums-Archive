---
title: "Alarming information from netstat?"
date: 2007-11-29
forum: Server Platforms
---

### Post by benne on 2007-11-29
Hi there?

I ran the "netsat -tap" on my private server i didnt like the outcome...

```
benedikt@nepal:~$ netstat -tap
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:6954                  *:*                     LISTEN     -
tcp        0      0 localhost:mysql         *:*                     LISTEN     -
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     -
tcp        0      0 *:www                   *:*                     LISTEN     -
tcp        0      0 *:ftp                   *:*                     LISTEN     -
tcp        0      0 localhost:smtp          *:*                     LISTEN     -
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     -
tcp        0  36088 192.168.1.252:4997      ACCA2D41.ipt.aol.c:6881 ESTABLISHED-
tcp        0      0 192.168.1.252:4876      ool-18b9b4eb.dyn.:23714 ESTABLISHED-
tcp        0      0 192.168.1.252:4368      124-168-130-88.dy:51413 ESTABLISHED-
tcp        0  28310 192.168.1.252:4327      a16115.upc-a.chel:36972 ESTABLISHED-
tcp        0      0 192.168.1.252:3823      d14-69-:afs3-fileserver ESTABLISHED-
tcp6       0      0 *:ssh                   *:*                     LISTEN     -
tcp6       0    148 ::ffff:192.168.1.25:ssh fs2.ir.is:22520         ESTABLISHED-

```

For good measure i did it on another server:

```
bk@draper:~$ netstat -tap
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:40482         *:*                     LISTEN     -
tcp        0      0 localhost:mysql         *:*                     LISTEN     -
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     -
tcp        0      0 localhost:submission    *:*                     LISTEN     -
tcp        0      0 *:10000                 *:*                     LISTEN     -
tcp        0      0 localhost:42835         *:*                     LISTEN     -
tcp        0      0 *:ftp                   *:*                     LISTEN     -
tcp        0      0 localhost:ipp           *:*                     LISTEN     -
tcp        0      0 localhost:smtp          *:*                     LISTEN     -
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     -
tcp        0      0 localhost:40482         localhost:40504         ESTABLISHED-
tcp        0      0 localhost:40504         localhost:40482         ESTABLISHED-
tcp6       0      0 *:www                   *:*                     LISTEN     -
tcp6       0      0 *:ssh                   *:*                     LISTEN     -
tcp6       0      0 draper.2t.is:ssh        udt-bk.2t.local:4967    ESTABLISHED-
tcp6       0      0 draper.2t.is:ssh        udt-bk.2t.local:3013    ESTABLISHED-
tcp6       0      0 draper.2t.is:ssh        udt-bk.2t.local:1238    ESTABLISHED-
tcp6       0      0 draper.2t.is:ssh        udt-bk.2t.local:1235    ESTABLISHED-
```

Is the output on my personal server normal?

---

### Post by MJN on 2007-11-29
It might be better if you're more specific - what didn't you like?
 
Mathew

---

### Post by benne on 2007-11-29
The ports 6954, 4997, 4997, 4876, 23714, 4368, 51413, 4327, 36972 and 3823 are NOT open in my router and therefor i dont like the connections...

---

### Post by benne on 2007-11-29
I ran a nmap scan on the host... looks like ive been hacked.. 

```
# nmap host.org

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-29 13:43 GMT
Interesting ports on *****:
Not shown: 1681 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
100/tcp  open     newacct
209/tcp  open     tam
277/tcp  open     unknown
1418/tcp open     timbuktu-srv2
1424/tcp open     hybrid
1720/tcp filtered H.323/Q.931
2105/tcp open     eklogin
5717/tcp open     prosharenotify
5901/tcp open     vnc-1
6502/tcp open     netop-rc
7003/tcp open     afs3-vlserver
8021/tcp open     ftp-proxy
```

---

### Post by MJN on 2007-11-29
> **benne said:**
> The ports 6954, 4997, 4997, 4876, 23714, 4368, 51413, 4327, 36972 and 3823 are NOT open in my router and therefor i dont like the connections...
 
You need to slow down. Seriously. Jumping to conclusions is not going to do you any favours.
 
You have listed local and remote ports - your router is not involved with forwarding outgoing ports so you can immediately scrap any remote port from that list. Furthermore, some (if not all) of these established connections could well have originated from your machine in which, again, it doesn't matter what ports you've got forwarded in your router. You say these ports aren't 'open' - they are or else they wouldn't be reaching you.
 
Do you run any Torrent software? That connection to :6881 looks like it could be such a connection (although the port number itself, at this level, is not indicative with certainty).
 
Try running **sudo lsof -i :<port>** where <port> is each of your ports as listed by nmap and this will identify the process using them.
 
What services **do** you run?
 
Mathew

---

### Post by benne on 2007-11-29
The only services that are running are ftp, ssh and http. mysql is also running but only on localhost. 

The nmap output is not normal. The port 6881 is forwared for torrent software but it is not running. 

Those ports are not forwared to this machine through the router. I know what ports are forwareded and what port are not fowarded. I did run nmap to scan this host a few weeks ago and then the output was like it was supposed to be. Showed only ssh, http and ftp.

---

### Post by MJN on 2007-11-29
Please run the lsof test like I asked otherwise it's difficult to offer any advice.
 
You are misunderstanding the concept of port forwarding - the connection involving the remote port 6881 in your original netstat output has nothing to do with what ports you have forwarded - such rules apply only to incoming ports. Furthermore, your router will automatically forward the source port (4997) to your machine if it was your machine that initiated the connection (using 4997 as its ephemeral port).
 
Mathew

---

### Post by benne on 2007-11-29
Allright. Thanks for telling me that about the ports.  I just ran nmap from home and it showed up like it should do 

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-29 17:09 GMT
Interesting ports on ***:
Not shown: 1691 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
1080/tcp open     socks
5901/tcp filtered vnc-1
8080/tcp open     http-proxy

Nmap finished: 1 IP address (1 host up) scanned in 9.451 seconds
```

When i did the nmap earlier today i got these services/ports i am NOT running, or at least not aware of running :
```

100/tcp  open     newacct
209/tcp  open     tam
277/tcp  open     unknown
1418/tcp open     timbuktu-srv2
1424/tcp open     hybrid
1720/tcp filtered H.323/Q.931
2105/tcp open     eklogin
5717/tcp open     prosharenotify
5901/tcp open     vnc-1
6502/tcp open     netop-rc
7003/tcp open     afs3-vlserver
8021/tcp open     ftp-proxy

```

this is what lsof came out with for those ports (kind of what i expected)
```

root@think:~# lsof -i :21
root@think:~# lsof -i :100
root@think:~# lsof -i :209
root@think:~# lsof -i :277
root@think:~# lsof -i :1418
root@think:~# lsof -i :1424
root@think:~# lsof -i :1720
root@think:~# lsof -i :2105
root@think:~# lsof -i :5717
root@think:~# lsof -i :5901
root@think:~# lsof -i :6502
root@think:~# lsof -i :7003
root@think:~# lsof -i :8021
root@think:~# 

```

Could i have been false alarm from nmap? Is that possible?

---

### Post by MJN on 2007-11-29
I don't know *exactly* how nmap determines what's running on a port but I suspect in the very basic port scan mode it just looks for open sockets and effectively does a reverse-lookup on the port number against the IANA list. This is all fine and dandy for the 0-1024 range which is well locked down and generally used exclusively by those registered applications but for ports >1024 these may well be registered by 'less common' protocols/applications but they are also often used by other un-registered protocols/applications and indeed every client connection picks one at random for its return path. What I'm trying to say is don't believe everything you read!
 
I was about to suggest running lsof with sudo but I see you were root anyway (tut tut!). Anyway, this is showing there weren't any processes at all (it's a shame you didn't run lsof against port 22 etc to see what a 'positive' result would look like - the sshd process in this case)
 
Mathew
 
P.S. Be very careful running nmap from outside your network - its anyone's guess how some routers respond to packets on random ports and you cannot reliably trust home routers to behave in the 'correct' way (hence you end up with funny results).

---

### Post by benne on 2007-11-29
Yes, i think that is excatly how nmap works... It least it sounds pretty much logical. 

I was going to post a positive test when i saw that the wrong hostname was in the terminal. I had totaally forgotten to ssh to the server (now im feeling really stupid).

here is the output from the server 
```

root@nepal:~# lsof -i :100
root@nepal:~# lsof -i :209
root@nepal:~# lsof -i :277
root@nepal:~# lsof -i :1418
root@nepal:~# lsof -i :1424
root@nepal:~# lsof -i :1720
root@nepal:~# lsof -i :2105
root@nepal:~# lsof -i :5717
root@nepal:~# lsof -i :5901
root@nepal:~# lsof -i :6502
root@nepal:~# lsof -i :7003
root@nepal:~# lsof -i :8021
root@nepal:~# 

```

Note that the hostname is nepal and not thik...

positive test:
```

root@nepal:~# lsof -i :21
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
vsftpd  4663 root    3u  IPv4  13865       TCP *:ftp (LISTEN)

```

But i still dont like the old nmap output, especially not with all those funny names... I have been examining the computer and i cant find any eidence of hacking, so it looks like a false alarm...

---

### Post by MJN on 2007-11-29
You've lost me now - I'm confused as to where you are, where/what your server is, where you have and haven't done the nmap.

But, yes, I think it was indeed a false alarm!

Mathew

---

