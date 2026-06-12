---
title: "apache2 woes"
date: 2010-10-12
forum: Server Platforms
---

### Post by tad1073 on 2010-10-12
I am having problems accessing my website. I have port forwarding enabled on my router and below are the errors I am getting plus my firewall setup.

```
thomas@tdtconsulting:/etc/apache2/sites-available$ sudo a2ensite tdtconsulting
[sudo] password for thomas: 
Enabling site tdtconsulting.
Run '/etc/init.d/apache2 reload' to activate new configuration!
thomas@tdtconsulting:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          [Tue Oct 12 18:21:04 2010] [warn] NameVirtualHost 192.168.1.3:80 has no VirtualHosts

```

```
thomas@tdtconsulting:/etc/apache2/sites-available$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

```

---

### Post by arrrghhh on 2010-10-12
**[warn] NameVirtualHost 192.168.1.3:80 has no VirtualHosts**

That I think is the culprit... Check your config files.

---

### Post by tad1073 on 2010-10-12
ok, got that fixed but I still can't access my site nor can I ssh into tdtconsulting.dyndns.org

do I need to give the address as my lan address or wan address?

---

### Post by HighCommander540 on 2010-10-12
> **tad1073 said:**
> ok, got that fixed but I still can't access my site nor can I ssh into tdtconsulting.dyndns.org

Are you sure that you have the port forwarding setup correctly? I know there have been many times where I thought it was configured correctly, but it was a digit off.

Check the computers IP address. Then make sure you router is sending 80 and 22 to that IP address.

Also, I have had the problem if you are running on a personal connection (like DSL). Sometimes the modem you get is actually a router too. So you have to set up a rule in the modem as well.

---

### Post by tad1073 on 2010-10-12
> **HighCommander540 said:**
> Are you sure that you have the port forwarding setup correctly? I know there have been many times where I thought it was configured correctly, but it was a digit off.

Check the computers IP address. Then make sure you router is sending 80 and 22 to that IP address.

Also, I have had the problem if you are running on a personal connection (like DSL). Sometimes the modem you get is actually a router too. So you have to set up a rule in the modem as well.

I have checked port forwarding and everything is good there. We just got a new modem a couple of moths ago, it is set to bridged with our router set to PPPoE. I will have to check the modem firewall but that entails me unplugging the modem from the router and pluging the computer into it.

---

### Post by arrrghhh on 2010-10-13
> **tad1073 said:**
> ok, got that fixed but I still can't access my site nor can I ssh into tdtconsulting.dyndns.org

do I need to give the address as my lan address or wan address?

So if you're on your LAN - use the LAN address.  If you're on a WAN link, use the WAN address.

I'm not sure why, but some routers seem to let you access a site from the WAN address when you're on the LAN and some don't.  I believe mine does, but it's a pretty advanced router.  There may be some forward setting on it that I haven't ran into :p

If it doesn't even work from your LAN, you've got bigger problems.  Use nmap from another box to make sure the port is at least visible on your LAN.

---

### Post by scrooge_74 on 2010-10-13
I put my money on the provider's router check if that one is forwarding ports correctly to your own router.

Also sometimes those routers use port 80 for admin work so you may have to move the admin port to something else in order for it to properly forward the port 80 request to your internal lan

---

### Post by tad1073 on 2010-10-13
> **arrrghhh said:**
> If it doesn't even work from your LAN, you've got bigger problems.  Use nmap from another box to make sure the port is at least visible on your LAN.

I can access everylthing I need to over the lan, it is just when I try and use my domain name to access it is where I run into problems.

---

### Post by HighCommander540 on 2010-10-13
> **tad1073 said:**
> I can access everylthing I need to over the lan, it is just when I try and use my domain name to access it is where I run into problems.

> **arrrghhh said:**
> So if you're on your LAN - use the LAN address.  If you're on a WAN link, use the WAN address.

I'm not sure why, but some routers seem to let you access a site from the WAN address when you're on the LAN and some don't.  I believe mine does, but it's a pretty advanced router.  There may be some forward setting on it that I haven't ran into :p

