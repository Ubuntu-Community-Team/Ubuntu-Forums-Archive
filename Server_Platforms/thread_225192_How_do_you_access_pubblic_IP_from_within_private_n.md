---
title: "How do you access pubblic IP from within private network?"
date: 2006-07-29
forum: Server Platforms
---

### Post by zasf on 2006-07-29
Hi,

I have a small home network, composed by a Netgear DG834G router (192.168.1.1), a Ubuntu server (192.168.1.99) and my laptop (192.168.1.5). I use dyndns so that I can access my server (ftp, http, proxy) from outside the local network and it works very well using port forwarding to the server.

I'd like to be able to access my server using myname.homeunix.net **from within my private network** also, **not ** using local ip address (192.168.1.99). Is that possible? Currently my router forwards requests to my server only if they come from outside network and I couldn't find any settings in the configuration interface.

Thanks

---

### Post by Ares Drake on 2006-07-29
> **zasf said:**
> Hi,

I have a small home network, composed by a Netgear DG834G router (192.168.1.1), a Ubuntu server (192.168.1.99) and my laptop (192.168.1.5). I use dyndns so that I can access my server (ftp, http, proxy) from outside the local network and it works very well using port forwarding to the server.

I'd like to be able to access my server using myname.homeunix.net **from within my private network** also, **not ** using local ip address (192.168.1.99). Is that possible? Currently my router forwards requests to my server only if they come from outside network and I couldn't find any settings in the configuration interface.

Thanks

I suppose it is not possible. The problem is your router - most routers for home or small office usage can't resolve their own adress. So it is impossible to acces your own extern adress myname.homeunix.net from within your network the way you want it.

---

### Post by fdoving on 2006-07-29
I suggest adding myname.homeunix.net to /etc/hosts with a line like this:
```

192.168.1.99 myname.homeunix.net 

```

That is on the clients.

I don't understand why you would want to go outside your router to access the server. As the router only forwards requests to the same server on the same ip. So this would work just fine even with vhost setups in apache and all.

- Frode

---

### Post by zasf on 2006-07-29
> **fdoving said:**
> I suggest adding myname.homeunix.net to /etc/hosts with a line like this:
```

192.168.1.99 myname.homeunix.net 

```

That is on the clients.

I don't understand why you would want to go outside your router to access the server. As the router only forwards requests to the same server on the same ip. So this would work just fine even with vhost setups in apache and all.

- Frode

This works fine when my laptop is in the local network, but when I connect from outside it won't work, trying to resolv 192.168.1.99 wich is not gonna be my server.

---

### Post by drivel on 2006-07-29
ithink it depends on your router..

---

### Post by fdoving on 2006-07-29
> **zasf said:**
> This works fine when my laptop is in the local network, but when I connect from outside it won't work, trying to resolv 192.168.1.99 wich is not gonna be my server.

Then setup BIND (nameserver) on your server. Make a zone for  homeunix.net and set mysite.homeunix.net to 192.168.1.99 in it. Then configure the routers DHCP-server to use 192.168.1.99 as primary nameserver. You should also setup BIND with your ISPs-nameservers as forwarders, that way it asks them for names before going to the root servers.


Or maybe a simpler solution: use a local hostname for local communication.

mysite.homeunix.local for example.
you can put it in /etc/hosts without getting problems outside your network. You would have to add a ServerAlias in the virtual host in apache and similar. But i think that's the best solution. 

- Frode

- Frode

---

### Post by strixy on 2006-07-29
> Re: How do you access public IP from within private network?

It seems a little counterintuitive to me to want to go outside the local network only to get back into it again. So I'm pretty sure I don't completely understand what's going on.

I also use a local network and dynds service at work. When I want to access our work server locally (eg. when I have my laptop at work) I use the local IP address (eg. 192.168.1.35 for example).

