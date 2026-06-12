---
title: "Can't ping from the server 10.04.3 by ip?"
date: 2012-01-09
forum: Server Platforms
---

### Post by Jim.Armstrong on 2012-01-09
I've just installed 10.04.3 server and I've added the DNS package this box is in beta.
It's not attached to the production network yet. I've got the server attached to a 16 port Netgear switch along with a laptop that's running XP.

I can ping from the laptop to the server but I can't ping from the server to XP.  The cursor just sits there flashing until I hit ctrl c.

From the server I can ping localhost it returns 127.0.0.1 like it should, and I can ping 172.16.17.254 that's assigned to eth0.

I'm pinging by ip only.

The server ip addy 172.16.17.254, mask 255.255.252.0, gateway 172.16.17.254.
XP ip addy 172.16.17.183, mask 255.255.252.0, gateway 172.16.17.254.

I'm asking if there is some setting or app like apparmor that I need to modify to make this work?  It seems like when I ping XP the request is sent, but the reply is blocked by the server.

If you need additonal info let me know.

---

### Post by Jim.Armstrong on 2012-01-09
I've got something in the routing hosed up.  I put the box in the production network and I can ping from the server to the XP laptop.

---

### Post by jonobr on 2012-01-09
hello


I may be missing something here, 

If your just using a switch, then remove the gateway IP address from your server as its set to the same as the IP.(not sure if thats a typo)
In a switched network and in your preliminary testing you wont need to route to the gateway

The bigger problem though, 
Looking at your netmask , the server IP address is in the 172.16.17.252 network with the usable addresses
172.16.17.253 - 172.16.17.254


Your XP is in a different subnet.

Im figuring if you were to change it to 172.16.17.253  this could work.
The fact it working one way is probably becuase there may be a mac entry for one device already on the switch or in XP

This all assumes a flat uninteresting switch thats not doing anything fancy, but if you were setup using vlans, thats a horse of a different colour.

Mind you you would still need a router on a stick for that, Im not sure if the netgear can do it

---

### Post by jonobr on 2012-01-09
Hello

Missed your post

> I've got something in the routing hosed up. I put the box in the production network and I can ping from the server to the XP laptop.

This could be explained by the production network allowing and recognizing vlans.
When you move it, its in the correct vlans and routes accordingly but if you move to a private network,  your switch probably doesnt have vlans operational to route the traffic

---

### Post by jonobr on 2012-01-10
Hey


Any joy??

Cheers

Jonobr

---

### Post by Jim.Armstrong on 2012-01-19
sorry for the delay in replying. small shop, wear many hats been being beaten by a different stick.

i just gave up on it once i moved it into production and it pinged both ways.

currently being aggravated with a logging problem. it's not writing to the dns log file i have set up.  works on the old box, so i set it up the same way on this new box.  i'm reading the documentation, searching the forum, etc.  i'll be posting up a new question about it most likely.

thanks for getting back to me.

---

### Post by jonobr on 2012-01-19
Ok

Thanks for the feedback

Cheers

Jonobr

PS- When upgrading, always a good idea to hold onto config files etc.
I reckon from you other post (upgrading bind) you had logging and then it was overwritten in a new cfg.
Thats why its always good to have those old configs in your back pocket.

Mind you, Im sure really annoyed at me now, Monday morning quarterbacking something that's already done:-)

---

### Post by Jim.Armstrong on 2012-01-22
> **jonobr said:**
> Ok

Thanks for the feedback

Cheers

Jonobr

PS- When upgrading, always a good idea to hold onto config files etc.
I reckon from you other post (upgrading bind) you had logging and then it was overwritten in a new cfg.
Thats why its always good to have those old configs in your back pocket.

Mind you, Im sure really annoyed at me now, Monday morning quarterbacking something that's already done:-)

Logging turned out to be an apparmor permissions thing, I didn't have write enabled.  I found the solution in the documentation. But after looking at the apparmor config file I found a stanza at the end of it that had the line /var/log/named so I changed my named.conf.local file from /var/log/bind to /var/log/named and copied the files into it.  Logging is working the way I expect it to, and I can use tail -f to check it out in real time.

I do save my old config files. Matter a fact I renamed the originals and then sftp'd the  named.conf.local and named.conf.options on to the new box.  The named.conf.default-zones file was new to me.  Once I had a look at it I just left it alone.  Thanks for the tips though every little bit helps.

---

