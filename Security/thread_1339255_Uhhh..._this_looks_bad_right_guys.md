---
title: "Uhhh... this looks bad right guys?"
date: 2009-11-27
forum: Security
---

### Post by User0123 on 2009-11-27
[IMG]http://i48.tinypic.com/9ux4s7.jpg[/IMG]

The MSN protocol and xchat are fine, those are intended, its the rest I dont understand, particularly worrying is telnet and ftp as I don't need nor want anyone connecting to machine using those protocols, the other ports could be in use by rootkits I guess?

Thanks in advance to anyone who can shed any light on this issue.

---

### Post by EJeanmaire on 2009-11-27
> **User0123 said:**
> [IMG]http://i48.tinypic.com/9ux4s7.jpg[/IMG]

The MSN protocol and xchat are fine, those are intended, its the rest I dont understand, particularly worrying is telnet and ftp as I don't need nor want anyone connecting to machine using those protocols, the other ports could be in use by rootkits I guess?

Thanks in advance to anyone who can shed any light on this issue.

You appear to be doing the FTP and Telneting, not vice-versa.

---

### Post by Sarmacid on 2009-11-27
The ftp ip seems to be related to MSN, however the telnet one doesn't```
$ host 65.54.172.193
193.172.54.65.in-addr.arpa domain name pointer by2msg2020408.gateway.edge.messenger.live.com.
193.172.54.65.in-addr.arpa domain name pointer by2msg2020408.mixer.edge.messenger.live.com.

$ host 95.105.156.150
150.156.105.95.in-addr.arpa domain name pointer dial-95-105-156-150-orange.orange.sk.

```

---

### Post by EJeanmaire on 2009-11-27
> **Sarmacid said:**
> The ftp ip seems to be related to MSN, however the telnet one doesn't```
$ host 65.54.172.193
193.172.54.65.in-addr.arpa domain name pointer by2msg2020408.gateway.edge.messenger.live.com.
193.172.54.65.in-addr.arpa domain name pointer by2msg2020408.mixer.edge.messenger.live.com.

$ host 95.105.156.150
150.156.105.95.in-addr.arpa domain name pointer dial-95-105-156-150-orange.orange.sk.

```

Look again, the FTP and Telnet are both to the 95.X.X.X IP address; not the MSN one.

---

### Post by User0123 on 2009-11-27
Yeah its the 95.X.X.X IP that is worrying me, and if the connections are me connecting to telnet and FTP at 95.X.X.X, why is it when I open a shell and try to telnet that IP or even when I nmap it, nothing is open?

This all seems very strange to me.

---

### Post by EJeanmaire on 2009-11-27
> **User0123 said:**
> Yeah its the 95.X.X.X IP that is worrying me, and if the connections are me connecting to telnet and FTP at 95.X.X.X, why is it when I open a shell and try to telnet that IP or even when I nmap it, nothing is open?

This all seems very strange to me.

Show the output of the following commands:

netstat -a -p --inet

finger

sudo lastb

---

### Post by sgosnell on 2009-11-27
Are you sure that isn't **your** IP address?  It's an Orange Slovensko ISP, in Bratislava.

---

### Post by User0123 on 2009-11-27
> **EJeanmaire said:**
> Show the output of the following commands:

netstat -a -p --inet

finger

sudo lastb

```
netstat -a -p --inet
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      1626/cupsd      
tcp        0      0 localhost:mysql         *:*                     LISTEN      16593/mysqld    
tcp        0      0 192.168.0.4:43821       gv-in-f101.1e100.ne:www ESTABLISHED 21300/firefox   
udp        0      0 *:mdns                  *:*                                 28648/avahi-daemon:
udp        0      0 *:51508                 *:*                                 28648/avahi-daemon:
udp        0      0 *:bootpc                *:*                                 891/dhclient   

