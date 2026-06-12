---
title: "I've got a port forwarding problem"
date: 2007-02-20
forum: Server Platforms
---

### Post by jrobinson5 on 2007-02-20
Here's the deal. I've got a nice little Gateway box I'm using as an Apache server, running Ubuntu Hoary server install (CLI only). It's got a static IP address. I'm trying to get port forwarding working with [the cheap new wireless router I got]("http://www.newegg.com/Product/Product.asp?Item=N82E16833180031R"). Here's the status. I can ssh into the box just fine, both thru the local IP address and thru the WAN IP with port 22 forwarded. I can also access the internet just fine through elinks on the server. However, even after forwarding port 80, I still cannot access the webserver through the wan IP or the DynDNS name. Here's what the router lists on the Virtual Server page:
```
Virtual Server HTTP	TCP 80/80	192.168.1.150
	ssh	* 22/22	192.168.1.150
```

And here's the network settings on the server:
```
=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2007.02.20 21:18:25 =~=~=~=~=~=~=~=~=~=~=~=
login as: jrobinson
Using keyboard-interactive authentication.
Password: 
Linux wwwserver 2.6.10-6-386 #1 Fri Sep 15 12:41:20 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Tue Feb 20 20:39:49 2007 from cpe-70-116-89-51.houston.res.rr.com

jrobinson@wwwserver:~$ sudo /etc/init.d/networking restart

jrobinson@wwwserver:~$ sudo vi /etc/network/interfacescat  /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.0.0
network 192.168.1.0
broadcast 192.168.255.255
gateway 192.168.1.1
jrobinson@wwwserver:~$ exit
logout

```

If you need any more information I will be happy to provide it.
James

---

### Post by featherking on 2007-02-20
try running this to see if your apache is listening on port 80 correctly:

```
netstat -l | grep www
```

You can copy and paste but if it shows nothing then your problem is not your port forward it is your apache. If it returns something like 'tcp 0 0 <ip>:www *:*' then we move to step two..

---

### Post by jrobinson5 on 2007-02-21
```
=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2007.02.21 15:32:37 =~=~=~=~=~=~=~=~=~=~=~=
login as: jrobinson
Using keyboard-interactive authentication.
Password: 
Linux wwwserver 2.6.10-6-386 #1 Fri Sep 15 12:41:20 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Wed Feb 21 15:31:29 2007 from cpe-70-116-89-51.houston.res.rr.com

jrobinson@wwwserver:~$ netstat -l | grep www
tcp6       0      0 *:www                   *:*                     LISTEN     
jrobinson@wwwserver:~$ eisxit
logout
```

If it helps you, be aware that it worked fine on my last router. When I got the new router I had to change some stuff to get static IP to work, and after that the port forwarding on the router wouldn't work. I can still access it just fine by using its local IP address on another computer on the same network.

---

### Post by featherking on 2007-02-21
i tried to click on your link above to see your router but it leads to a newegg search page :/ So what router is it?
Also, its very odd that you are able to access ssh and not www server.. Can you access the www server from your lan? is that what you meant when you said:
> I can still access it just fine by using its local IP address on another computer on the same network.

---

### Post by jrobinson5 on 2007-02-21
Doh! The router is an Encore ENHWI-G, which NewEgg apparently discontinued between when I posted the link and when you clicked it. And yes to your question. I can access it from the lan, but that doesn't help me much when it's a web server.

James

---

### Post by featherking on 2007-02-21
Well i found this [[COLOR="Red"]page[/COLOR]]("http://www.portforward.com/english/routers/port_forwarding/Encore/ENHWI_G/Apache.htm") on setting up apache for your router to see if you needed to do anything special, but it doesnt look all to tricky and im sure youve set it up correctly. Maybe you could read that page to double check your configuration. Another thing i would try is put your webserver in the dmz, Im sure you know about the dmz but in case you dont, the dmz puts a totally open connection between the internet and whatever computer you specify. So when your webserver is in the dmz you wouldnt need any port forwarding rules, and your only protection then is the webserver local firewall.

So if you add the 192.168.1.150 to the dmz page in your router configuration, and you still can access the web server from the internet, then you need to look at maybe a conflicting firewall setting or something. Try the dmz setting and post back

---

### Post by jrobinson5 on 2007-02-21
Everything works fine in the DMZ, which I am quite happy with. Unless there is any reason to do otherwise I plan to stay in this mode. 

I did not know what DMZ was before you informed me. Thank you very much for doing so.

James

---

### Post by featherking on 2007-02-22
Yes the dmz is very useful (esp for pesky game configurations) the only downside is you are making that computer wide open to the internet, so as i said you rely entirely on its firewall.

Having said that, i once had a router that would not port forward either. It really irritated me for so long, i ended up doing the same as you. I put a good firewall on and let it go in the dmz.

Just be sure to check your access logs to make sure no unwanted peoples are getting into your server. Running your ssh on port 22 is a very easy target for example, i usually move mine to another port. But thats just a preference.

Glad you got it working though, congrats

---

### Post by jrobinson5 on 2007-02-22
Yeah, interestingly enough, after trying dmz, I turned it off and reenable port forwarding and it suddenly worked. Increddibly bizarre, but whatever, it works now.

James.

---

### Post by featherking on 2007-02-23
That is bizarre, but you cant complain if its working, however it got that way

---

