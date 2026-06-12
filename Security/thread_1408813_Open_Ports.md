---
title: "Open Ports"
date: 2010-02-16
forum: Security
---

### Post by tomehb on 2010-02-16
Hi,

Just wondering if I infact need all of these ports open on my server... All I'm using it for is https, ftp(tls), and ssh... 

if so how do I go about disabling them and what are they for...


PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
111/tcp  filtered rpcbind
135/tcp  filtered msrpc
443/tcp  open     https
445/tcp  filtered microsoft-ds
554/tcp  filtered rtsp
1720/tcp filtered H.323/Q.931
2000/tcp filtered callbook
5000/tcp filtered upnp
5060/tcp filtered sip

---

### Post by lisati on 2010-02-16
The [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") website might be of some help testing and explaining things.

---

### Post by cariboo on 2010-02-17
> **tomehb said:**
> Hi,

Just wondering if I infact need all of these ports open on my server... All I'm using it for is https, ftp(tls), and ssh... 

if so how do I go about disabling them and what are they for...


PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
111/tcp  filtered rpcbind
135/tcp  filtered msrpc
443/tcp  open     https
445/tcp  filtered microsoft-ds
554/tcp  filtered rtsp
1720/tcp filtered H.323/Q.931
2000/tcp filtered callbook
5000/tcp filtered upnp
5060/tcp filtered sip

Turn off the services you don't need. I see you have NFS, Samba, some sort of multimedia streaming and upnp servers running. I would also suggest getting rid of the ftp server, and use sftp instead. The callbook/sip looks like it could be VOIP

---

### Post by cdenley on 2010-02-17
The only ports you have open are http, https, ftp, and ssh. If you want to close http, edit /etc/apache2/ports.conf to stop apache from listening on port 80.

---

### Post by tomehb on 2010-02-17
Ah yeah, I thought that filtered meant i.e it was being filtered for certain address ranges or somthing... but infact... filtered  means that a firewall, filter, or other network obstacle is blocking the port so that Nmap cannot tell whether it is open or closed......  so did a netsat which is what i should of done at the start! 

```

administrator@tomehb:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 *:https                 *:*                     LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
udp        0      0 localhost:snmp          *:*
udp        0      0 *:bootpc                *:*
udp        0      0 93.174.138.201:ntp      *:*
udp        0      0 localhost:ntp           *:*
udp        0      0 *:ntp                   *:*
udp6       0      0 fe80::250:56ff:fe9a:ntp [::]:*
udp6       0      0 ip6-localhost:ntp       [::]:*
udp6       0      0 [::]:ntp                [::]:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     11801    /var/run/fail2ban/fail2ban.sock
unix  2      [ ACC ]     STREAM     LISTENING     11453    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     11248    /dev/log

```

---

### Post by tomehb on 2010-02-17
> **cariboo907 said:**
> Turn off the services you don't need. I see you have NFS, Samba, some sort of multimedia streaming and upnp servers running. I would also suggest getting rid of the ftp server, and use sftp instead. The callbook/sip looks like it could be VOIP


Currently using FTP with TLS, would you still suggest sftp? if so what sftp server would you suggest :)

---

### Post by cdenley on 2010-02-17
I believe filtered means the connection attempt was rejected (not dropped or accepted). An SFTP server would be openssh-server, which I think you are already using. I think FTP over SSL is fine, though, if you require encryption.

---

### Post by tomehb on 2010-02-17
> **cdenley said:**
> I believe filtered means the connection attempt was rejected (not dropped or accepted). An SFTP server would be openssh-server, which I think you are already using. I think FTP over SSL is fine, though, if you require encryption.

Cheers, I guess that will be all.. Just updated my post (above) :) about the filtered ports.. i was panicking for nothing... Thanks for the help though :)

Also need a little guidance with [http://ubuntuforums.org/showthread.php?t=1408798](http://ubuntuforums.org/showthread.php?t=1408798) ... :)

---

