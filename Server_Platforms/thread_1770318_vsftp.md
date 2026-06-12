---
title: "vsftp"
date: 2011-05-29
forum: Server Platforms
---

### Post by luofeiyu on 2011-05-29
my network:
public network ip is   xx.yy.zz.ww
one ip share (adsl+route,ip is 192.168.1.1),
A machine (ip 192.168.1.100),there is vsftp on it 
B machine (ip 192.168.1.101),there is vsftp on it 

I make a ip mapping
the port 21(192.168.1.1) was mapped to A machine (ip 192.168.1.100)

my friend can connect  A machine  from internet,
the port 20(192.168.1.1) was mapped to B machine (ip 192.168.1.101)

the fellowing  command can't run  
ftp   xx.yy.zz.ww:20
ftp   xx.yy.zz.ww:21

i can only connect A machine with command
ftp  xx.yy.zz.ww

 how to make another map ,can make my friend connect my  machine B ?

---

