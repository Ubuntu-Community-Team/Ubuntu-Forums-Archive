---
title: "Problems with wordpress for external users."
date: 2006-03-22
forum: Server Platforms
---

### Post by ze0n on 2006-03-22
Dear Ubuntu-users!

I have recently reinstalled my server here at home and changed from Debian to Ubuntu. I'm just going to use the server as a small webserver to host my blog and to play around a bit with. Already I have stumbled upon a problem I can't seem to solve and after hours and hours of looking through config files and man entries I have decided to turn to the pro's instead. So here I am. 

I installed wordpress in /var/www/wordpress and everythning seemed to work fine when accessing the server locally. Then the other day when I tried to access my blog at work I couldn't get it to work. Probably because it was set up for internal use I thought so I changed the "WordPress address (URI):" and the "Blog address (URI):" to my external IP. Of course I couldn't get in to the blog after that from my internal network and had to go through a proxy to be able to make any posts. Fine I thought, that wouldn't be that much of a problem but still I wanted to be able to edit posts from my internal network. After some changes I can't seem to get the pictures on the web-site, I can see all the text but it seems as if it can't read the .css file. So now the blog looks horrible when trying to access it from the outside and normal accessing it from my internal network. I tried to reinstall wordpress from scratch, made a new database, a new directory for the wordpress files to reside in but no change. 

I talked to some other people about this problem and they said I should check /etc/hosts and correct it but I think it's correct.

