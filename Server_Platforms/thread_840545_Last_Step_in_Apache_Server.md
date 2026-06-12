---
title: "Last Step in Apache Server"
date: 2008-06-25
forum: Server Platforms
---

### Post by Wangsta on 2008-06-25
Here is my situation: I have Apache and everything nicely installed on my Linux box. I've been running it only on my computer, not the web, testing out PHP and Mysql etc. I haven't changed much of the default settings and now I want to host it to the web.
I'm also getting my internet through a router, btw.
I also have a SSH server which I have successfully accessed from computers not in my network. The linux box has a static IP and everything too. So I go to my external IP address, and it gives me the router setup.
I go down and turn on the port forwarding that forwards port 80 to the linux box's static ip, right underneath where I did it for the SSH. I save the settings, but when I go to my external ip again, instead of seeing my site-- or the router setup again, for that matter-- it just goes into an infinite loading sequence. It never loads anything.

I tried accessing it through a proxy and it still didn't work. How do I get my Apache to the outside world?

If it helps, I got this when I forgot to use sudo: 
```

bleh bleh@server:~$ /etc/init.d/apache2 force-reload
open: Permission denied
 * Reloading web server config apache2                                          httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied
```

---

### Post by cariboo on 2008-06-25
Your ISP may be blocking port 80, try a different port eg: 8080.

Jim

---

### Post by unixbills on 2008-06-25
How are you checking on the local host with "localhost" or the IP address?  Try the IP?  It probably doesn't work either when set to the IP.  Check your /etc/apache2/apache2.conf and conf.d files.  What is allowed?  I think default is "localhost" only.  Change "Allow from localhost" to "Allow from all".

---

### Post by Wangsta on 2008-06-25
Typing in localhost works, but with the external IP address, when i'm not port-forwarding, it just displays the router setup, as if I typed 192.168.1.1

I can't find your "allow from localhost' anywhere, so I've hosted a file containing my apache2.conf and my site's configuration file together.

And how do I switch to a different port??

---

### Post by Martyn Thompson on 2008-06-25
Hi Wangsta,

This sounds very similar to the setup I have at home - I can access the 'local' site by typing in the local IP address (i.e. the one within your network). 

However if you go to a networked PC outside of your network (I use ones at work to test my systems) you can use your domain name (if forwarding is set up) or if not, the WAN IP address of the router. 

Let us know how you get on.

---

### Post by Wangsta on 2008-06-25
When I turned the port-forwarding on again, my friends couldn't see it either, the connection just timed out.
I tried changing ports by only going into my /etc/apache2/ports.conf and changed it to Listen 8080. I force-reloaded and restarted and changed the forwarded port to 8080.
This time there was no infinite loading sequence, it just went back to the router setup. :(

How come changing the port did this? How do you change the port the right way and still get it to show up on a web page?

---