finger
me        me         tty7       3d  Nov 24 19:49 (:0)
me        me         pts/0    7:30  Nov 27 15:11 (:0.0)
me        me         pts/1    5:44  Nov 27 16:56 (:0.0)
me        me         pts/2       5  Nov 27 22:35 (:0.0)
me        me         pts/3          Nov 27 22:37 (:0.0)

sudo lastb
me       tty7         :0               Sun Nov 22 15:35 - 15:35  (00:00)    
UNKNOWN  tty1                          Sat Nov 21 20:14 - 20:14  (00:00)    
me       tty7         :0               Tue Nov 17 16:29 - 16:29  (00:00)    
UNKNOWN  tty2                          Sat Nov 14 23:53 - 23:53  (00:00)    
UNKNOWN  tty2                          Sat Nov 14 23:52 - 23:52  (00:00)    
me       tty7         :0               Fri Nov 13 00:43 - 00:43  (00:00)    
```

And yes, I'm sure that isn't my IP, I'm nowhere near that.

---

### Post by User0123 on 2009-11-28
Anyone make sense of this?

---

### Post by rookcifer on 2009-11-28
I don't see anything suspicious in your first netstat output, so try this:

```
sudo netstat -atpvnl
```

---

### Post by User0123 on 2009-11-28
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:61876           0.0.0.0:*               LISTEN      4194/wish8.5    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2130/cupsd      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1669/mysqld     
tcp        0      0 192.168.0.4:50408       207.46.125.30:1863      CLOSE_WAIT  4194/wish8.5    
tcp        0      0 192.168.0.4:44450       66.102.9.113:80         ESTABLISHED 2909/firefox    
tcp        0      0 192.168.0.4:44624       207.46.124.201:1863     ESTABLISHED 4194/wish8.5    
tcp        0      0 192.168.0.4:48416       208.81.191.111:80       ESTABLISHED 2909/firefox    
tcp6       0      0 ::1:631                 :::*                    LISTEN      2130/cupsd      
tcp6       0      0 :::80                   :::*                    LISTEN      2237/apache2  
```

Nothing that seems suspicious here to me either =/

---

### Post by koenn on 2009-11-29
Those "Active Connections" in that firewall program you're using should be identical to the "Established" connections in netstat.

Have you tried running both (netstat + firewall GUI) at the same time ? 
I'll trust netstat before anything else, so if there's a difference, 
- the firewall GUI has a bug ?
- the firewall program sets up these connections ? <= that would be interesting :)
- ...

---

### Post by User0123 on 2009-11-29
Yeah I've rebooted since detecting these connections and they haven't re-established.

---

### Post by EJeanmaire on 2009-11-30
> **User0123 said:**
> Yeah I've rebooted since detecting these connections and they haven't re-established.

My guess is you made a few one-time connections (you connected to an FTP server, not someone connecting to you via FTP.)  If you were downloading a file though firefox, it may have very well been off an ftp site, which would use the FTP port (21).  I don;t think at this point you should worry.

---

### Post by User0123 on 2009-11-30
I'm pretty sure I didn't connect to any FTP server and when I do scan that IP nothing is shown as open anyway.


My only guess is that it could be related to transmission, the torrent client, that's the only software I have used for any file transfers, although I know it doesn't use FTP.

Oh well I guess I should just forget about it for now.

---

### Post by EJeanmaire on 2009-11-30
> **User0123 said:**
> I'm pretty sure I didn't connect to any FTP server and when I do scan that IP nothing is shown as open anyway.


My only guess is that it could be related to transmission, the torrent client, that's the only software I have used for any file transfers, although I know it doesn't use FTP.

Oh well I guess I should just forget about it for now.

You might have downloaded the actual torrent file from an FTP location, the download dialog box in firefox looks just like a normal http download.

---

### Post by User0123 on 2009-11-30
I'm normally the uber paranoid type, I tend to check links carefully and I would have noticed if it was ftp://

Oh well I guess I'll just keep being paranoid but try to worry less :P

---

