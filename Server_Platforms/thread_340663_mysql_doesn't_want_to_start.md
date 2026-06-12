---
title: "mysql doesn't want to start"
date: 2007-01-17
forum: Server Platforms
---

### Post by antek on 2007-01-17
Hey.

Does anyone have any idea why mysqld doesn't want to start? I was trying to launch /etc/init.d/mysqld start, but it ended with 'failed' status. So i tried to launch it manually by entering 'mysqld' command, and it gave me an error, that it can't bind to the 3306 port and it may be in use (`pgrep mysql' shows nothing):
```
070117 19:57:26  InnoDB: Started; log sequence number 0 46032
070117 19:57:27 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
070117 19:57:27 [ERROR] Do you already have another mysqld server running on port: 3306 ?
070117 19:57:27 [ERROR] Aborting

070117 19:57:27  InnoDB: Starting shutdown...
070117 19:57:29  InnoDB: Shutdown completed; log sequence number 0 46032
070117 19:57:29 [Note] mysqld: Shutdown complete
```
I've checked the port with netcat:
```
$ nc -v -v localhost 3306
blackrazor.antonone.ath.cx [127.0.0.1] 3306 (mysql) : Connection refused
 sent 0, rcvd 0
```
so it looks like the port is free, because netcat'ing to a different port, like 13214 gives the save "connection refused" error message.

Any ideas?

---

### Post by jtc on 2007-01-17
I'm afraid it isn't that easy. Netcat gives you a connection refused no matter if it really is something running which is denying you or if there is simly nothing there. Better ways to check used ports is by running "nmap localhost" or (as root) "netstat -tap"

In this case it sounds as if you might have a halv-started mysqld remaining from the init-script. You could always check if you've got any running with "ps aux |grep mysqld"

---

### Post by antek on 2007-01-17
Thanks for a fast reply. I've checked with ps aux | grep mysqld, and with nmap, and there's no mentioning about mysqld.
```
Not shown: 1673 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
701/tcp  open  unknown
2049/tcp open  nfs
8009/tcp open  ajp13
```
I'm not sure what port 701 is (another port for nfs?), 25 is postfix, 80 is apache, not sure what 111 stands for (also nfs?) and 8009 is hm.. to connect apache with tomcat? :) Well, not so sure about that neither, anyway it seems that there's no mysqld running.

Here's the output from netstat -tap (from root):
```
tcp        0      0 *:nfs                   *:*                     LISTEN     -                   
tcp        0      0 blackrazor.antonon:6600 *:*                     LISTEN     3014/mpd            
tcp        0      0 *:4555                  *:*                     LISTEN     -                   
tcp        0      0 *:sunrpc                *:*                     LISTEN     1697/portmap        
tcp        0      0 *:2806                  *:*                     LISTEN     2895/rpc.statd      
tcp        0      0 blackrazor.antonon:smtp *:*                     LISTEN     2775/master         
tcp        0      0 *:701                   *:*                     LISTEN     2642/rpc.mountd     
tcp        1      0 192.168.1.2:3620        post.audioscrobbler:www CLOSE_WAIT 4016/rhythmbox      
tcp        0      0 192.168.1.2:3159        tw-in-f99.google.co:www ESTABLISHED4471/swiftfox-bin   
tcp        0      0 192.168.1.2:4060        host-195-116-239-3:5223 ESTABLISHED4173/ekg2           
tcp6       0      0 blackrazor.antonon:8005 *:*                     LISTEN     2840/java           
tcp6       0      0 *:8009                  *:*                     LISTEN     2840/java           
tcp6       0      0 *:www                   *:*                     LISTEN     3207/apache2        
tcp6       0      0 *:8180                  *:*                     LISTEN     2840/java           
tcp6       0      0 ip6-localhost:smtp      *:*                     LISTEN     2775/master         
tcp6     341      0 blackrazor.antonon:8009 blackrazor.antonon:3087 CLOSE_WAIT 2840/java           
tcp6      24      0 blackrazor.antonon:8009 blackrazor.antonon:3085 CLOSE_WAIT 2840/java           
tcp6      12      0 blackrazor.antonon:8009 blackrazor.antonon:3084 CLOSE_WAIT 2840/java           
tcp6      15      0 blackrazor.antonon:8009 blackrazor.antonon:3082 CLOSE_WAIT 2840/java
```
I have some apps running, but mysqld is not among them...

---

### Post by antek on 2007-01-17
Btw. i've also tried rebooting the system, it didn't help.

---

### Post by jtc on 2007-01-17
Well, did a quick Google. Seems like one of the reasons people get this error is that their network loopback interface isn't set up properly. How does your /etc/network/interfaces look like? Do you have these two lines, or something similar?

auto lo
iface lo inet loopback

---

### Post by antek on 2007-01-17
Here's the file (I also tried google but I didn't find anything which could help):

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
    hostname blackrazor.antonone.ath.cx

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by antek on 2007-01-17
Damn!! Sorry for trouble... it's fixed now. I feel really stupid. :P
I am in the different network right now, and I forgot to change bind-address in my.cnf. There was an ip 192.168.0.9 (the one I used for this computer earlier), changing it to 127.0.0.1 fixed the problem.

Again, sorry for trouble, and thanks for your time :)

---

### Post by jtc on 2007-01-17
Glad it worked out :-) No problem!

---

### Post by shk on 2007-03-08
:lolflag: I just had the exact same problem . I had an ip change some days ago but the computer only restarted today due to a power fluctuation. It didn't cross my mind that this could be the problem . Great luck comming across this post , thanks :guitar:

---

