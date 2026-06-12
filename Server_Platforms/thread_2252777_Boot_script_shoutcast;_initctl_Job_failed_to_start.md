---
title: "Boot script shoutcast; initctl: Job failed to start (Ubuntu Linux 14.04.1)"
date: 2014-11-14
forum: Server Platforms
---

### Post by kevinx2 on 2014-11-14
> [INDENT]   #Shoutcast      
#      
#Shoutcast      

description  "Shoutcast"


      start on runlevel [2345]

      #stop on runlevel [!2345]      
pre-start script   ? 
  start on runlevel [2345]      
stop on runlevel [!2345]

      
end script


      exec /home/shoutcast/sc_serv /home/shoutcast/sc_serv.conf

 [/INDENT]


 But when I hit the 'Start Now'-button, I get the message:

> 
Starting service Shoutcast ..
[INDENT]      initctl: Job failed to start

      .. failed![/INDENT]
[INDENT]

[/INDENT]
 Who can help me to solve my problem.
  Kinds regards, Kevinx

---

