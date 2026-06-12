---
title: "Firefox"
date: 2010-04-24
forum: Security
---

### Post by ubuchignome on 2010-04-24
What ports does Firefox use to connect to the Internet?

---

### Post by yabbadabbadont on 2010-04-24
It would depend upon which protocol was being used.  Normally it would be port 80, http.

---

### Post by Bachstelze on 2010-04-24
> **yabbadabbadont said:**
> It would depend upon which protocol was being used.  Normally it would be port 80, http.

No, port 80 is used by web servers, not clients. Clients usually use a random high port for connecting to server.

@OP: You can use the [font=monospace]netstat[/font] command (the "Foreign address" field should show port 80).

---

### Post by rookcifer on 2010-04-24
As the guy above said, Firefox typically uses a random high numbered port.  I have noticed it is almost always between 30000-60000.

---

### Post by ubuchignome on 2010-04-24
I am trying to set the firewall to allow it out, but I believe it keeps switching ports as a security measure. So, how can I let it out past the wall? Humm.

---

### Post by mmalone21 on 2010-04-24
> **ubuchignome said:**
> What ports does Firefox use to connect to the Internet?

HTTP: 80
SSL: 443 for the most part but it really depends on the proxy server give me more details.

---

### Post by Bachstelze on 2010-04-24
> **mmalone21 said:**
> HTTP: 80
SSL: 443 for the most part but it really depends on the proxy server give me more details.

No.

---

### Post by mmalone21 on 2010-04-25
> **Bachstelze said:**
> No.

[http://support.mozilla.com/en-US/kb/Error+loading+web+sites](http://support.mozilla.com/en-US/kb/Error+loading+web+sites)

I always heard the French were rude. See link above that is where my info came from I am wondering what Ports Firefox uses in France. Perhaps you could enlighten us.

---

### Post by mmalone21 on 2010-04-25
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by lovinglinux on 2010-04-25
On most systems, there is not a good reason to block outgoing connections. If you do so, then you need to create a rule in iptables to allow any outgoing connections on destination port 80, like this:

```
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -j ACCEPT
```

You will need to create rules for other destination port as well, depending on which type of services do you use. For instance, you will need to allow destination port 443 for https connections, 21 for FTP, 993 for IMAP and so on. Anyway, too much trouble for virtually no benefit.

What application you are using to create the firewall rules?

---

### Post by cariboo on 2010-04-25
> **mmalone21 said:**
> [http://support.mozilla.com/en-US/kb/Error+loading+web+sites](http://support.mozilla.com/en-US/kb/Error+loading+web+sites)

I always heard the French were rude. See link above that is where my info came from I am wondering what Ports Firefox uses in France. Perhaps you could enlighten us.

It doesn't say anywhere on that page that firefox uses port 80 for an outgoing connection. Apache listens on port 80 and 443, maybe that is where the confusion is.

---

### Post by lovinglinux on 2010-04-25
> **mmalone21 said:**
> [http://support.mozilla.com/en-US/kb/Error+loading+web+sites](http://support.mozilla.com/en-US/kb/Error+loading+web+sites)

I always heard the French were rude. See link above that is where my info came from I am wondering what Ports Firefox uses in France. Perhaps you could enlighten us.

Any connection has a source port and a destination port. When Firefox tries to connect to a web site it uses a random port as source, which means the port the connection is using to leave your machine, and usually use port 80 as destination, which is the default port used by web servers to allow browsers to enter and retrieve the web site content.

Since source (outgoing) ports are random, the only way to selective allow the outgoing connection is to allow the destination port instead of the source port.

See my previous post.

---

### Post by ubuchignome on 2010-04-25
The ports Firefox uses leaving the machine are definitely random, between 3000 and 6000. The ports it connects to are 80. I can track that in the Firewall. But how can you configure the leaving port when it changes every time. Maybe by entering a port range leaving and destination port 80? IDK still trying.
Thanks for all the feedback. Be well! and polite :)

---

### Post by lovinglinux on 2010-04-25
> **ubuchignome said:**
> But how can you configure the leaving port when it changes every time. 

You don't. That's the point. Instead you allow the destination port 80, so any outgoing connection using whatever random source port and port 80 as destination will be allowed.

Please answer these questions so I can help you more efficiently:

What interface you are using to configure your firewall?

Why do you feel the need to block outgoing connections? 

Are you sure you need a firewall? Please describe why you need it.

---

### Post by ubuchignome on 2010-04-25
> **lovinglinux said:**
> You don't. That's the point. Instead you allow the destination port 80, so any outgoing connection using whatever random source port and port 80 as destination will be allowed.

Please answer these questions so I can help you more efficiently:

What interface you are using to configure your firewall?

Why do you feel the need to block outgoing connections? 

Are you sure you need a firewall? Please describe why you need it.
[COLOR=black][FONT=Verdana]Thanks. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. I am using GUFW to configure the firewall.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2. I want to control and log the outgoing connections to assure that nothing is initiating from internal ports. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]3. And I think that every computer with an internet connection must have a firewall running these days.[/FONT][/COLOR]

---

### Post by lovinglinux on 2010-04-25
> **ubuchignome said:**
> [COLOR=black][FONT=Verdana]1. I am using GUFW to configure the firewall.[/FONT][/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154299&stc=1&d=1272205862[/IMG]

> **ubuchignome said:**
> [COLOR=black][FONT=Verdana]3. And I think that every computer with an internet connection must have a firewall running these days.[/FONT][/COLOR]

No they don't. If you don't have any server running, then all ports are closed and all unrequested connection attempts from outside will be rejected, even if you let your machine wide open. If you have a server, then you probably need to allow the traffic to go through, so a firewall would be blocking ports that are already closed and allowing traffic to the only ports that are indeed open. A firewall is useful when you want to limit who can access the server. For example, I have one machine in my local network that runs a ssh server. I don't want to allow anyone from outside my local network to reach the ssh port, but I want to access it from another machine in my LAN, so I can configure the firewall to allow only internal IP addresses on the ssh port.

Additionally, if you have a router, then all unrequested traffic will be rejected anyway, unless you forward the port on the router.

BTW, monitoring traffic on a daily basis because you are afraid someone might crack your machine is a waste of time.

Read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812) tutorial.

---

### Post by ubuchignome on 2010-04-25
Thanks much for your input and time.
 
Be Well.

---