```
127.0.0.1       localhost.localdomain   localhost       hobbiton
192.168.0.100   hobbiton.lan            hobbiton

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I hope that some of you people might have any idea on what to do to correct this problem. I want to be able to access my blog both internally and externally, is that possible? 

If you need any more information or want to look on any of my config-files just tell me. 

Also I should apologize for my bad english. It's not my native language so please excuse me for any typos.

Best Regards
Mathias

---

### Post by claes on 2006-03-22
If you set the "WordPress address (URI):" and the "Blog address (URI):" to use a name instead of an ip address it should work. That is what I have done and it works external and internal.

Claes

---

### Post by Horndog on 2006-03-22
There is too much information missing. This is clearly a network problem. You mention a proxy. We need to know the details about your local network and what kind of a proxy server is used, along with what kind of Internet account (Home, business, and Dynamic or static IP). Until we have this information all anyone can do is commiserate with you.

---

### Post by ze0n on 2006-03-22
Claes: I have set the "WordPress address (URI):" and the "Blog address (URI):" to use my domain name foo.bar.nu so I have no IP-adress there. Still no success unfortunately. 

Horndog: I wasn't that clear in my previous message, I'm only using the proxy for testing purpose. That is I only use a proxy to see what it would look like when someone tries to access my computer from the outside. I have a dynamic IP and I use it with a Free Dynamic DNS to get my domainname. I haven't had my IP changed for more then a year so you could almost call it a static IP. My internet account is for home use only, a DSL modem with a builtin router from Alcatel. My Ubuntu server have a static IP and is directly connected to the router in which I have opened all the necessary ports. I'm not in i domain at home, instead on my Windows machines I have a workgroup named LAN which is also enabled in my routers DHCP server. That's why my Ubuntu server is named hobbiton.lan. 

Thanks for your time!

Best Regards
Mathias

---

### Post by Horndog on 2006-03-22
[QUOTE=ze0n][...]
Horndog: I wasn't that clear in my previous message, I'm only using the proxy for testing purpose. That is I only use a proxy to see what it would look like when someone tries to access my computer from the outside. I have a dynamic IP and I use it with a Free Dynamic DNS to get my domainname. I haven't had my IP changed for more then a year so you could almost call it a static IP. My internet account is for home use only, a DSL modem with a builtin router from Alcatel. My Ubuntu server have a static IP and is directly connected to the router in which I have opened all the necessary ports. I'm not in i domain at home, instead on my Windows machines I have a workgroup named LAN which is also enabled in my routers DHCP server. That's why my Ubuntu server is named hobbiton.lan. 

Thanks for your time!

Best Regards
Mathias[/QUOTE]

Two things that come to mind: In order to see your site, from thie Internet behind a proxy, you have to setup a reverse proxy and make sure your ISP does not block port 80. I'm sure you know that port 80 has to be forwarded to the right local IP from your router and open on your firewall.

---

### Post by ze0n on 2006-03-23
Well there's no problem getting in to my page when I put my domain name in the "WordPress address (URI):" and the "Blog address (URI):" fields. So there's nothing wrong with the acctual connection to the webserver as it seems. I just want to be able to access my webserver at my internal address 192.168.0.100 when I'm at home and access it at my external address "213.***.***.***" when I'm at work or something like that. It seems as if I change the "WordPress address (URI):" and the "Blog address (URI):"  to my external IP or my domain name I can connect to the server from work but it tries to load the pictures from my internal address 192.168.0.100.

Well I guess I'll have to do some more trying. Thanks for your help!

Best Regards 
Mathias

---

### Post by claes on 2006-03-23
Could be that the wordpress server resolvs the name to the internal ip and that's why it works strange when you connect to it from internet. That's what my server does. Meaning the server itself resolves it's fqdn (fully qualified domain name) to it's internal ip and that works for me. 

What is the address to the pictures in your code? I always set all my links on my web pages to use "/directory/file"  not full http:// addresses as that makes it troublesome to move the site.

Not sure if this is any help for you.

Claes

---

### Post by Horndog on 2006-03-23
[QUOTE=claes][color=red]Could be that the wordpress server resolvs the name to the internal ip[/color] and that's why it works strange when you connect to it from internet. That's what my server does. Meaning the server itself resolves it's fqdn (fully qualified domain name) to it's internal ip and that works for me. 

What is the address to the pictures in your code? I always set all my links on my web pages to use "/directory/file"  not full http:// addresses as that makes it troublesome to move the site.

Not sure if this is any help for you.

Claes[/QUOTE]

If that's the case then there is probably line in the servers host file with that domain name. (For testing purposes I'm sure ;)) To trick the **[color=red]network**[/color] into loading that page using a domain name address with a local **[color=red]network**[/color] IP, instead of doing a proper DNS search using the ISP's Domain Name Server. The obvious solution is to remove it unless there is still more unrevealed pertinent information.

---

### Post by ze0n on 2006-03-23
Now it's working for external access it seems. The address is [http://ze0n.mine.nu]("http://ze0n.mine.nu") and everything seems to work perfectly well when I access it via a proxy. Now when I try to access the site by entering my internal IP, 192.168.0.100 I can't reach my site because it's beeing redirected to ze0n.mine.nu of course. That's the problem, I would like to be able to access my blog from home without the use of a free proxy server.

Regards
Mathias

---

### Post by claes on 2006-03-23
Well that part is very simple. Add ze0n.mine.nu to your /etc/hosts file and point it to your internal ip. wordpress don't work as it should when you try to connect to it with any other address besides the address you set up as a uri.

Claes

---

### Post by Horndog on 2006-03-23
[QUOTE=ze0n] [...]
I would like to be able to access my blog from home without the use of a free proxy server.[/QUOTE]

Why don't you tell us about this proxy server? ...and why would you need this "free proxy server?"

---

### Post by ze0n on 2006-03-24
Well the reason why I'm using a proxy is that I can't access my wordpress-blog internally. That is by entering my internal IP 192.168.0.100 in Firefox. And if I enter ze0n.mine.nu in Firefox I can't access it either because beacuse I'm at the same IP. Therefore I use a free proxy in Firefox to tell the network I'm coming from another IP so I can access my blog. 

Well case solved, I'll go on with my current setup. Doesn't matter that much if I can't access my blog with the internal address.

---

### Post by kmi on 2006-03-24
Hi,
Sorry if I have missed steps and can't really figure out your actual config ze0n but, as a UbuntuApacheMySQLPHPMyAdminWordpress (UAMPW ?! ;)) user too, I somehow feel free to contibute... :mrgreen:

In Wordpress (blog/address URI), I have : [http://kmi.no-ip.org](http://kmi.no-ip.org)
and in /etc/hosts :
```
127.0.0.1 localhost.localdomain localhost webbun
192.168.3.50 kmi.no-ip.org webbun
```
And everything is OK... Could you please post your actual config. ?

---

### Post by ze0n on 2006-03-25
> **kmi]Hi,
Sorry if I have missed steps and can't really figure out your actual config ze0n but, as a UbuntuApacheMySQLPHPMyAdminWordpress (UAMPW ?!  said:**
> http://kmi.no-ip.org[/url]
and in /etc/hosts :
```
127.0.0.1 localhost.localdomain localhost webbun
192.168.3.50 kmi.no-ip.org webbun
```
And everything is OK... Could you please post your actual config. ?

I have it written down like that to and sure, it's working on my Linux computer but when I grab my iBook or some of my other computers, I can't access it. Well I'll just set up a new internal DNS I guess :) 

Thanks for all your answers people. 

Best Regards
Mathias

---

### Post by claes on 2006-03-25
Or you can edit the hosts file on your other computers if you don't want to hack dns. But it less jobb to just set up a internal dns server. Alot more fun aswell. :-)

Claes

---

