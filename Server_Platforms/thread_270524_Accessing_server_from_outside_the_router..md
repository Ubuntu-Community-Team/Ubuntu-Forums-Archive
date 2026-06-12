---
title: "Accessing server from outside the router."
date: 2006-10-03
forum: Server Platforms
---

### Post by st_itty on 2006-10-03
I'm rather new to linux. I have set up an headless server at home. I use puTTy to access it from other computers inside my home network and it works just fine. What do I have to do in order for me to access the server from outside the network. Do I have to forward some port on the router to the server ip? I have a dyanmic dns alias which I succesfully use to remote into a windows desktop. I did setup the router to forward port 22 to the server ip but that doesnt seem to be working. Do I need to setup anything else on the server?
Any help woud be appreciated.
Thanks.

---

### Post by chipyoung on 2006-10-03
If you are forwarding port 22 to the server you want to access, then all you should need to do when you ssh, is put in the ip address of your router (The one assigned to you)(i.e ssh xx.xx.xx.xx).  Of course, make sure that you have ssh-server installed on your server.

cly

---

### Post by st_itty on 2006-10-04
Thanks my router was acting up it wasnt forwaring the port 22 properly. I resetted the router and it now works like a charm.

---

