---
title: "nmap 127.0.0.1: a lot of open ports"
date: 2007-07-30
forum: Server Platforms
---

### Post by chinaski on 2007-07-30
I am no good at all about security stuff, but yesterday I made a fresh install of Ubuntu Feisty and this is the nmap 127.0.0.1 output

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-31 03:24 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1657 closed ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
7/tcp     open  echo
9/tcp     open  discard
11/tcp    open  systat
15/tcp    open  netstat
25/tcp    open  smtp
70/tcp    open  gopher
79/tcp    open  finger
80/tcp    open  http
109/tcp   open  pop2
110/tcp   open  pop3
111/tcp   open  rpcbind
119/tcp   open  nntp
138/tcp   open  netbios-dgm
139/tcp   open  netbios-ssn
143/tcp   open  imap
512/tcp   open  exec
513/tcp   open  login
514/tcp   open  shell
515/tcp   open  printer
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
2001/tcp  open  dc
4000/tcp  open  remoteanything
6000/tcp  open  X11
6001/tcp  open  X11:1
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.158 seconds

```

is everything all right? because reading some names I have strange feelings...

p.s. Shields Up's scan give me all service ports stealth

---

### Post by AlexThomson_NZ on 2007-07-30
I'm no security expert either, but nmap only gives this on my box:
```

Interesting ports on localhost (127.0.0.1):
Not shown: 1694 closed ports
PORT    STATE SERVICE
80/tcp  open  http
81/tcp  open  hosts2-ns
631/tcp open  ipp

```

---

### Post by chinaski on 2007-07-31
hi,

I've installed Firestarter and disabled Tor + Privoxy from starting automatically at system boot (I know this maybe it's not relevanyt for the issue) and though did not set any rule for Iptables (which has default settings) now nmap 127.0.0.1 show:

> Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-31 13:08 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp


I am only browsing the web, no mail client open, nothing special running

I am confused...

---

### Post by chinaski on 2007-07-31
I am DUMB

when portsentry is on I got all the above listed ports as open with nmap 127.0.0.1

when is off, only the last two I've listed

sorry if I posted for nothing :(

---

### Post by rich.bradshaw on 2007-07-31
That's weird...

Where did you get the download from etc?

There shouldn't be anything open.

Maybe you should nmap your external IP instead? Not sure if it makes a difference...

---

### Post by chinaski on 2007-07-31
> **rich.bradshaw said:**
> That's weird...

Where did you get the download from etc?

you mean portsentry? from Synaptic
> 
There shouldn't be anything open.
so what could I do in order to get things normally?
> 
Maybe you should nmap your external IP instead? Not sure if it makes a difference...```
za@station-1:~$ nmap xxx.xx.xxx.xx

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-31 16:22 CEST
Interesting ports on adsl-xxx-xx.xx-x.xxx.xx (xxx.xxx.xx.xx):
Not shown: 1696 closed ports
PORT   STATE SERVICE
80/tcp open  http

```is that ok?

---

### Post by xpod on 2007-07-31
I`m hoping this is even better :)

```
dad@home1:~$ nmap **.**.**.**.

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-31 16:24 BST
All 1697 scanned ports on ***.***.***.**.my.crazycable.line.com (**.**.**.**) are closed

Nmap finished: 1 IP address (1 host up) scanned in 0.356 seconds
```

I hope my pc is a bit securer than my isp`s online help forum anyway.:)
It was apparently  hacked by some disgruntled kiddie yesterday who, after gaining admin rights to the place then left a quite a bit of destruction in his wake seemingly.:(
Not only that but visitors were apparently infected too after clicking on dodgy links to dodgy exe`s that had been left...or something like that anyway.

I dont know.....you only go on to get your broadband checked or complain about the speeds but then leave with you machine in tatters....lol

I really should`nt laugh eh:-\"

---

