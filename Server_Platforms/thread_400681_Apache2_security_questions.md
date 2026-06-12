---
title: "Apache2 security questions"
date: 2007-04-03
forum: Server Platforms
---

### Post by HeyItsMatt on 2007-04-03
Hey everyone.  I want to set up an Apache webserver so that I can try to learn some PHP and play with MySQL.  I installed the Ubuntu desktop edition as opposed to the server edition, since I am new to Ubuntu and was a little wary of a non-GUI server environment.  

Question 1 - if I am adding 127.0.0.1:80 in the Apache ports.conf file, this means that the webserver can only be accessed from the machine on which it is running, and I do not have to worry about other security measures (other than people physically accessing my machine), right?  Basically I want to use the webserver for testing, but not have it be accessible from the internet.

Question 2 - If I have a firewall up with restricted inbound connections, does this mean that people cannot access my webserver even if I have port 80 open on outbound connections (in order to surf the web)?.  I.E. since an incoming request on port 80 would not be something initiated by myself, it would be blocked?  Perhaps this is redundant anyways if my first question is correct.

Question 3 - Assuming that I wanted to open the webserver to the internet at some point, is there some newbie-friendly resource that explains how to configure MySQL / PHP / Apache to be as secure as possible?  I've looked around a bit but a lot of stuff seems geared towards the Ubuntu server edition (maybe I should just follow pretty much the same suggestions?) and are not very informative in terms of explaining to a newbie what each step is doing.  I'm wondering if I should even attempt to set up an internet-available webserver on Linux, or if this is really something for a professional/computer expert to do.

Question 4 - I am behind a D-LINK DI-624 router, and I noticed that after it made a DHCP request to my computer to give it a new IP address (it did this after a power outage, I had to restart everything) it no longer recognizes my computer's hostname ("unknown") even though it still gave it a new IP address and lists it in the DHCP section of the router.  Is there something about Ubuntu where the router isn't getting the hostname?  I am able to get the actual hostname using the "hostname" command in the terminal.  Unrelated to LAMP servers, I know, but I seems like I shouldn't start another thread just for that.

Thank you for reading my long-winded post.

---

### Post by dfreer on 2007-04-03
Question 1 - If your server is behind a firewall (all home routers should have one), and you haven't opened port 80 on the firewall, you should be fine. But this works just as well too.

Question 2 - You shouldn't have to open port 80 to surf the web. Basically, your firewall should be set up so that everything coming out of your laptop is free to pass through, while anything coming in is denied (unless it is a response to something you initiated). So all incoming connections from the internet, unless you are running another service, should be blocked by your firewall.

Question 3 - Can't help you here, sorry :)

Question 4 - It seems like most of my routers do not play nice with my ubuntu boxes, to the point that I have to specify the name of my computers in each of my /etc/hosts file just to be able to ping/ssh by hostname and not by IP.

---

### Post by HeyItsMatt on 2007-04-03
Hey, thanks for the answers dfreer.

> **dfreer said:**
> 
Question 2 - You shouldn't have to open port 80 to surf the web. Basically, your firewall should be set up so that everything coming out of your laptop is free to pass through, while anything coming in is denied (unless it is a response to something you initiated). So all incoming connections from the internet, unless you are running another service, should be blocked by your firewall.


Yeah, I forgot to mention I have outbound security set on restrictive and just have rules manually set up for the general services I use (on the off chance I somehow get a naughty program on my comp I guess).  Perhaps fairly unnecessary but I guess I'm just paranoid :)

---

### Post by Frosty Cold Drink on 2007-04-03
> **HeyItsMatt said:**
> Question 1 - if I am adding 127.0.0.1:80 in the Apache ports.conf file, this means that the webserver can only be accessed from the machine on which it is running, and I do not have to worry about other security measures (other than people physically accessing my machine), right?  Basically I want to use the webserver for testing, but not have it be accessible from the internet.[/qutote]
Yes and No. Other computers can't establish direct connections, however active attacks will be scaffolded. Casually, you won't need to worry, but don't put your taxes up there assuming you are safe. (But you wouldn't do that anyway, right?)

> Question 2 - If I have a firewall up with restricted inbound connections, does this mean that people cannot access my webserver even if I have port 80 open on outbound connections (in order to surf the web)?.  I.E. since an incoming request on port 80 would not be something initiated by myself, it would be blocked?  Perhaps this is redundant anyways if my first question is correct.
Yes. Make sure your rules are interface specific, as you can have your firewall set to deny yourself access! Generally speaking, I don't like firewalls. They are used to band-aid far to often. If you need a firewall, something else is wrong. That said, there is nothing wrong with insurance.

[quote]Question 3 - Assuming that I wanted to open the webserver to the internet at some point, is there some newbie-friendly resource that explains how to configure MySQL / PHP / Apache to be as secure as possible?  I've looked around a bit but a lot of stuff seems geared towards the Ubuntu server edition (maybe I should just follow pretty much the same suggestions?) and are not very informative in terms of explaining to a newbie what each step is doing.  I'm wondering if I should even attempt to set up an internet-available webserver on Linux, or if this is really something for a professional/computer expert to do.
There are far too many tips and guides out there. Just dive in. Generally, your normal security rules apply. Turn off what you don't need (modules, configuration options), DISABLE CONFIGURATION OVERRIDES in per-directory configuration files (.htaccess by default) that you don't need, use suexec and suphp if you can, don't run your daemons as root, and PHP safe mode can be a good thing.

> Question 4 - I am behind a D-LINK DI-624 router, and I noticed that after it made a DHCP request to my computer to give it a new IP address (it did this after a power outage, I had to restart everything) it no longer recognizes my computer's hostname ("unknown") even though it still gave it a new IP address and lists it in the DHCP section of the router.  Is there something about Ubuntu where the router isn't getting the hostname?  I am able to get the actual hostname using the "hostname" command in the terminal.  Unrelated to LAMP servers, I know, but I seems like I shouldn't start another thread just for that.
I don't know how the router is getting the hostname, but typically they can be given in the DHCP requests. No idea if ubuntu configs are telling dhclient to do this or not.

> Thank you for reading my long-winded post.
Eh.

---

