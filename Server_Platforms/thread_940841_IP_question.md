---
title: "IP question"
date: 2008-10-07
forum: Server Platforms
---

### Post by terjit on 2008-10-07
I have a question that i am putting under the server category because it is happening on my server.  I have searched the internet for a few days to see if i could find a solution and no luck so here goes.

I have a server that has ubuntu server on it and hosts apache/php/mysql.  I was recently told by the it department here at my university, where i work, that the are changing some networks around and my formerly dynamically assigned static ip address was now going to be fully static.  so i made the changes in /etc/network/interfaces and restarted my networking and all was dandy.  However about an hour later i got a call back that i was still requesting a dhcp address from them.  I cannot find any way that the server is doing this.  Any help would be great

Thanks

---

### Post by cdenley on 2008-10-07
> **terjit said:**
> I have a question that i am putting under the server category because it is happening on my server.  I have searched the internet for a few days to see if i could find a solution and no luck so here goes.

I have a server that has ubuntu server on it and hosts apache/php/mysql.  I was recently told by the it department here at my university, where i work, that the are changing some networks around and my formerly dynamically assigned static ip address was now going to be fully static.  so i made the changes in /etc/network/interfaces and restarted my networking and all was dandy.  However about an hour later i got a call back that i was still requesting a dhcp address from them.  I cannot find any way that the server is doing this.  Any help would be great

Thanks

I think "/etc/init.d/networking restart" might not always kill the dhcp client. Either reboot the server, or try running
```

sudo killall dhclient3

```
or this if that doesn't work
```

sudo lsof -n -i :bootpc

```

---

### Post by alastair on 2008-10-07
Also, networking is set up via the file :

/etc/network/interfaces

and a "static" IP will include the word "static". Worth a look perhaps.

Alastair

---

