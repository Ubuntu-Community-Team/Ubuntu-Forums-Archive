---
title: "Help on setting up samba file server for windows"
date: 2011-03-14
forum: Server Platforms
---

### Post by 4eva on 2011-03-14
Hi,

I follow the guide from [http://www.brighthub.com/computing/linux/articles/23332.aspx](http://www.brighthub.com/computing/linux/articles/23332.aspx) and [http://www.brighthub.com/computing/linux/articles/37777.aspx](http://www.brighthub.com/computing/linux/articles/37777.aspx). I can't seem to connect to it when using windows 7.

Both are in the same workgroup (W0RKGR0UP) and I have set DHCP address for the ubuntu box.

Is there any other thing that I would still need to edit ? My router address is 192.168.0.1 and the fixed ip for ubuntu box is 192.168.0.103.

Much appreciated for any of the help :popcorn:

---

### Post by pricetech on 2011-03-14
How did you configure your Samba server ??

How are you trying to connect ??

---

### Post by 4eva on 2011-03-14
> **pricetech said:**
> How did you configure your Samba server ??

How are you trying to connect ??

I tried using the 2 guides above... Probably map as a network drive. :confused:

---

### Post by HermanAB on 2011-03-15
Howdy,

So, you got it installed and it doesn't work? You are nearly there...

Here is a Samba debug guide:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by 4eva on 2011-03-15
> **HermanAB said:**
> Howdy,

So, you got it installed and it doesn't work? You are nearly there...

Here is a Samba debug guide:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

Thanks I got it working :D 

The problem was with my windows 7 network card, I accidentally switch off client for Microsoft network & file and printer sharing.

Now I need to secure my server ! :popcorn: Tips would be good.

How do I allow a only specific pc to access a folder while denying all others ?

I tried adding this to smb.conf but did not work.

> hosts allow = 192.168.0.101/24
hosts deny = 0.0.0.0/0The other pc with lan ip of 192.168.0.102 were still able to access it.

---

