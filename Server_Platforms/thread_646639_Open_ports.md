---
title: "Open ports"
date: 2007-12-21
forum: Server Platforms
---

### Post by JayFunGee on 2007-12-21
I am a bit concerned about the status of ports on my machine. After running a scan I found a number of open ports, most of which I recognise but a few have me confused. Can anybody give me comments / advise on the following extract of the port scan:

445	open	microsoft-ds (something to do with WINE?)
34257	open	unknown
44071	open	unknown
47235	open	unknown

Thanks
:confused:

---

### Post by gombadi on 2007-12-21
Open up a terminal window and type -

```

sudo netstat -plntu

```

That will show you what ports are open on the machine and what program and process ID is actually listening on the port.

Post the results if you want some more help.

---

### Post by JayFunGee on 2007-12-21
Thanks Gombadi appreciate it. Here it is:
btw, apart from normal software, I run apache, postgresql and mysql

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:37417           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     5154/mysqld         
tcp        0      0 0.0.0.0:44586           0.0.0.0:*               LISTEN     4314/rpc.statd      
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     5366/smbd           
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4295/portmap        
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5668/apache2        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5073/cupsd          
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     5693/postgres       
tcp        0      0 0.0.0.0:35834           0.0.0.0:*               LISTEN     5327/rpc.mountd     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     5366/smbd           
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          4314/rpc.statd      
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          -                   
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          5327/rpc.mountd     
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          5471/avahi-daemon:  
udp        0      0 192.168.1.4:137         0.0.0.0:*                          5364/nmbd           
udp        0      0 0.0.0.0:137             0.0.0.0:*                          5364/nmbd           
udp        0      0 192.168.1.4:138         0.0.0.0:*                          5364/nmbd           
udp        0      0 0.0.0.0:138             0.0.0.0:*                          5364/nmbd           
udp        0      0 0.0.0.0:674             0.0.0.0:*                          4314/rpc.statd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                          6083/dhclient       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5471/avahi-daemon:  
udp        0      0 0.0.0.0:111             0.0.0.0:*                          4295/portmap

---

### Post by gombadi on 2007-12-21
Eliminate the programs we know

You are also running nfs on these ports
tcp 0 0 0.0.0.0:2049 0.0.0.0:* LISTEN -
tcp 0 0 0.0.0.0:44586 0.0.0.0:* LISTEN 4314/rpc.statd
tcp 0 0 0.0.0.0:111 0.0.0.0:* LISTEN 4295/portmap
tcp 0 0 0.0.0.0:35834 0.0.0.0:* LISTEN 5327/rpc.mountd
udp 0 0 0.0.0.0:32768 0.0.0.0:* 4314/rpc.statd
udp 0 0 0.0.0.0:2049 0.0.0.0:* -
udp 0 0 0.0.0.0:32771 0.0.0.0:* 5327/rpc.mountd
udp 0 0 0.0.0.0:674 0.0.0.0:* 4314/rpc.statd
udp 0 0 0.0.0.0:111 0.0.0.0:* 4295/portmap

mysql and postgress
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 5154/mysqld
tcp 0 0 127.0.0.1:5432 0.0.0.0:* LISTEN 5693/postgres

samba
tcp 0 0 0.0.0.0:139 0.0.0.0:* LISTEN 5366/smbd
tcp 0 0 0.0.0.0:445 0.0.0.0:* LISTEN 5366/smbd
udp 0 0 192.168.1.4:137 0.0.0.0:* 5364/nmbd
udp 0 0 0.0.0.0:137 0.0.0.0:* 5364/nmbd
udp 0 0 192.168.1.4:138 0.0.0.0:* 5364/nmbd
udp 0 0 0.0.0.0:138 0.0.0.0:* 5364/nmbd

Apache
tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN 5668/apache2

Misc stuff that is normally running
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 5073/cupsd
udp 0 0 0.0.0.0:32772 0.0.0.0:* 5471/avahi-daemon:
udp 0 0 0.0.0.0:68 0.0.0.0:* 6083/dhclient
udp 0 0 0.0.0.0:5353 0.0.0.0:* 5471/avahi-daemon:

we are left with -
tcp 0 0 0.0.0.0:37417 0.0.0.0:* LISTEN -
udp 0 0 0.0.0.0:32770 0.0.0.0:* -

These are different from the ports you reported in the first post. They could be part of nfs/portmap which uses dynamic port allocation. They do not show what process ID is listening. Not necessarily a bad thing as I have seen this before. Restart the system and see if they appear on the same ports or different ports appear. Do a google search to see if anything shows up. 

You seem to be on a private network so you probably have a router protecting your system. Not open to the Internet is a good thing :-)

---