If I want to access the work server from my laptop when I am at work I use the servers local IP address of [http://192.168.1.34](http://192.168.1.34) (for example). If I am at home and want to access the server at work I use [http://myhost.homeunix.net](http://myhost.homeunix.net).

I have my dyndns service forwarding requests for [http://myhost.homeunix.net](http://myhost.homeunix.net) to the external IP address (provided by my works ISP) where it then hits my work router. My works router forwards all requests to port80 to the proper internal (LAN) IP address that I configured in my works router config. I also configured that computer (the server) to have a dynamic internal IP address, not one that was automatically acquired via DHCP. I also made sure that the ip addy for the server was set to a number higher than the bumber of computers in the office's network, but less than 225. eg. we have 27 computers on the network, so I picked a number between 28 and 225 eg. 192.168.1.35

In Ubuntu, you can set this in the "system" - "administration" - "networking" application (root pw required) and then by selecting the "connection" and "properties". 

I have the router at work configured to forward incoming requests from the outside (eg. the internet) to the appropriate internal IP (LAN) of the server at work.

You will want to configure your router. Depending on the router, you can access it's configuration by going to [http://192.168.1.1](http://192.168.1.1) - read the manual for your router for more information on how to do port forwarding or to edit the DMZ host.

When you ask, > Re: How do you access public IP from within private network? this could mean a couple of different things.

The first thing I think of is that you need the IP address that your ISP gives you so you can set up your dyndns service to point to your router. In which case you have more trouble than you think.

We actually pay extra for my work to have a semi-dynamic IP and we also pay extra for us to be allowed to host a web server and email server etc etc...

If you are using a dial up service or have a semi-dynamic IP from your ISP,  your external IP address actually changes everytime you connect or every so often - which may be the problem you are describing. In which case you need a dns updating tool (available from your dyndns service provider) which will actually communicate with your dyndns service and automatically update your external IP.

If you are trying to give your local networked computers "names" instead of IP addresses, then you will want to follow up on the advice "fdoving" gave above.

If I've missed the mark, could you please describe what you want to do and the result you would like to see, and maybe compare/contrast that with what you are doing now and the result you get now?

---

### Post by zasf on 2006-07-30
> **fdoving said:**
> Then setup BIND (nameserver) on your server. Make a zone for  homeunix.net and set mysite.homeunix.net to 192.168.1.99 in it. Then configure the routers DHCP-server to use 192.168.1.99 as primary nameserver. You should also setup BIND with your ISPs-nameservers as forwarders, that way it asks them for names before going to the root servers.

This is probably what I need to do, from what I read BIND is not so intuitive, so I'd better give it a try and if it takes too long, I'll keep using different URLs to access my server (ie mysite.homeunix.net and 192.168.1.99 locally)

thanks

---

### Post by zasf on 2006-07-30
> **strixy said:**
> It seems a little counterintuitive to me to want to go outside the local network only to get back into it again. So I'm pretty sure I don't completely understand what's going on.

I also use a local network and dynds service at work. When I want to access our work server locally (eg. when I have my laptop at work) I use the local IP address (eg. 192.168.1.35 for example).

If I want to access the work server from my laptop when I am at work I use the servers local IP address of [http://192.168.1.34](http://192.168.1.34) (for example). If I am at home and want to access the server at work I use [http://myhost.homeunix.net](http://myhost.homeunix.net).

I have my dyndns service forwarding requests for [http://myhost.homeunix.net](http://myhost.homeunix.net) to the external IP address (provided by my works ISP) where it then hits my work router. My works router forwards all requests to port80 to the proper internal (LAN) IP address that I configured in my works router config. I also configured that computer (the server) to have a dynamic internal IP address, not one that was automatically acquired via DHCP. I also made sure that the ip addy for the server was set to a number higher than the bumber of computers in the office's network, but less than 225. eg. we have 27 computers on the network, so I picked a number between 28 and 225 eg. 192.168.1.35

In Ubuntu, you can set this in the "system" - "administration" - "networking" application (root pw required) and then by selecting the "connection" and "properties". 

I have the router at work configured to forward incoming requests from the outside (eg. the internet) to the appropriate internal IP (LAN) of the server at work.

You will want to configure your router. Depending on the router, you can access it's configuration by going to [http://192.168.1.1](http://192.168.1.1) - read the manual for your router for more information on how to do port forwarding or to edit the DMZ host.

this is exaclty what I already did and described in my first post

> **strixy said:**
> If I've missed the mark, could you please describe what you want to do and the result you would like to see, and maybe compare/contrast that with what you are doing now and the result you get now?

what I want to do is

```
ssh me@mysite.homeunix.net
```

both remote and locally, instead of doing

```
ssh me@192.168.1.99
```

when in the local net.

---

