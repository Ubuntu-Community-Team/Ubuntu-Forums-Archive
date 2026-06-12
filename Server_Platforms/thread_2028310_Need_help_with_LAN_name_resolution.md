---
title: "Need help with LAN name resolution"
date: 2012-07-17
forum: Server Platforms
---

### Post by lykwydchykyn on 2012-07-17
Here's the scenario.  I have a home network with about half a dozen devices on it.  All of them are on DHCP except for my server, which we use for a variety of services like web, ssh, dict, proxy, etc.

Today I got a replacement router/modem from my ISP, a Netgear VersaLink b90-755025.  I got it set up, but the DHCP settings are pathetically limited.  Previously, I had my server running dnsmasq to resolve hostnames for local computers and to cache DNS.  But my new router doesn't allow me to specify custom DNS entries for the LAN.

It has its own special sauce to resolve hostnames that are on DHCP, but for static I'm on my own.

I know I can edit the hosts file on every OS on every machine (some of them dual boot, or more...), but I'd rather have an automatic solution. Is there some kind of broadcast-based solution I can use that doesn't require tinkering on the clients?  Is there a way to get to more advanced settings on this router? (custom firmware isn't an option right now -- I don't want to brick my internet connection!)

I tried to set up avahi, but I don't think I understand what it actually does.

---

### Post by koenn on 2012-07-18
how about

- turn of the dhcp server in the router
- use dnsmasq dhcp server instead

---

### Post by Morbius1 on 2012-07-18
> **lykwydchykyn said:**
> Is there some kind of broadcast-based solution I can use that doesn't require tinkering on the clients?
Linux / Samba does this automatically but it might need a little help.

When you install Ubuntu it creates a set of defaults that determines how samba ( client and server ) functions. The first thing it does is it sets the netbios name to your hostname. You can find the default samba setting for that by running the following command:
```
testparm -sv /dev/null | grep "netbios name"
```There is one issue here and that's the length of the netbios name. Run the command above and count the number of characters. If it's 16 characters long or longer then the other machines can't resolve it. You can fix that by actually changing the hostname but you can also just edit smb.conf and give the server a shorter name by adding the following line - right under the workgroup line:
```
netbios name = some-name
```[COLOR=Blue]*Just make sure that some-name is less that 16 characters long.*[/COLOR]

This pretty much works out of the box once the 16 character limit has been fixed but you might need to take one more step and it's something you referenced in your question.

By default samba will resolve netbios names in this order:
> name resolve order = lmhosts wins host bcastlmhosts and host are not set up for samba by default so they are ignored. wins refers to a WINS server and this can cause ( although not always ) all sorts of problems if you don't happen to have one in your network. The only one that works by default is bcast - broadcast - and it's listed last. Put it first and put wins last by adding another line to smb.conf in the [global] section:
```
name resolve order = bcast lmhosts host wins 
```[B]
[COLOR=Blue]EDIT[/COLOR][/B]: I should note that Windows machine automatically truncates the hostname to 15 characters and although it handles the name resolve order in exactly the same way a Linux machine does it handles it better. So you need to make these changes to all Linux machines on your network.

[COLOR=Blue]**EDIT2**[/COLOR]: There are a couple of bug reports that essentially ask for these changes to be implemented on install so that we don't have to mess with things:

Hostname length: [https://bugs.launchpad.net/ubuntu/precise/+source/samba/+bug/735072](https://bugs.launchpad.net/ubuntu/precise/+source/samba/+bug/735072)
Bcast first: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/804588)

---

### Post by volkswagner on 2012-07-18
Wow that router seems pretty lame.

Can any of the DHCP clients access each other by hostname?  If the issue is just the server perhaps you can set a static lease and change the server from static to DHCP.

I did not see any info available on setting up a static lease on the Netgear.  Sometimes this will be enough to at least let the router be aware of the hostname.


If the above does not work, you may want to ditch that router or add a second.
I'm not sure how much this will affect you, but I'd try adding a second router behind the Netgear.  If there is a DMZ setting on the isp provided router, put the second routers into the dmz.  Then all your LAN and wireless LAN devices will connect to the second router.

Unfortunately this will create a double NAT situation, but I fee as though you will struggle with that isp provided router.

