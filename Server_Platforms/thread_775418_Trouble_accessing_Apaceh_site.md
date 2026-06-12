---
title: "Trouble accessing Apaceh site?"
date: 2008-04-30
forum: Server Platforms
---

### Post by ixlam on 2008-04-30
I have gusty installed and apache hosting my site, Im behind a router and using a redirection service,

I can browse the site from my own PC using http://<the name of my site>
but not from outside the LAN. (apache is using port 80)

The router port 80 is open and my IP/"domain" IS being updated with the redirection service provider.

Could my firewall/iptables be the issue  ie.redirections blocked ?

what would be the easiest way to diagnose this ?

thanks in advance.

---

### Post by bluefrog on 2008-04-30
If you are trying to reach it from your LAN, you will not be able to do it.
You can not access [www.yourdomain.com](www.yourdomain.com) from your LAN (except of course if your machine name is [www.yourdomain.com](www.yourdomain.com), but that's another story)

If this not the case, explain your case more precisely, give the address...

James Dupin

---

### Post by windependence on 2008-04-30
Go to [www.canyouseeme.org](www.canyouseeme.org) and check your port 80 to see if it is open. many ISPs block you from running a server on their network. If that is the case, you can just host the site on another port like 8080, or 81. Let us know what you find out.

-Tim

---

### Post by ixlam on 2008-04-30
so .. [http://www.canyouseeme.org/](http://www.canyouseeme.org/) cannot see my port 80 as being opend,, 
*it might be my IPtables though.

my router is set to:
Virtual Server HTTPS	192.168.0.2	TCP 80/80

Apache is also set to 80 as the listening port.

this config  DID work at one time in the past.
I have changed the IPtables since so I think that this could be the problem.

When I put [www.(nameofmysite).dyndns.org](www.(nameofmysite).dyndns.org) in to my browsers address bar it works. 
but if a friend elsehwere does, it does NOT work.

---

### Post by ixlam on 2008-05-01
OKAY .. its definately my Iptables config .. after I shut down the firewall everything works as planned!! 

Now If I could just remember how to add outgoing traffic on port 80 I'd be set?!

I've added 

# Allow http
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -o eth0 -p udp -m udp --dport 443 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT


But still no go ??

---

