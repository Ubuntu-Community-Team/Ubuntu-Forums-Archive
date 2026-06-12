---
title: "Cant access my webpage from within network"
date: 2009-04-05
forum: Server Platforms
---

### Post by bilbo0a on 2009-04-05
I am a new to linux.
I setup Ubuntu server 8.10 on a decicated machine running only this OS.
Network seems to work ok as i can install updates and run it remotly via putty
I only changed the listen port to 8000.
Sever is starting up well 
Now i tried from another computer in my network to access the apache server home page (the basic page provided by apache server)
i use IpAdressOfSever:8000 in my Browser but i cant connect.
any ideas what else to check
Appreciate your input.

---

### Post by majamba on 2009-04-05
you want be able to acess that webpage from any other computer than the one is installed
you have to setup different things on apache if you want to acess it from the network

you will probably need a domain name and other stuff too which i can't remember

---

### Post by dresdn on 2009-04-05
> I only changed the listen port to 8000.

What exactly did you change?  To have Apache listen on port 8000, you need to change 

```

Listen 80

```

```

Listen 8000

```

in /etc/apache2/ports.conf

If you did do all this and it's not working, ensure that it's listening on all ports.

Run the following from the server CLI and see if you can connect:

```

telnet localhost 8000

telnet ipAddressOfServer 8000

```

-Mike

---

### Post by arsnova on 2009-04-06
Also, if you're behind a router's firewall, make sure to set up the router's port forwarding for 8000, and have it point to the Linux box (set up with a static IP).

Apache needs to be restarted for the new port to stick:

```
/etc/init.d/apache2 restart
```

Hope this helps...

---

### Post by bilbo0a on 2009-04-06
Thanks all for your comments.
I have changed the ports.conf file correctly with 
listen 8000

i have forwared the port from the router to the ip of my linux webserver but i thought this is irrelevant as i am accessing the web page from within my network directly via the ip of the linux webserver.

One thing to note is that my linux webserver does not use a static ip , but i let him get his ip from the router, could this cause this issue?

Regards

---

