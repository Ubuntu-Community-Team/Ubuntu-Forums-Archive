---
title: "[SOLVED] Connection Refused Aptitude"
date: 2007-09-03
forum: Server Platforms
---

### Post by batrick on 2007-09-03
I get this error when I run

```
batrick@waterdeep:~$ sudo apt-get update
Password:
Err http://security.ubuntu.com feisty-security Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/main Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/restricted Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/universe Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com feisty-security/multiverse Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/main Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/restricted Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/universe Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-backports Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I think it has something to do with being unable to open a socket on 8080 but I can't figure it out. I've messed with the iptables a little and didn't accomplish anything.

Because I suspect this will be asked for, here is the output of

```
cat /etc/apt/sources.list
batrick@waterdeep:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

#deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

Can someone help please?

---

### Post by p_quarles on 2007-09-03
Post the output of the following commands:
```
ifconfig -a
```and
```
ping -c5 www.google.com
```The message you got indicates that there's a connectivity problem. (127.0.0.1=localhost).
EDIT: Give the output of this, as well:
```
sudo iptables -L -v
```

---

### Post by batrick on 2007-09-03
```
batrick@waterdeep:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:4D:EF:F3:98
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:feef:f398/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5843004 (5.5 MiB)  TX bytes:6737449 (6.4 MiB)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:30:1B:42:4A:BB
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xdead

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1800 (1.7 KiB)  TX bytes:1800 (1.7 KiB)

```

```
batrick@waterdeep:~$ ping -c5 www.google.com
PING www.l.google.com (72.14.253.104) 56(84) bytes of data.
64 bytes from po-in-f104.google.com (72.14.253.104): icmp_seq=1 ttl=238 time=77.3 ms
64 bytes from po-in-f104.google.com (72.14.253.104): icmp_seq=2 ttl=238 time=77.4 ms
64 bytes from po-in-f104.google.com (72.14.253.104): icmp_seq=3 ttl=238 time=79.0 ms
64 bytes from po-in-f104.google.com (72.14.253.104): icmp_seq=4 ttl=238 time=76.3 ms
64 bytes from po-in-f104.google.com (72.14.253.104): icmp_seq=5 ttl=238 time=106 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4036ms
rtt min/avg/max/mdev = 76.380/83.301/106.307/11.537 ms

```

```
batrick@waterdeep:~$ sudo iptables -L -v
Password:
Chain INPUT (policy ACCEPT 2 packets, 491 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 2 packets, 491 bytes)
 pkts bytes target     prot opt in     out     source               destination 

```

---

### Post by batrick on 2007-09-03
Also, I can't open a socket on any port but 80 and 22 (may be some others). With Lua:

```
>require "socket"
>return socket.connect("localhost", 8080)
nil   connection refused
> return socket.connect("www.google.com", 80)
tcp{client}: 0x808e724
> return socket.connect("www.google.com", 8080) -- Just blocks here

```

I know you might not be familiar with Lua, but hopefully it gives some insight into the problem.

---

### Post by p_quarles on 2007-09-03
> **batrick said:**
> Also, I can't open a socket on any port but 80 and 22 (may be some others). With Lua:

```
>require "socket"
>return socket.connect("localhost", 8080)
nil   connection refused
> return socket.connect("www.google.com", 80)
tcp{client}: 0x808e724
> return socket.connect("www.google.com", 8080) -- Just blocks here

```

I know you might not be familiar with Lua, but hopefully it gives some insight into the problem.
I don't know what to make of the socket error there, but all of the other tests you ran returned normal results . . . so I'm stumped, for now.

The question is why apt is attempting to connect to the localhost loopback to get to the repos. I'm going to take a look at some config files to see if I can get any further ideas. In the meantime, you might try pinging security.ubuntu.com and us.archive.ubuntu.com.

---

### Post by batrick on 2007-09-03
Pings to those sites were fine.

---

### Post by batrick on 2007-09-03
I can bind to the port 8080 ok inside a program, but trying to connect to it is blocked, so I imagine that's the problem. How can I open the port? I have no idea how it got blocked, it always used to work :S

---

### Post by p_quarles on 2007-09-03
APT wouldn't normally use port 8080 any more than it would use the loopback. It uses non-reserved high ports. For instance, the following is output from netstat directly after running an update:
```
tcp        0      0 10.0.0.4:56709          91.189.88.31:80         TIME_WAIT
```The outgoing request was using port 56709. If you run "host" on the remote address you'll see that it's one of the Canonical repos. 

So, whatever is going on here has to do with the fact that it's using the wrong interface altogether. 

Others may have better suggestions, but this is all I can think of:
1) Look through the files in /etc/apt/apt.conf.d/ for anything that specifies an interface. I just looked through these, and there shouldn't be anything like that.
2) Maybe APT is just broken. You might give this a shot:
```
sudo dpkg --configure apt-get
```
EDIT: Strike the above; wrong package name. Should be:
```
sudo dpkg --configure apt-utils
```

---

### Post by batrick on 2007-09-03
```
batrick@waterdeep:~$ sudo dpkg --configure apt-utils
Password:
dpkg: error processing apt-utils (--configure):
 package apt-utils is already installed and configured
Errors were encountered while processing:
 apt-utils
```

I couldn't find anything about an interface in the files in /etc/apt/apt.conf.d

---

### Post by p_quarles on 2007-09-03
Yeah, it looks like I'm out of my depth here. One last thing to suggest, though:
```
sudo apt-get check -f
```
That will look for broken packages and attempt to fix them.

---

### Post by batrick on 2007-09-03
nope :(

---

### Post by p_quarles on 2007-09-03
I just scanned through some of the [bug reports for APT]("http://bugs.debian.org/cgi-bin/pkgreport.cgi?src=apt#_0_3_4"), and the only thing I noticed was that some people were having similar problems when they were using proxies. Dunno if that helps.

---

### Post by batrick on 2007-09-03
Nope I'm not using a proxy, just going straight through my router.

---

### Post by p_quarles on 2007-09-03
Wish I could be of more help. If I were in your position, I'd give this another several days and see if someone else can help. Then I'd just back up and reinstall. 

You might also try using dpkg to flatout remove and reinstall [apt-utils]("http://packages.debian.org/stable/admin/apt"). I wouldn't hold out high hopes for that method, though.

---

### Post by GigaVolt on 2007-09-04
1) unset http_proxy
2) ap-get update
3) cat /etc/resolv.conf
4) route

---

### Post by batrick on 2007-09-04
Wow that fixed it!

unset http_proxy

I'm not sure how that got set ><

Thanks!

---

### Post by GigaVolt on 2007-09-04
Pleasure is mine. 
http_proxy is environment variables. For real unset this variable edit you are /root/.bashrc file or /etc/profile.

---

### Post by sleepyjon on 2007-10-08
> **GigaVolt said:**
> 1) unset http_proxy
2) ap-get update
3) cat /etc/resolv.conf
4) route

Thanks, I had a similar problem and this solved it for me aswell.

---

