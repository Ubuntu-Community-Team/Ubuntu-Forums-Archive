---
title: "update date/time of client"
date: 2011-05-08
forum: Server Platforms
---

### Post by mahmoodn on 2011-05-08
Hi,
How can a client update its date and time with the local server?

---

### Post by Lars Noodén on 2011-05-08
Do you mean by using NTPd or OpenNTP to synchronize the system clock with a time server?

---

### Post by mahmoodn on 2011-05-08
I don't know. the server has two NIC. one is connected to internet and the other is connected to a local switch with 192.168.X.Y address. The clients hence are connected to the local switch. So I want the clients to be sync with server. The server will auto update itself with internet.

---

### Post by Lars Noodén on 2011-05-09
Set up [NTP](http://packages.ubuntu.com/natty/ntp) or [OpenNTP](http://packages.ubuntu.com/natty/openntpd) on the server.  Have it both sync with the time servers in the NTP pool and serve time to your subnet.  Put NTP or OpenNTP on the clients and point them to the server.

---

### Post by Grenage on 2011-05-09
Doesn't Ubuntu automatically use NTP to set its time?  I configure all of mine, so I can't recall the default.

Either way, it is simple to modify the ntp.conf file, you just need to replace the client's existing NTP server address with your internal server's address:

```
gksu gedit /etc/ntp.conf
```

---

### Post by mahmoodn on 2011-05-09
```
mahmood@client:~$ cat /etc/ntp.conf
....
# You do need to talk to an NTP server or two (or three).
#server ntp.ubuntu.com
192.168.1.1
....

```
However ```
mahmood@client:~$ sudo ntpdate
 2 Oct 18:01:29 ntpdate[13656]: no servers can be used, exiting

```

---

### Post by Lars Noodén on 2011-05-09
[ntpdate](http://manpages.ubuntu.com/manpages/natty/en/man8/ntpdate.8.html) needs the address of a NTP server.

e.g.:
```

sudo ntpdate 0.pool.debian.ntp.org

```
or
```

sudo ntpdate ntp.ubuntu.com
```

---

### Post by Grenage on 2011-05-09
> **mahmoodn said:**
> ```
mahmood@client:~$ cat /etc/ntp.conf
....
# You do need to talk to an NTP server or two (or three).
#server ntp.ubuntu.com
192.168.1.1
....

```
However ```
mahmood@client:~$ sudo ntpdate
 2 Oct 18:01:29 ntpdate[13656]: no servers can be used, exiting

```

Try:

```
ntpq -pn
```

ntpdate is where you manually specify a server.

---

### Post by mahmoodn on 2011-05-09
> **Lars Noodén said:**
> [ntpdate](http://manpages.ubuntu.com/manpages/natty/en/man8/ntpdate.8.html) needs the address of a NTP server.

e.g.:
```

sudo ntpdate 0.pool.debian.ntp.org

```
or
```

sudo ntpdate ntp.ubuntu.com
```

the client is not connected to internet:
```
mahmood@client:~$ sudo ntpdate 0.pool.debian.ntp.org
Name server cannot be used, exiting 2 Oct 18:18:04 ntpdate[13667]: name server cannot be used, reason: Temporary failure in name resolution

```

> **Grenage said:**
> Try:

```
ntpq -pn
```

ntpdate is where you manually specify a server.
```
mahmood@client:~$ ntpq -pn
ntpq: read: Connection refused
mahmood@client:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.656 ms
^C
--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.656/0.656/0.656/0.000 ms
mahmood@client:~$

```

---

### Post by Lars Noodén on 2011-05-09
> **mahmoodn said:**
> the client is not connected to internet:


Then set up your server first so that it is also serving up NTP.  Then point the client at the server:

```

sudo ntpdate 192.168.1.1 

```

---

### Post by mahmoodn on 2011-05-09
thanks
```
mahmood@client:~$ sudo ntpdate 192.168.1.1
 9 May 10:54:00 ntpdate[13679]: step time server 192.168.1.1 offset 18894618.920747 sec
mahmood@client:~$ date
Mon May  9 10:54:06 UTC 2011

```
Is it automatically then? or I have to manually run that command?

---

### Post by Lars Noodén on 2011-05-09
**ntpdate** has to be run manually, and **ntpd** runs automatically.  

If you have **ntpd** running then **ntpdate** is not needed.

---

### Post by mahmoodn on 2011-05-09
How can I check ntpd is running on client?

---

### Post by Lars Noodén on 2011-05-09
> **mahmoodn said:**
> How can I check ntpd is running on client?

```

pgrep -lx ntpd

```

or 
```

ps auwx | grep ntpd

```

or 
```

/etc/init.d/ntp status

```

---

### Post by mahmoodn on 2011-05-09
```
mahmood@client:~$ sudo dpkg -l | grep "ntp"
ii  ntp                              1:4.2.4p8+dfsg-1ubuntu2.1 Network Time Protocol daemon and utility pro
ii  ntpdate                          1:4.2.4p8+dfsg-1ubuntu2.1 client for setting system time from NTP serv
mahmood@client:~$ /etc/init.d/ntpd status
-bash: /etc/init.d/ntpd: No such file or directory
mahmood@client:~$

```

---

### Post by Lars Noodén on 2011-05-09
dpkg tells you what is installed.  Odds are that if it is installed, then it is also running automatically.

ps, pgrep, and the init.d script tell you explicitly what is running.

(PS. I misspelled ntp in the previous example. It's now corrected.)

---

### Post by mahmoodn on 2011-05-09
as I posted, /etc/init.d/ntpd says no such file.
How can I put it there?

---

### Post by Grenage on 2011-05-09
```
sudo apt-get install ntp
```

Make sure it's actually installed.

---

### Post by Lars Noodén on 2011-05-09
> **mahmoodn said:**
> as I posted, /etc/init.d/ntpd says no such file.
How can I put it there?

I should have put ntp without the extra 'd'
```

/etc/init.d/**ntp** status

```

---

### Post by mahmoodn on 2011-05-09
```

mahmood@client:~$ /etc/init.d/ntp status
 * NTP server is not running
mahmood@client:~$ sudo /etc/init.d/ntp start
 * Starting NTP server ntpd                                                    [ OK ]
mahmood@client:~$

```
Is that all?

---

### Post by Lars Noodén on 2011-05-09
> **mahmoodn said:**
> ```

mahmood@client:~$ /etc/init.d/ntp status
 * NTP server is not running
mahmood@client:~$ sudo /etc/init.d/ntp start
 * Starting NTP server ntpd                                                    [ OK ]
mahmood@client:~$

```
Is that all?

Yes -- if it is pointed at your server.

/etc/ntp.conf should have a line pointing to your own NTP server.

---

### Post by mahmoodn on 2011-05-09
thanks a lot :)

---

