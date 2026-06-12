---
title: "New to making servers, big question."
date: 2009-08-31
forum: Server Platforms
---

### Post by silverfire675 on 2009-08-31
I have setup my server with teh desktop-server combo and have been using webmin and direct commands.  I have a friend who has had more experience with linux and Im trying to get it so he can acess it and help me create and run this server.  My question is this, how do I find the default gateway so I can type in a certain ip address in my internet browser and connect.  Or am I going to need something like Putty or Hyperterminal.   In any case I need help finding the server ip and port(I think this is 22 right now through ssh, but Im going to change it).   

Thanks for helping a noob.

Silver


UPDATE:  I typed route into my server and I only get 1 gateway address which is the local one.  I need help connecting remotely.

---

### Post by cdenley on 2009-08-31
```

wget -O - -q http://whatismyip.org/ && echo

```

If you have a router between you and your ISP, then you will need to configure your router to forward inbound connections on port 22 to your server (port forwarding).

---

### Post by twoaday on 2009-08-31
There are several ways to allow remote access to teh server depending on what yu have set up but if all yu are looking for is the out side IP address so that your friend can get to your machine, then try [http://www.whatismyip.com/](http://www.whatismyip.com/). This will give you the address that he/she needs to connect. Now if you are behind a router and or firewall (recommended) then you will need to do port forwarding to direct the traffic to the server. Getting into your router / firewall and reading through the set up options should help walk you through that. You can always check this site out [http://portforward.com/](http://portforward.com/) or read the manual for you equipment, and if all else fails hit up the manufacturer of said equipment for more information. 

Hope this helps

---

### Post by silverfire675 on 2009-08-31
Thanks guys you ro:guitar:ck

---

