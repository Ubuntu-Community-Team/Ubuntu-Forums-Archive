---
title: "HTB split of outgoing traffic for services of one LAN computer (server) and rest"
date: 2013-12-08
forum: Server Platforms
---

### Post by luna.vulpo on 2013-12-08
After change to Ubuntu server I have a strange big upload. Server is  also router so I think I could set HTB. It is first time when I  configure HTB so I ask you help.

What I want to do: 4Mbit/s upload split in half. First half for server  and second half for rest of LAN computers. Each service: www,ssh,smtp,  imap shouldn't fill up the upload. So for each minimum 200kbps and  maximum 2000kbps.

I made same rules using HTB but I have some problems with it. And also I have questions:

How to add second rule for rest of LAN computers?
Can rules have a some normal name like a:www?
can be name for class like 1:1:1?
How to add rule which split one ip and rest?

my configuration:

```
/etc/network/interfaces
iface p3p1 inet static
address <IP_publiczne>
netmask 255.255.255.248
gateway <IP_publiczne>

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
```

my proposal of rules
```
### cleaning # czszczenie regu&#322;
tc qdisc del root dev p3p1
tc qdisc add dev p3p1 root handle 1:0 htb default 2

tc class add dev p3p1 parent 1:0 classid 1:1 htb rate 4000kbit ceil 4000kbit

### split of stream # podzia&#322; ca&#322;ego pasma: www, smtp, imap, ssh, inne
#inne # rest
tc class add dev p3p1 parent 1:1 classid 1:2 htb rate 200kbit ceil 2000kbit
#www
tc class add dev p3p1 parent 1:1 classid 1:3 htb rate 200kbit ceil 2000kbit
#smtp
tc class add dev p3p1 parent 1:1 classid 1:4 htb rate 200kbit ceil 2000kbit
#imap
tc class add dev p3p1 parent 1:1 classid 1:5 htb rate 200kbit ceil 2000kbit
#ssh
tc class add dev p3p1 parent 1:1 classid 1:6 htb rate 200kbit ceil 2000kbit


#### filters # filtry
#www
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 80 0xffff flowid 1:3
#smtp
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 25 0xffff flowid 1:4
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 587 0xffff flowid 1:4
#imap
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 143 0xffff flowid 1:5
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 993 0xffff flowid 1:5
#ssh
tc filter add dev p3p1 protocol ip parent 1:0 u32 match ip sport 22 0xffff flowid 1:6
#inne - brak, bo w regule na pocz&#261;tku w parametrze default jest 2, czyli trafia do filtru nr 1:2


# wszystkim po równo
tc qdisc add dev p3p1 parent 1:2 handle 2:0 sfq perturb 10
tc qdisc add dev p3p1 parent 1:3 handle 3:0 sfq perturb 10
tc qdisc add dev p3p1 parent 1:4 handle 4:0 sfq perturb 10
tc qdisc add dev p3p1 parent 1:5 handle 5:0 sfq perturb 10
tc qdisc add dev p3p1 parent 1:6 handle 6:0 sfq perturb 10

```

---

