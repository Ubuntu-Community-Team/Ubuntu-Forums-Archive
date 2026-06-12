---
title: "how do i allow outside connections to my localhost domain?"
date: 2007-07-13
forum: Server Platforms
---

### Post by jammodotnet on 2007-07-13
So for the past few weeks, I've been working on a few developmental websites.

I've learned to make a few virtual hosts, whereas:
[www.jammo.net](www.jammo.net) = my main live/public site.
[www.jammo.dev](www.jammo.dev) = my tester localhost/private site.

How would I set up my system to allow connections from the outside world to test my localhost site??
I'd also have to consider security and such matters, as I don't want to compromise my Ubuntu installation.

NOTE: although I've accomplished a ton of KnowHow using Ubuntu, I'm still a newbie. I don't do enough tinkering with via command line, etc. So please keep my newbish skills in mind if you are able to guide me. :) :(

---

### Post by Mr. C. on 2007-07-13
Have you created A records for your hosts at your DNS server's site ?

Do you have a router, or are you using iptables on Ubuntu ?  Either way, you need to open inbound port 80 TCP and forward it to the host where your apache server is running.

MrC

---

### Post by Footballkid4 on 2007-07-13
Well, both of those are running on one server (since you said you're using VirtualHosts), which means that port 80 is already open.  Can you possibly show is the VirtualHost directive for your development site (stripping out anything which may be a security risk, of course)

---

### Post by Mr. C. on 2007-07-13
> **Footballkid4 said:**
> Well, both of those are running on one server (since you said you're using VirtualHosts), which means that port 80 is already open.  Can you possibly show is the VirtualHost directive for your development site (stripping out anything which may be a security risk, of course)

You're comparing apples and oranges.  Don't confuse "open" with "listening".  A firewall can block incoming connections to a server listening on a port.  And opening a port via firewall does not imply a service is listening on the same port.

MrC

---

### Post by jammodotnet on 2007-07-14
> **jammodotnet said:**
> NOTE: although I've accomplished a ton of KnowHow using Ubuntu, I'm still a newbie. I don't do enough tinkering with via command line, etc. So please keep my newbish skills in mind if you are able to guide me. :) :(

:(

> **Mr. C. said:**
> Have you created A records for your hosts at your DNS server's site?
No. I don't know how.

> **Mr. C. said:**
> Do you have a router, or are you using iptables on Ubuntu ?  Either way, you need to open inbound port 80 TCP and forward it to the host where your apache server is running.
My Internet connection if via Time Warner Cable (ie: cable internet), so I have a router.

How would I open that port?
When you mention '*forward it to the host where your apache server is running*", you mean, localhost, right?

> **Footballkid4 said:**
> Well, both of those are running on one server (since you said you're using VirtualHosts), which means that port 80 is already open.  Can you possibly show is the VirtualHost directive for your development site (stripping out anything which may be a security risk, of course)

you mean this:```
sudo gphpedit /etc/hosts
```???
```
127.0.0.1 localhost jammo-desktop jammo.dev
127.0.1.1 jammo-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

or this```
sudo gphpedit /etc/apache2/sites-enabled/default
```
```
NameVirtualHost *
<VirtualHost *>
ServerName jammo.dev
DocumentRoot /home/jammo/public_html/jammo.dev
</VirtualHost>
```

---

### Post by primski on 2007-07-14
just a quick thought before it gets misleading:
 
you cannot have domain [www.jammo.dev](www.jammo.dev)  accessible from the 'outside', simply because .dev is not a registered extension, therefore you cannot have it on the internet.

The .net version, you need to have registered domain and have a dns record point to your server. Have you bought  this domain?

---

### Post by jammodotnet on 2007-07-14
> **primski said:**
> just a quick thought before it gets misleading:
 
you cannot have domain [www.jammo.dev](www.jammo.dev)  accessible from the 'outside', simply because .dev is not a registered extension, therefore you cannot have it on the internet.

The .net version, you need to have registered domain and have a dns record point to your server. Have you bought  this domain?
Yes, I do own the domain [www.jammo.net](www.jammo.net)
However, I do not require that the .dev account be accessible 24/7. Only briefly as I continue to develop the site.

I was underthe impression that I could just link someone to my pc via the IP address?
If the only available method is for me to have a domain pointing to my PC, then I suppose I can purchase a new name for the sake of development. :)
But I'd still rather just use my IP address, if at all possible?!

---

### Post by Mr. C. on 2007-07-14
jammodotnet,

You need to focus and prioritize your goals - you're trying to do too many things that you do not understand.

1) Get your website functional.
2) Configure it to be a name-base virtual host.
3) Edit your /etc/hosts such that the hostname you use in ServerName is present in the /etc/hosts file, as:
```

127.0.0.1   localhost
...
127.0.0.1   ServerName           # production server, www.jammo.net
127.0.0.1   ServerName           # development server, www.jammo.dev

```
This will allow you to start testing your server internally.

4) When you are ready to go live, you need to go to your DNS registrar's web site, and configure an A record for [www.jammo.net](www.jammo.net) which points to your public IP address.  DNS indicates that there is an A record already:

jammo.net.              3589    IN      A       66.246.128.98

however, we cannot know if this is your IP address, or a placeholder.  It appears to have in index.html file, and it looks like your contents.

You cannot do this for the .dev server, because .dev is not a valid top level domain (as indicated by primski earlier).
5) Create a port 80 forward on your firewall to the LAN IP address of your web server.
6) Test your server from some remote network, to see if it works correctly remotely.

MrC

---

