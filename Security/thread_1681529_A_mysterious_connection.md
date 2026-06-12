---
title: "A mysterious connection"
date: 2011-02-04
forum: Security
---

### Post by darknuts on 2011-02-04
Hello everyone! This is my first post on this site. I have what might be a slight security issue. I'm running Firestarter 1.0.3 on Ubuntu 10.4 LTS and I've picked up a sustained connection from host 72.167.18.239:37740. For some reason this connection has slipped through my normally stringent firewall and I cant figure out why its connecting to me. I tried to block it but I'm unable. I looked it up online and I found that it belongs to 'godaddy' but why would they connect to me? Does anyone know what this is for and if it can hurt my computer?

---

### Post by aromo on 2011-02-04
If you don't know what it is, block it and see if you broke something.  I wouldn't accept any inbound connections I don't know anything about.  In your firewall, you should be able to explicitly block by IP address, port or a combination of both.

I hope that helps.

---

### Post by darknuts on 2011-02-04
I tried that. Under my firewall's policy, it only allows me to _unblock_ ports and access from other IPs. It seems its restrictive by nature and it has given me a few headaches while trying to establish my network. It blocks anything I don't specifically allow. Thats why i cant figure out how this connection was established. Is there any way I can find out what program its interacting with?

Correction:
I figured out how to block _outbound_ traffic but not inbound. I blocked connection to the port and IP in question. Nothing has changed.

---

### Post by moody_mark on 2011-02-04
Whats the output of the command:

```
netstat -lntup
```

It should tell you which ports are open and which process is using them

---

### Post by darknuts on 2011-02-04
Here's what I got:

```
bearcat@bearcat8f:~$ sudo netstat -lntup
[sudo] password for bearcat: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:49152           0.0.0.0:*               LISTEN      3168/mediatomb  
tcp        0      0 0.0.0.0:39587           0.0.0.0:*               LISTEN      12653/skype     
tcp        0      0 0.0.0.0:10021           0.0.0.0:*               LISTEN      16143/mono      
tcp        0      0 0.0.0.0:54698           0.0.0.0:*               LISTEN      16098/Giver     
tcp        0      0 0.0.0.0:5904            0.0.0.0:*               LISTEN      2012/krfb       
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      13481/sshd      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1193/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      19866/smbd 
tcp6       0      0 :::139                  :::*                    LISTEN      19866/smbd      
tcp6       0      0 :::5900                 :::*                    LISTEN      1858/vino-server
tcp6       0      0 :::80                   :::*                    LISTEN      1248/apache2    
tcp6       0      0 :::56529                :::*                    LISTEN      7622/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      13481/sshd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1193/cupsd      
udp        0      0 0.0.0.0:39387           0.0.0.0:*                           18240/VirtualBox
udp        0      0 0.0.0.0:33383           0.0.0.0:*                           18240/VirtualBox
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           936/avahi-daemon: r
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           3168/mediatomb  
udp        0      0 192.168.1.5:137         0.0.0.0:*                           19874/nmbd      
udp        0      0 0.0.0.0:137             0.0.0.0:*                           19874/nmbd      
udp        0      0 192.168.1.5:138         0.0.0.0:*                           19874/nmbd      
udp        0      0 0.0.0.0:138             0.0.0.0:*                           19874/nmbd      
udp        0      0 0.0.0.0:39587           0.0.0.0:*                           12653/skype     
udp        0      0 127.0.0.1:52014         0.0.0.0:*                           12653/skype     
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1436/dhclient   
udp        0      0 127.0.0.1:46923         0.0.0.0:*                           3168/mediatomb  
udp        0      0 0.0.0.0:47692           0.0.0.0:*                           936/avahi-daemon: r
``` I couldn't find the IP or port in question.

---

### Post by moody_mark on 2011-02-04
Netstat will show you a definitive list of what connections you have. Where else are you seeing this connection? Seems to me like it could be a "red herring"

---

### Post by darknuts on 2011-02-04
hmm. I'm only seeing it on my firewall under "Active connections". Maybe if I restart, it'll go away.

---

### Post by darknuts on 2011-02-04
I was looking on another board and the guy there has the same problem as me. 

[http://ubuntuforums.org/showthread.php?t=1681060](http://ubuntuforums.org/showthread.php?t=1681060)

But no answers there either...

---

### Post by darknuts on 2011-02-04
Well, I did a system restart and It went away. I'll see if it comes back or not.

---

### Post by hackertarget on 2011-02-04
Skype? it uses a peer to peer model and can connect to seemingly strange random IP addresses. Usually on port 443 from what I recall though.

I have chased down many a seemingly random connection to strange countries when reviewing firewall reports only to find someone had skype on the client.

---

