---
title: "New to Linux and hosting a Web Server – I’m confused!"
date: 2009-11-26
forum: Server Platforms
---

### Post by eddie1968 on 2009-11-26
[FONT=Calibri][SIZE=3]Could someone please help me? I am brand-spanking new to Linux and setting up a web server and I am trying hard but now am really starting to tear my hair out…[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I am trying to set up my own web site hosted from home via my ADSL service provided by my ISP, which is TPG Internet (Australian ISP). I have a separate 2.66 GHz Pentium 4 PC that is linked to my Netgear wireless router via an Ethernet cable. I have installed Ubuntu server 8.04 Hardy Heron on the PC and have also installed LAMP and EHCP. I have followed a tutorial for setting up PHP and Apache and all systems appear to be working okay.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I have registered a domain name with AustDomains, my registrar. My ISP has given me a static ISP address and do not block any ports.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The PC has an IP address of 10.0.0.5, which shows “It works!” when I type it in, which I understand means that Apache is working. I can also view my control panel through [/SIZE][/FONT][[FONT=Calibri][SIZE=3][COLOR=#0000ff]http://10.0.0.5/vhost/ehcp[/COLOR][/SIZE][/FONT]]("http://10.0.0.5/vhost/ehcp")[FONT=Calibri][SIZE=3]. I can also SFTP to my server via FileZilla using this IP address.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]What I can’t do is make my website visible to the outside world, and this is where I am going to need some help, please.[/SIZE][/FONT]
 
**[SIZE=3][FONT=Calibri]My settings:[/FONT][/SIZE]**
 
[FONT=Calibri][SIZE=3]When I use the */sbin/ifconfig* command on my server, the following IP addresses appear:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Link encap: Ethernet[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Inet addr: 10.0.0.5[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bcast: 10.0.0.255[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Mask: 255.255.255.0[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Link encap: Local loopback[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Inet addr: 127.0.0.1[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Mask: 255.0.0.0[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]My IPS’s DNS addresses are as follows:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Primary DNS: 203.12.160.35[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Secondary DNS: 203.12.160.36[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]My router’s WAN IP is as follows [COLOR=red](I have used XXX for security purposes[/COLOR][COLOR=red])[/COLOR] : 220.XXX.83.XXX. On my router, I have also port forwarded HTTP (port 80) and SFTP (port 22) to 10.0.0.5.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Okay, here is my first problem… When I am configuring the static address in Ubuntu */etc/network/interfaces*, what details do I put into this file? My current settings are:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]*# The primary network interface*[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]*auto eth0*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*Iface eth0 inet static* [COLOR=red](I changed this from DHCP to static)[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*address 10.0.0.5*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*netmask 255.255.255.0*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*network 10.0.0.0*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*broadcast 10.0.0.255*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*gateway 10.0.0.1*[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]My second problem - In the etc/resolv.conf file, what settings do I put in there? My current settings are:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]*search mydomain.com* [COLOR=red](I have used my own domain name here)[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*nameserver 203.12.160.35*[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*nameserver 203.12.160.36*[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]My last problem is on my Domain registrar’s website. They ask for name servers and IP addresses for my domain name. What do I enter here? My current settings (which I have entered) are:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]ns1.tpgi.com.au 203.12.160.35[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ns2.tpgi.com.au 203.12.160.36[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]If somebody could please help a Linux illiterate (but who wants to have a go at it) out, I would be truly grateful.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Many thanks.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Cheers,[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]Eddie.[/FONT][/SIZE]

---

### Post by mlentink on 2009-11-26
10.x.x.x are adresses for private networks, not public.

I guess you need to setup port forwarding in your router to your server. Are you sure your public adress ( probably 203.x.x.x) is static?

Please be aware of the distinction between your ***public adress*** (i.e. the adress of your router) and your ***private adress*** (the adress within your LAN, 10.x.x.x)

---

### Post by munky99999 on 2009-11-26
> My router&#8217;s WAN IP is as follows (I have used XXX for security purposes) : 220.XXX.83.XXX.

If someone goes to 

[http://220.XXX.83.XXX](http://220.XXX.83.XXX)

Does it work? You can just goto the base webpage. Not necessarily any vhost stuff. However you're are verifying that the outside world cannot see you. Should be able to see that.

Doing this will take the domain name issue out of the equation.

If that doesnt work. The issue doesn't lay with the domain name.
If that does work. The issue lay with the domain name resolution.

> When I am configuring the static address in Ubuntu /etc/network/interfaces, what details do I put into this file? My current settings are:
That's fine. The static setting is what will allow port forwarding to never need to change.


One thing you can also do.

```
nslookup mydomain.com (I have used my own domain name here)
```
Make sure what you get back is your ip. The 220.XXX.83.XXX


> My last problem is on my Domain registrar&#8217;s website. They ask for name servers and IP addresses for my domain name. What do I enter here? My current settings (which I have entered) are:

ns1.tpgi.com.au 203.12.160.35
ns2.tpgi.com.au 203.12.160.36
This is probably the issue.

The IP address for the domain name should be pointed at your ip.

The 220.XXX.83.XXX

Your ISP's DNS doesn't care or know about your domain name.

Your domain name name servers are your own. I'm not sure if you require these. You should be able to simply point the domain registrar to your webserver. No name resolution required then.


If you do require name servers.

[https://help.ubuntu.com/9.10/serverguide/C/dns.html](https://help.ubuntu.com/9.10/serverguide/C/dns.html)

Configure a primary master. Not caching or secondary. You really shouldnt try to do this step. As it sounds like it's completely unnecessary.

---

### Post by eddie1968 on 2009-11-26
Many thanks for your help. I have entered [[COLOR=#444444]http://220.XXX.83.XXX[/COLOR]]("http://220.XXX.83.XXX") into my web browser and yes, it does point to my site. :p
 
I have now updated my domain registrar's name servers and IP address to point to 220.XXX.83.XXX. Hopefully once that is propogated I should then be able to type [http://www.mydomain.com](http://www.mydomain.com) into a web browser to view my site?
 
Will advise if I have success.
 
Thanks again.
 
Cheers,
 
Eddie.

---

### Post by gombadi on 2009-11-26
> 
I have now updated my domain registrar's name servers and IP address to point to 220.XXX.83.XXX.


I don't think this will fix your domain lookup problems.

The nameserver information you enter in the registrar tells the world what DNS server to talk to to get information about your domain. If you enter your ip address then you will need a DNS server running at that public ip address to answer queries for your domain. Based on what you have said above you do not have a DNS server running on this machine.

Another easier solution may be to use the dns servers of the registrar for dns. Most registrars have the ability to host dns for domains registered with them then you log into their site and can enter ip information for the hosts - i.e. www goes to 220.xxx.83.xxx etc

---

### Post by eddie1968 on 2009-11-26
Thanks for the info Gombadi,
 
My registrar does have DNS hosting, but they want AUD$34 per year for the privilege, and I really don't want to be shelling out for this service.  Does anyone know of any decent DNS hosts that has this service for free?  I have seen that OpenDNS has a free account, but I'm not certain whether I can use it for my purpose.
 
Cheers,
 
Eddie.

---

### Post by eddie1968 on 2009-11-27
Yay!  I finally got it to work.  I found a free DNS hosting site ([www.dnsexit.com]("http://www.dnsexit.com")) and pointed it to my external WAN IP address.  I changed the name servers on the domain registrar to dnsexit's ones and voila!  Many thanks to everyone that provided me with assistance.  It is much appreciated.
 
Time for a few beers and some cheers,

Eddie.
 
:p

---

### Post by winven on 2009-12-18
I Don't get confused in choosing the Hosting,Because i choosed the LINUX Platform Web Hosting Economy Plan at low cost in the site [http://www.xnynz.com/](http://www.xnynz.com/)

---