---

### Post by sandyd on 2012-07-18
> **lykwydchykyn said:**
> Here's the scenario.  I have a home network with about half a dozen devices on it.  All of them are on DHCP except for my server, which we use for a variety of services like web, ssh, dict, proxy, etc.

Today I got a replacement router/modem from my ISP, a Netgear VersaLink b90-755025.  I got it set up, but the DHCP settings are pathetically limited.  Previously, I had my server running dnsmasq to resolve hostnames for local computers and to cache DNS.  But my new router doesn't allow me to specify custom DNS entries for the LAN.

It has its own special sauce to resolve hostnames that are on DHCP, but for static I'm on my own.

I know I can edit the hosts file on every OS on every machine (some of them dual boot, or more...), but I'd rather have an automatic solution. Is there some kind of broadcast-based solution I can use that doesn't require tinkering on the clients?  Is there a way to get to more advanced settings on this router? (custom firmware isn't an option right now -- I don't want to brick my internet connection!)

I tried to set up avahi, but I don't think I understand what it actually does.
This is easy.
Get a switch (they are deathly cheap), and hook up all computers + the server to it.
Hook up the router to the server, and route everything through the server.

---

### Post by lykwydchykyn on 2012-07-18
Thanks for the suggestions; there are a couple of points I should make:

 - I considered switching to DHCP on the server.  The only downside to this is that the server isn't necessarily reliable, and it's somewhat slow.  If it goes down while I'm at work, nobody at home will be able to use the Internet.  That's not really ideal.

 - I have a netbios name set, but for some reason it's not being resolved by clients.  Plus, samba is (by far) not the only (or even the most oft-used) service on this machine.  Does nb name resolution work for non-samba services?

 - All the DHCP hosts can find each other by name.  The router is presumably doing this.

 - Yes, absolutely, it is a crap router.  The only redeeming aspect is that it's free.

 - I still have my old router; I'd rather use the wireless on the new router, since it's faster.  I guess I could have the old router just for DHCP if I need to.  Not really ideal.


Anyway, thanks for the brainstorms so far...  I guess the quick & easy solution might be to enable a second IP address on the server and make it dynamic.  I want to keep a static just because I have a lot of things set to go to it by IP right now (proxy filtering, e.g.) and I want to be able to find it in the event name resolution doesn't work.

---

### Post by sandyd on 2012-07-18
> **lykwydchykyn said:**
> Thanks for the suggestions; there are a couple of points I should make:

 - I considered switching to DHCP on the server.  The only downside to this is that the server isn't necessarily reliable, and it's somewhat slow.  If it goes down while I'm at work, nobody at home will be able to use the Internet.  That's not really ideal.

 - I have a netbios name set, but for some reason it's not being resolved by clients.  Plus, samba is (by far) not the only (or even the most oft-used) service on this machine.  Does nb name resolution work for non-samba services?

 - All the DHCP hosts can find each other by name.  The router is presumably doing this.

 - Yes, absolutely, it is a crap router.  The only redeeming aspect is that it's free.

 - I still have my old router; I'd rather use the wireless on the new router, since it's faster.  I guess I could have the old router just for DHCP if I need to.  Not really ideal.


Anyway, thanks for the brainstorms so far...  I guess the quick & easy solution might be to enable a second IP address on the server and make it dynamic.  I want to keep a static just because I have a lot of things set to go to it by IP right now (proxy filtering, e.g.) and I want to be able to find it in the event name resolution doesn't work.
Have you considered simply disabling dhcp on the new router, and let the old one handle dhcp?

---

### Post by Morbius1 on 2012-07-18
> - I have a netbios name set, but for some reason it's not being resolved by clients.If you have reset the "name resolve order" to have bcast first on all your machines and they are in fact in the same subnet ( bcast only works within a subnet ) - and I'm guessing they are if they are all connected to the same router then the only things that will stop it are:

** Firewall is in the way.
** The name service isn't running. Check it:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```I have never come across a situation where given the constraint of being in the same subnet that bcast + a 15 character or less netbios name didn't work. I suppose it's possible that your router is blocking broadcast but I personally haven’t come across that.

[COLOR=Blue]**BTW**[/COLOR], I'm assuming that Samba itself is functioning. 

