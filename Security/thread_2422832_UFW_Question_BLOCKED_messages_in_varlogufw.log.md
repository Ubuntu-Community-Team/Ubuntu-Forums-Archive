---
title: "UFW Question BLOCKED messages in /var/log/ufw.log"
date: 2019-07-13
forum: Security
---

### Post by mike.lussier on 2019-07-13
This is ubuntu 19.04 up to date on all patches

I have setup UFW and I keep getting these blocked messages. 
I have tried several different ways to allow the traffic but I continue to see the messages. 
What have I missed? 

 Anywhere                   ALLOW IN    172.18.20.0/26 8443/tcp   
 Anywhere                   ALLOW IN    172.18.20.0/26/tcp        
 8443/tcp                   ALLOW IN    172.18.20.0/26            
 8443/tcp                   ALLOW IN    172.18.20.0/26 1023:65535/tcp
1023:65535/tcp             ALLOW IN    172.18.20.33              
Anywhere                   ALLOW IN    172.18.20.33 8443/tcp     


Jul 13 08:27:13 desktop kernel: [138520.289068] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=104.17.49.74 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x20 TTL=56 ID=50112 DF PROTO=TCP SPT=443 DPT=57772 WINDOW=30 RES=0x00 ACK URGP=0 
Jul 13 08:27:43 desktop kernel: [138550.523353] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=104.17.49.74 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x20 TTL=56 ID=50114 DF PROTO=TCP SPT=443 DPT=57772 WINDOW=30 RES=0x00 ACK URGP=0

---

### Post by TheFu on 2019-07-13
Please edit your post to use 'code tags' and ensure the exact output from ```
sudo ufw status
``` is posted as it appears in the terminal. There are impossible typos in the stuff above that would never work.

---

### Post by mike.lussier on 2019-07-13
```

root@desktop:/var/www/mrtg# ufw status
Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere                  
514/udp                    ALLOW       Anywhere                  
Anywhere                   ALLOW       192.168.20.24             
Anywhere                   ALLOW       192.168.20.25             
Anywhere                   ALLOW       172.18.20.59              
Anywhere                   ALLOW       172.18.21.59              
Anywhere                   ALLOW       172.18.22.59              
Anywhere                   ALLOW       172.18.23.59              
Anywhere                   ALLOW       192.168.21.24             
Anywhere                   ALLOW       192.168.22.24             
Anywhere                   ALLOW       192.168.23.24             
Anywhere                   ALLOW       192.168.28.5              
Anywhere                   ALLOW       192.168.28.7              
Anywhere                   ALLOW       192.168.28.11             
20,21,10000:10100/tcp      ALLOW       192.168.22.0/26           
20,21,10000:10100/tcp      ALLOW       192.168.20.0/24           
Anywhere                   ALLOW       192.168.20.0/24 161/udp   
Anywhere                   ALLOW       192.168.21.0/24 161/udp   
Anywhere                   ALLOW       192.168.22.0/24 161/udp   
Anywhere                   ALLOW       192.168.23.0/24 161/udp   
Anywhere                   ALLOW       172.18.20.0/26 161/udp    
Anywhere                   ALLOW       172.18.21.0/26 161/udp    
Anywhere                   ALLOW       172.18.22.0/26 161/udp    
Anywhere                   ALLOW       172.18.23.0/26 161/udp    
Anywhere                   ALLOW       192.168.24.0/24 161/udp   
Anywhere                   ALLOW       192.168.25.0/24 161/udp   
Anywhere                   ALLOW       192.168.26.0/24 161/udp   
Anywhere                   ALLOW       192.168.27.0/24 161/udp   
Anywhere                   ALLOW       192.168.28.0/24 161/udp   
Anywhere                   ALLOW       192.168.29.0/24 161/udp   
Anywhere                   ALLOW       192.168.24.0/24           
Anywhere                   ALLOW       192.168.25.0/24           
Anywhere                   ALLOW       192.168.26.0/26           
Anywhere                   ALLOW       192.168.27.0/26           
Anywhere                   ALLOW       192.168.28.0/26           
Anywhere                   ALLOW       192.168.29.0/26           
Anywhere                   ALLOW       192.168.20.0/24           
Anywhere                   ALLOW       192.168.20.100 631/tcp    
Anywhere                   ALLOW       172.18.20.0/26 8443/tcp   
Anywhere                   ALLOW       172.18.21.0/26 8443/tcp   
Anywhere                   ALLOW       172.18.22.0/26 8443/tcp   
Anywhere                   ALLOW       172.18.23.0/26 8443/tcp   
Anywhere                   ALLOW       172.18.20.0/26/tcp        
Anywhere                   ALLOW       172.18.20.0/26/udp        
8443/udp                   ALLOW       172.18.20.0/26            
8443/tcp                   ALLOW       172.18.20.0/26            
8443/tcp                   ALLOW       172.18.20.0/26 1023:65535/tcp
1023:65535/tcp             ALLOW       172.18.20.33              
Anywhere                   ALLOW       172.18.20.33 8443/tcp     


```

