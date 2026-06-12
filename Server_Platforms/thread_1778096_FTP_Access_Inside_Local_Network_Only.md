---
title: "FTP Access Inside Local Network Only?"
date: 2011-06-08
forum: Server Platforms
---

### Post by CGW on 2011-06-08
Hello all:

I've been researching this all day with no luck thus far.  Basically I need to cutoff port 21/ftp access from IP addresses outside of my local network.  My local IP range is something like 192.168.0.100 - 192.168.0.150 -- so anything outside of this range would automatically be blocked.

Any IP address outside of this range would be denied as I use SFTP for remote access, etc. from home, etc.

I've researched IP tables, tcp wrappers, etc. but am still unsure which would be best for what is probably a simple fix.

Thanks in advance.

Chris

Relevant info:  Vsftpd via Ubuntu Server 10.10

---

### Post by ruffEdgz on 2011-06-08
After looking over the vsftpd.conf manpage, I don't see anything that could help with placing an IP range. 

You could just use the variable 'listen_address' to only listen to your private network.

```

listen_address:
If vsftpd is in standalone mode, the default listen address (of all local interfaces) may be overridden by this setting. Provide a numeric IP address.

```

But the idea of doing it with iptables could work as well.

---

### Post by CGW on 2011-06-08
I've considered iptables, but am unsure as to how to set them up for this type of application.  I've been Googling it but haven't found any examples to work from.

---

### Post by ruffEdgz on 2011-06-09
Ok, so I hope this can help you and there might be more to add to your iptables but lets get you going with some basic appends:
```

sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables  -A INPUT -p tcp -m state --state NEW,ESTABLISHED -m tcp --dport 22 -j ACCEPT

```
This will help if you need SSH connections to your computer in question but if you do have a way to physically get to the computer, that will help if any problems to come about and you can't ssh for some reason.

Now lets see if we can get the accepting rule for port 21 on your private network:
```

sudo iptables -A INPUT --src 192.168.0.0/24 -p tcp --dport 21 -j ACCEPT

```
This will only let those in your private network using port 21 only.
Now that we accepted your network, lets reject anyone else:
```

sudo iptables -A INPUT -j DROP

or

sudo iptables -A INPUT ! --src 192.168.0.0/24 -p tcp --dport 21 -j DROP

```
**The first option** will drop the request if it isn't accepted in any of the rules above. **The second option **will only drop requests that are not from 192.168.0.0/24 and trying to use destination port 21. Either one should work.

So now that we have all the rules in place this is what it should look like after appending them together:
```

sudo iptables -L INPUT

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            state NEW,ESTABLISHED tcp dpt:ssh
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:ftp 
DROP       tcp  -- !192.168.0.0/24       anywhere            tcp dpt:ftp 
or
DROP       all  --  anywhere             anywhere

```
Let me know if there is anything else you would like to know or if there is anything else that needs to be done.

Cheers!

---

### Post by chazz_tsc on 2011-06-09
I would suggest using the less restrictive form of the iptables command, ```
sudo iptables -A INPUT ! --src 192.168.0.0/24 -p tcp --dport 21 -j DROP
``` if you want to leave any other ports open on your machine. If you drop everything except ports 21 and 22, you can serve SSH and FTP, but nothing else whatsoever.

---

### Post by CGW on 2011-06-09
Thanks...that was similar to what I was attempting but I wasn't having any luck.

HOWEVER, here's the funny thing.  I have port 21 closed on my router.  If I try to access the server's ftp from somewhere other than my network it times out saying the host is unavailable.  But if I try to access the ftp server from inside the network it connects fine despite the fact that the router isn't forwarding port 21.  Is this normal?  And is it still safe from the outside?

---

### Post by ruffEdgz on 2011-06-09
Well it sounds like you just have your router handling the firewall requests instead of the server. If that is the case, you should be able to set it up with similar rules if you want.
> 
HOWEVER, here's the funny thing. I have port 21 closed on my router. If I try to access the server's ftp from somewhere other than my network it times out saying the host is unavailable. But if I try to access the ftp server from inside the network it connects fine despite the fact that the router isn't forwarding port 21. Is this normal? And is it still safe from the outside?

Sounds like to me that its working the way you want it. I am getting from your comment:
[list]
[*]When inside your network and on another computer, you can get to server through port 21
[*]When you are away from your network, any connection attempts timeout and say they are unreachable
[/list]
Sounds like you have done it ;)

Use this tool anytime to see which ports are open from the outside: [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)

If you also want, give use some info about your router, firmware and a screenshot of how you are handling the firewall/port forwarding if you would like to know more from your routers standpoint.

---

### Post by CGW on 2011-06-09
I'm running a Linksys WRT54G with firmware v1.02.8.  The only port settings I have are the following:

[IMG]http://img29.imageshack.us/img29/8260/23161636.png[/IMG]

Otherwise, I have no port/ip settings in either the router or the server.  Somehow, all is well.  I can access the ftp server from inside the network just fine, while it seems no one outside the network can see it or access it.

---

### Post by chazz_tsc on 2011-06-09
> **CGW said:**
> I have port 21 closed on my router.  If I try to access the server's ftp from somewhere other than my network it times out saying the host is unavailable.  But if I try to access the ftp server from inside the network it connects fine despite the fact that the router isn't forwarding port 21.  Is this normal?  And is it still safe from the outside?

Yes, it is normal; your router usually controls routes from one side (the Internet) to the other (your home net) and vice versa, but does not control routes within your home network. Most home routers have 4 or 5 ports on a switch on the inside, and things happening within your home network only go through the switch, never touching the router at all.

Edit, now that I have seen your latest post: With the WRT routers, there is often also a setting for "virtual server". In this case, it would be a Virtual FTP Server that you would have to point at the Ubuntu box if you wanted FTP from outside.

---

### Post by ruffEdgz on 2011-06-09
> **chazz_tsc said:**
> Yes, it is normal; your router usually controls routes from one side (the Internet) to the other (your home net) and vice versa, but does not control routes within your home network. Most home routers have 4 or 5 ports on a switch on the inside, and things happening within your home network only go through the switch, never touching the router at all.

Edit, now that I have seen your latest post: With the WRT routers, there is often also a setting for "virtual server". In this case, it would be a Virtual FTP Server that you would have to point at the Ubuntu box if you wanted FTP from outside.

+1 on this one. The router will only handle the port forwarding coming from the WAN to your local network. Your local network will be able to see and communicate to each other just fine.

Glad everything is working the way you need it to. Cheers!

---

### Post by CGW on 2011-06-09
Thanks guys.  Nothing like wasting time to find out I was trying to reinvent the wheel.

Thanks again!!

---