If it doesn't even work from your LAN, you've got bigger problems.  Use nmap from another box to make sure the port is at least visible on your LAN.

Yeah, this could be your problem. I had the same issue with an old router.

Try this...Hook up to a different internet connection (like a friends). And then see if you can access the pages or SSH.

Some router's (like my old one) have a really weird DNS lookup thing that if you try to access a IP address that routes right back to itself (like this case). It won't let you access the external one from within the router. But you can use the LAN address. I know its a little weird and confusing, but it happened to me.

Basically try accessing your tdtconsulting.dyndns.org from outside your LAN. If you can you are good and just use your LAN address when you are connected to the network.

---

### Post by arrrghhh on 2010-10-13
> **tad1073 said:**
> I can access everylthing I need to over the lan, it is just when I try and use my domain name to access it is where I run into problems.

How is your domain name forwarded to your IP?  Is it dyndns?  Are you using the client...?

Have you tried hitting your site with just your external IP?

---

### Post by tad1073 on 2010-10-13
> **HighCommander540 said:**
> Yeah, this could be your problem. I had the same issue with an old router.

Try this...Hook up to a different internet connection (like a friends). And then see if you can access the pages or SSH.

Some router's (like my old one) have a really weird DNS lookup thing that if you try to access a IP address that routes right back to itself (like this case). It won't let you access the external one from within the router. But you can use the LAN address. I know its a little weird and confusing, but it happened to me.

Basically try accessing your tdtconsulting.dyndns.org from outside your LAN. If you can you are good and just use your LAN address when you are connected to the network.

I know it works cause when I was using centOs everthing worked as intended. My router is a new router ie. 1 year old


> **arrrghhh said:**
> How is your domain name forwarded to your IP?  Is it dyndns?  Are you using the client...?

Have you tried hitting your site with just your external IP?

I am using dyndns. I have disabled iptable rule for port 80 and managed to lock myself out from remoting to my server. I have been too lazy to cary a monitor, keyboard and mouse down to it to fix the rules.

---

### Post by arrrghhh on 2010-10-13
So have you verified that dyndns is getting updated correctly?  You didn't say if it worked if you try & hit it with the external IP instead of the DNS-friendly name.

I'm not sure what you mean about disabling the iptable rule for port 80... Don't you just ssh in?

---

### Post by tad1073 on 2010-10-13
> **arrrghhh said:**
> So have you verified that dyndns is getting updated correctly?  You didn't say if it worked if you try & hit it with the external IP instead of the DNS-friendly name.

I'm not sure what you mean about disabling the iptable rule for port 80... Don't you just ssh in?

I have tried it with my wan address but no dice. 

I deleted the rule for port 80.

I do use ssh to access my server but I have locked myself out because I forgot to add a rule for ssh after doing iptables -P INPUT DROP

---

### Post by HighCommander540 on 2010-10-13
> **tad1073 said:**
> I have tried it with my wan address but no dice. 

I deleted the rule for port 80.

I do use ssh to access my server but I have locked myself out because I forgot to add a rule for ssh after doing iptables -P INPUT DROP

Looks like you are going to have to access it with a keyobard and monitor. :P

---

### Post by tad1073 on 2010-10-14
> **HighCommander540 said:**
> Looks like you are going to have to access it with a keyobard and monitor. :P

actually all I had to do was reboot the machine

---

### Post by HighCommander540 on 2010-10-14
> **tad1073 said:**
> actually all I had to do was reboot the machine

That's cool does everything work now?

---

### Post by tad1073 on 2010-10-16
> **HighCommander540 said:**
> That's cool does everything work now?

I can ssh again if that is what you mean.

---

### Post by tad1073 on 2010-10-30
new error after sorting things out

```
* Restarting web server apache2
apache2: apr_sockaddr_info_get() failed for tdtconslting.dyndns.org
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

``` more help would be greatly appreciated

---

### Post by tad1073 on 2010-10-31
got the above error squared away. now when I try to access my website it just times out.

---

### Post by tad1073 on 2010-12-08
got everything working, turned out it was my router settings

---

