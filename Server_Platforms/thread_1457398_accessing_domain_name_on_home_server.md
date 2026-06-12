---
title: "accessing domain name on home server"
date: 2010-04-18
forum: Server Platforms
---

### Post by 6py7 on 2010-04-18
I am a complete newbie at web servers, so I installed Ubuntu Server and have a LAMP set up.  I have gotten dynamic DNS to link to my domain, and that seems to be working.  My domain is 6py7.com.  If I try to access my domain from within my home network it links me to my router's main page (192.168.2.1).  I have my server set up with a static ip at 192.168.2.100 and have port forwarding set up.

Is there something I missed with the setup of this?  I can only access my domain if I use a network outside of my home network, but if I am within my home network the domain name links to the router.

---

### Post by Ryan Dwyer on 2010-04-18
That's how it works. If you want to access your server using the domain name from inside your network then you'll need to change your local DNS settings.

---

### Post by volkswagner on 2010-04-18
Two settings on your router to check

Turn off remote admin...This will display admin page to local LAN not WAN users.

Check your NAT setting.

---

### Post by SRST Technologies on 2010-04-18
Seems to me that your Dynamic DNS client is running on the server and not on the router.  If you run it on the server, it's going to tell DynDNS.org or whoever is your Dynamic DNS provider that the server's private IP address is the address it wants to make the record against, and naturally nobody on the net knows your server's private IP address.

If your router supports it, configure the Dynamic DNS client on the router and turn it off on the server.  Since you have port forwarding in place already, it'll suddenly work without a hitch.

---

### Post by Kiwi76 on 2010-04-19
If none of the solutions posted are the issue, your router may simply lack NAT loopback and not have the option to enable/do it. I say this because I had that problem.

If the client (not your server) you're using to access it is Windows based, you can modify your "HOSTS" file to redirect your domain name to your server's IP address, and/or simply access it via the internal IP address (may not work as well when links come into question?). This is what I did.

If the client is something else (Mac/Linux/etc.), I wouldn't know the equivalent, though I'm sure there must be one.

---

### Post by Cheesemill on 2010-04-19
> **Kiwi76 said:**
> 

If the client is something else (Mac/Linux/etc.), I wouldn't know the equivalent, though I'm sure there must be one.

There's a host file in Linux as well, you'll find it at /etc/hosts

Just add the internal IP address of your server along with your domain name, for example:
```
192.168.0.200       www.6py7.com
```

---

