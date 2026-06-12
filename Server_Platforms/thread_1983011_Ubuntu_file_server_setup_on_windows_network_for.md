---
title: "Ubuntu file server setup on windows network for"
date: 2012-05-19
forum: Server Platforms
---

### Post by jtirrell1 on 2012-05-19
Hey all,
 
I'm trying to set up a file server using Ubuntu 12.04 Server Edition at my work (mostly Windows comupters). 
 
I've done some research on using samba to do this, but it seems like I would have to manually add the server to network places on each Windows computer.  This is a problem, since we are a computer repair shop; computers will be connected to the network briefly while they're being repaired, and then never again.  It would be a hassle if we have to connect to the server manually every time.
 
I know that Windows is able to see all other windows computers on its local network.  Can I set up ubuntu so that all windows computers will see it automatically?
 
Assume that I will be using a dynamic IP.
 
Sorry if the post is confusing, but thanks for your help.

---

### Post by papibe on 2012-05-19
Hi jtirrell1.

Windows computers should be able to see the server if:
[LIST]
[*]The server is in the same LAN as they are (same IP addresses subset).
[*]Samba it is installed and running.
[*]The server belongs to the same workgroup as they belong.
[/LIST]
The only exception would be when you use the typical settings for exporting [homes], since they are hidden by default. However, that can be configured differently.

Just some thoughts.
Regards.

---

### Post by redmk2 on 2012-05-19
> **jtirrell1 said:**
> Hey all,
 
I'm trying to set up a file server using Ubuntu 12.04 Server Edition at my work (mostly Windows comupters). 
 
I've done some research on using samba to do this, but it seems like I would have to manually add the server to network places on each Windows computer.  This is a problem, since we are a computer repair shop; computers will be connected to the network briefly while they're being repaired, and then never again.  It would be a hassle if we have to connect to the server manually every time.
 
I know that Windows is able to see all other windows computers on its local network.  Can I set up ubuntu so that all windows computers will see it automatically?
 
Assume that I will be using a dynamic IP.
 
Sorry if the post is confusing, but thanks for your help.

The only line you need to change for the Samba server to be seen starts with ```
**[COLOR="Red"];[/COLOR]**	name resolve order
```

I think you should fine this line commented out in the [global] section of the /etc/samba/smb,conf file.  Uncomment the line and add add bcast just to the right if the = sign like this```
	name resolve order = *[COLOR="Blue"]bcast[/COLOR]* 
``` 

This will force the server to broadcast its presence on the local subnet.  In windows speak this is called a B-node.  You shuld see the server when browsing network neighborhood.

Setting the shares to be accessible is like it always is.  I would allow the shares to be available to all (guest=ok).

 @papibe you should be able to use as many workgroups as you like.  These to not restrict a user from seeing the server or accessing all available shares.

---

### Post by LHammonds on 2012-05-20
> **jtirrell1 said:**
>  It would be a hassle if we have to connect to the server manually every time.
 
Are saying it is too much of a hassle to click Start, Run and type **\\192.168.1.2\share**?

---

