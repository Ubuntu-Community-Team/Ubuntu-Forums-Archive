---
title: "MPICH2: failed to handshake with mpd on node0"
date: 2010-11-08
forum: Server Platforms
---

### Post by naeg on 2010-11-08
Hello community,

I tried to setup a cluster using this howto: [https://wiki.ubuntu.com/MpichCluster](https://wiki.ubuntu.com/MpichCluster)

What I have:
* nfs setup with same home directory for node and master
* password-less ssh connection
* mpich2 installed on both machines
* host entries in /etc/hosts(I can ping on hostnames)

But it fails, when I try to mpdboot on master(doesn't matter if mpd runs on the node or not). That's what I get:

```
master@master:~$ mpdboot -n 2 -v
running mpdallexit on master
LAUNCHED mpd on master via
RUNNING: mpd on master
LAUNCHED mpd on node0 via master
mpdboot_master (handle_mpd_output 407): failed to handshake with mpd on node0; recvd output={}
```I googled around, but I couldn't fint a working solution for me...

My /etc/hosts on master looks like:
```
127.0.0.1 localhost master
10.60.66.130 node0
```My /etc/hosts on node0:
```
127.0.0.1 localhost node0
10.60.66.129 master
```The IP adresses are right, since I can ssh and ping the other machine using the hostname.

Thanks in advance


greetings, naeg

---

### Post by pacomet on 2010-11-09
Hi, I'm having the same problem. 

meteo@boira:~$ cat mpd.hosts
boira
boira2
boira3

meteo@boira:~$ mpdboot -n 3
mpdboot_boira (handle_mpd_output 407): failed to handshake with mpd on boira2; recvd output={}

The curious thing is that it runs fine for the master and one node
meteo@boira:~$ mpdboot -n 2
meteo@boira:~$ mpdtrace
boira
boira2

and if I remove boira2 and leave only node boira3 then it runs fine.

Hope someone reads this message and can help.

Greetings

---

### Post by evad1089 on 2010-11-10
naeg:

make your hosts:

master:

127.0.0.1 localhost
10.60.66.129 master
10.60.66.130 node0

node0:
127.0.0.1 localhost 
10.60.66.129 master
10.60.66.130 node0

---

