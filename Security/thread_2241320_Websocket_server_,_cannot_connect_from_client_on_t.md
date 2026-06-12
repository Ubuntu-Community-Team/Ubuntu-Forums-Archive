---
title: "Websocket server , cannot connect from client on the  lan"
date: 2014-08-25
forum: Security
---

### Post by patrickcr on 2014-08-25
Hi , i'm new on UBUNTU, i dont have to much experience on IPTABLES.. i' not sur but i think thre is a issue on that..
So i created an java app, that loads a websocket server using an API for websockets.

By default, de websocket adress are pointing to 0.0.0.0, and i can connect to the websocket using the follow javascript sintax, if i'm trid from the host
ws://120.0.0.1:8080 works:
ws://IP adress:8080 wors
ws://localhost:8080 works too
the problem is when i trid o connect from an other comptuer on the lan..

I have the port 80 andd 8080 opne, i can still connect to the webserver, however to acees the websocket server  i cannot connect to it..

I think its beacause the program  process dones is not listenning in all interfaces... or as redirect from et01 to localhost that is not setted.. 

could someone tell me what is the cause of this problem,or  possible reasons for this issue???

I run the java program on widdonws it worlk weell on the lan, i dont know waht is missing, cause i'm not using linux every day...

I someone can help me i wou be gratefull

Thanks

Patrick

---

