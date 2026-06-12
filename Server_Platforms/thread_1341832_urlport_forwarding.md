---
title: "url/port forwarding"
date: 2009-11-30
forum: Server Platforms
---

### Post by blindmist on 2009-11-30
I have a domain, say google.com

that ip goes to say 200.200.200.1 and goes directly to that computer.

if i access google.com/int1 i need it to go the internal ip of 192.168.1.129:2693

and if i access google.com/int2 i need it to go the internal ip of 192.168.1.129:2694

and so forth for int3



How do i go about setting this up so that it does not redirect to that ip, but forwards it all?

---

### Post by BkkBonanza on 2009-11-30
It's easier to setup if you can use subdomains like int1.google.com but if not then you would have to use .htaccess or apache directives (assuming apache) to add an internal redirect. Internal redirects are not visible to the user since they are handled by the web server. If you really want to avoid redirects then you would have to map the relevant machines into your file system perhaps using NFS or Samba at the suitable directory mount point.

---

### Post by blindmist on 2009-11-30
i can do sub-domains. so say we go to 

int1.google.com--->192.168.1.129:2693**/gui**
int2.google.com--->192.168.1.129:2694**/gui**
int3.google.com--->192.168.1.129:2695**/gui**


how do i go about that?

**EDIT: I added something that is critical.**

---

### Post by BkkBonanza on 2009-11-30
Then you would just make DNS entries for each subdomain. If this is on your LAN then you would add entries to dnsmasq / dhcp on your router. For the ports you would add port info to the apache virtual domain directives, ie. for each particular subdomain you would indicate which port it should listen on. However, you would have to include that port value in any requests made unless you were able to add DNS entries that can force a redirect including port value. Not sure if that's common though. 

Some of this depends on exact network config. So for example, if you're behind a router (presumably true) then you would want to port forward specific ports to the right machine. 

If you are going to use subdomains though you wouldn't need (or really want) to use ports like 2693 etc. The subdomains can all exist on one machine listening on the normal port 80.

Is there a reason you want to use non-standard ports?

---

### Post by blindmist on 2009-11-30
The server does go through a router, just that all routers and switches are transparent to the server. I set it a static ip with the correct DNS and gateway and thats the ip for the server and website externally as well.

The probelm with all of this is that I need to ubuntu server to talk over to 192.168.1.129 port whatever which is a Windows machine running a windows only program.

There really isn't a simpler way to do this? I did not think it would be that difficult and figured someone would have implemented this.

I am sure I am not the only one that wants to redirect to an internal ip blindly.



I should also say, it is ok to type the port number and /gui on the subdomain side as long as it carries over with the 192 ip

int1.google.com:2693/gui ----> 192.168.1.129

---

### Post by BkkBonanza on 2009-12-01
I'm sorry, I'm not trying to be obtuse but it's not clear at all what you really want to do. It sounds like your'e trying to do something the wrong way and so it's being made more difficult than it needs to be. 

Perhaps go back to basics. 
Are you trying to serve to the public on the internet or just to your local LAN? Or to both?

I think if I knew what you want to achieve I could tell you the easiest way to set it up. It does sound like you're taking a hard path and usually non-standard ports and subdomains aren't needed. But it all depends what the goal is.

If I had to guess now I'd imagine you're set up like this:


```
public -> router -> ubuntu server
                 -> windows machine
```

You want anyone accessing the site via the base domain to go to ubuntu but anyone accessing the site via a special url (whether subdomain or subdirectory) to be routed to the windows machine?

---

### Post by blindmist on 2009-12-14
> **BkkBonaza said:**
> I'm sorry, I'm not trying to be obtuse but it's not clear at all what you really want to do. It sounds like your'e trying to do something the wrong way and so it's being made more difficult than it needs to be. 

Perhaps go back to basics. 
Are you trying to serve to the public on the internet or just to your local LAN? Or to both?

I think if I knew what you want to achieve I could tell you the easiest way to set it up. It does sound like you're taking a hard path and usually non-standard ports and subdomains aren't needed. But it all depends what the goal is.

If I had to guess now I'd imagine you're set up like this:


```
public -> router -> ubuntu server
                 -> windows machine
```

You want anyone accessing the site via the base domain to go to ubuntu but anyone accessing the site via a special url (whether subdomain or subdirectory) to be routed to the windows machine?

correct

---

### Post by BkkBonanza on 2009-12-14
Ok. Then this is easy.
Any domain or subdomain you want gets pointed to your router's public IP using DNS.
Your two machines get configured normally with whatever sites you want on each one.

Then in your router you forward two ports. Port 80 to the IP of your server machine. Another port (say 8080) points to the IP of your windows machine but port 80.

You url for the sites you want to have on your windows machine need to have the :8080 suffix. eg.

mydomain.com -> router fwd(80->uip:80) -> ubuntu machine (uip)
any.mydomain.com:8080 -> router fwd(8080->wip:80) -> windows machine (wip)

You can pretty much use any domain names or paths as you like because it's the port that decides which machine it ends up on.

---