Can you access the server by ip address:
```
smb://192.168.0.100
```Or using mdns ( avahi ):
```
smb://netbios-name.local
```

---

### Post by lykwydchykyn on 2012-07-18
> **Morbius1 said:**
> If you have reset the "name resolve order" to have bcast first on all your machines and they are in fact in the same subnet ( bcast only works within a subnet ) - and I'm guessing they are if they are all connected to the same router then the only things that will stop it are:

** Firewall is in the way.
** The name service isn't running. Check it:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```I have never come across a situation where given the constraint of being in the same subnet that bcast + a 15 character or less netbios name didn't work. I suppose it's possible that your router is blocking broadcast but I personally haven’t come across that.

[COLOR=Blue]**BTW**[/COLOR], I'm assuming that Samba itself is functioning. 

Can you access the server by ip address:
```
smb://192.168.0.100
```Or using mdns ( avahi ):
```
smb://netbios-name.local
```

Samba's running fine; but, honestly, if I have to touch every machine I might as well edit the hosts file and be done with it.

---

### Post by volkswagner on 2012-07-18
> **lykwydchykyn said:**
> 

 - All the DHCP hosts can find each other by name.  The router is presumably doing this.

 

Can you set a static lease on the isp provided router?  If you can associate your servers mac address with it's ip address in the router settings, this will give you the necessary static ip, but allow the server to get the dhcp from the router (the same ip every time) thus the router will be aware of the hostname as with other dhcp clients.

I'm guessing the limited functions on the router did not allow this?

---

### Post by papibe on 2012-07-18
> **volkswagner said:**
> Unfortunately this will create a double NAT situation, but I fee as though you will struggle with that isp provided router.

Unless the natty router can be set as bridge (AT&T example [here]("http://www.att.com/esupport/article.jsp?sid=KB401764&cv=801,902&title=Connecting+a+non-AT%26T+provided+router+to+your+AT%26T+Internet+connection#fbid=2g_7fiEvuSa")).

Regards.

---

### Post by Morbius1 on 2012-07-19
> **lykwydchykyn said:**
> Samba's running fine; but, honestly, if I have to touch every machine I might as well edit the hosts file and be done with it.
Fair enough. But if you accessed the other machine via mdns or can even  ping it that way ( i.e., ping netbios-name.local ) then you no longer have to browse to the other machine to access the share you can connect to it directly and bookmark it. WIndows, Linux, and OSX do mdns.

Anyway, If you can't set the Netgear router in bridge mode then Cascade it:

(1) Set up the old router as stand alone without connecting it to the internet and connect one machine to it.

(2) Reset the old router's ip address to be different from the main router. For example, if the main router has a lan side ip address of 192.168.0.1 then make the old routers ip address: 192.168.1.1. Then disconnect the machine.

(3) Connect a [COLOR=Blue]**LAN**[/COLOR] port of the main router to the [COLOR=Blue]**WAN**[/COLOR] port of the old router.

(4) Have all of the machines on your lan connect to the old router.

** From the main router's perspective it is supplying DHCP to only one client and that's the old router. It will have a WAN side ip address consistent with it being a client of the main router.

** But all of the PC's which are connected to the old router have ip addresses consistent with being a member of another subnet. 

** Just make sure that all your PC's are connected to the the old router and not a mix of the 2 routers because if you do you will be in 2 different subnets.

I searched the internet in hopes of finding an explanation that is perhaps more coherent than what I posted and found this:
[http://www6.nohold.net/Cisco2/ukp.aspx?pid=80&vw=1&articleid=3733](http://www6.nohold.net/Cisco2/ukp.aspx?pid=80&vw=1&articleid=3733)

Option2 is what I'm taking about here: **Cascading the Linksys router to another router (LAN-WAN)**

---

### Post by lykwydchykyn on 2012-07-19
> **volkswagner said:**
> Can you set a static lease on the isp provided router?  If you can associate your servers mac address with it's ip address in the router settings, this will give you the necessary static ip, but allow the server to get the dhcp from the router (the same ip every time) thus the router will be aware of the hostname as with other dhcp clients.

I'm guessing the limited functions on the router did not allow this?

Correct, it sadly has no such function.

---