---

### Post by TheFu on 2019-07-13
From what I see, 104.x.x.x isn't allowed to access port 443.  Perhaps they need to be told that the web server in on port 8443?

---

### Post by mike.lussier on 2019-07-13
the only thing that has access to the web server are local networks  192.168.[20-29].0  & 172.18.[20-23].0

---

### Post by TheFu on 2019-07-13
> **mike.lussier said:**
> the only thing that has access to the web server are local networks  192.168.[20-29].0  & 172.18.[20-23].0

So .... I don't understand the issue.
SRC=104.17.49.74 is the IP being blocked, which is what you want.

Is there something else?

---

### Post by mike.lussier on 2019-07-13
Sorry, 
I see I pasted the wrong item on the initial post. The client 192.168.20.26 is blocked  from the server 172.18.20.33 

```

TO=TCP SPT=8443 DPT=42200 WINDOW=0 RES=0x00 RST URGP=0 
Jul 13 14:02:10 desktop kernel: [158616.909576] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=172.18.20.33 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=TCP SPT=8443 DPT=42310 WINDOW=0 RES=0x00 RST URGP=0 
Jul 13 14:02:10 desktop kernel: [158616.909598] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=172.18.20.33 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=TCP SPT=8443 DPT=42310 WINDOW=0 RES=0x00 RST URGP=0 
Jul 13 14:04:12 desktop kernel: [158739.267699] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=172.18.20.33 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=TCP SPT=8443 DPT=42440 WINDOW=0 RES=0x00 RST URGP=0 
Jul 13 14:04:12 desktop kernel: [158739.267715] [UFW BLOCK] IN=eno1 OUT= MAC=d4:c9:ef:f4:e5:89:00:26:0b:d5:15:71:08:00 SRC=172.18.20.33 DST=192.168.20.26 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=0 DF PROTO=TCP SPT=8443 DPT=42440 WINDOW=0 RES=0x00 RST URGP=0 

```

---

### Post by SeijiSensei on 2019-07-13
The client in that entry is 172.18.20.33.

---

### Post by TheFu on 2019-07-13
That isn't what the "code" block you posted in #7 show. It shows the exact opposite source and target IPs.
DETAILS MATTER.  When the logs and the text describing them don't match, I'm confused.

Draw a picture. Show the source machine, any relevant firewall rules on it, and network equipment between, especially if there are multiple NICs, and the target machine with any relevant firewall rules on it.  Really for the complexity level of firewall rules you seem to need, ufw is a poor choice for the interface into the Linux firewall.  I would have switched to iptables after about the 8th rule.  ufw adds other rules that don't show up in ufw output.  They will show in iptables.  Order of the rules matters.

---

### Post by mike.lussier on 2019-07-13
172.18.20.33 is a controller  , client is 192.168.20.26 this is the machine im running ufw

---

