---
title: "Changing Listen Port?"
date: 2009-06-21
forum: Server Platforms
---

### Post by avynth on 2009-06-21
Hey, I'm clumsily bumbling my way through setting up a web server on my computer, and I've almost got it, but have run into a slight snag: my ISP blocks port 80. So I've decided to reroute my traffic through port 8080. I've changed Apache2's listen port to 8080 in the ports.conf file and forwarded port 8080 on my router to the server computer. Now here's where I can't make the connection: making incoming requests to *site.com* redirect through port 8080. I use NameCheap as my domain registrar, and use their dynamic dns update client to keep my ip address up to date. I was wondering if anybody was familiar with NameCheap and knew if there was a way to automatically redirect those requests to port 8080? I really would rather not resort to using yet another web site to facilitate the redirect if at all possible.

---

### Post by windependence on 2009-06-21
This is not the proper way to do what you want to do. The main configuration file is located at /etc/apache2/apche2.conf. Open it with a text editor and find this line:

```
Listen 80
```

Replace with the following line


 ```
Listen 8080
```
 Save the edited file
Restart Apache

 sudo /etc/init.d/apache2 restart


-Tim

---

### Post by Failbot on 2009-06-21
> Now here's where I can't make the connection: making incoming requests to site.com redirect through port 8080.
I don't know anything about NameCheap, I've always used a free zoneedit.com account for my DNS service instead of letting the name registrar handle it. I then create a WebForward from [www.mydomain.com](www.mydomain.com) to mydomaindomain.com:8080. You can use the "cloak" feature if you don't want people seeing the :8080 in the URL at the top of their browser.

I'm not sure if NameCheap have a similar feature, but that's the sort of thing you are looking for. Zoneedit.com does provide a dynamic ip update feature as well, so you could change over to them for your DNS service in the worst case scenario.

---

### Post by avynth on 2009-06-21
> **windependence said:**
> This is not the proper way to do what you want to do. The main configuration file is located at /etc/apache2/apche2.conf. Open it with a text editor and find this line:

```
Listen 80
```

Replace with the following line


 ```
Listen 8080
```
 Save the edited file
Restart Apache

 sudo /etc/init.d/apache2 restart


-Tim

I've looked at apache2.conf, httpd.conf, and ports.conf, and the only one that had any line about Listen was ports.conf. apache2.conf had no reference to it and httpd.conf was completely blank. For me, at least, Listen was in the ports.conf file.

> **Failbot said:**
> 

Quote:
Now here's where I can't make the connection: making incoming requests to site.com redirect through port 8080.

I don't know anything about NameCheap, I've always used a free zoneedit.com account for my DNS service instead of letting the name registrar handle it. I then create a WebForward from [www.mydomain.com](www.mydomain.com) to mydomaindomain.com:8080. You can use the "cloak" feature if you don't want people seeing the :8080 in the URL at the top of their browser.

I'm not sure if NameCheap have a similar feature, but that's the sort of thing you are looking for. Zoneedit.com does provide a dynamic ip update feature as well, so you could change over to them for your DNS service in the worst case scenario.


*sigh* I was really hoping to avoid having to register for yet another website. I'll look into it later today, thanks.

---

### Post by avynth on 2009-06-21
okay WHOOPS! I'm not exactly sure what I did, but I restarted my computer and now I'm not connecting to the internet (wired) at all. A quick rundown of things I've done: changed apache listen port to 8080, figured out the url redirect for namecheap, mmm, assigned a crontab job before even all this to use namecheap's dynamic dns client and forwarded port 8080 to the server computer.

So yeah... I really have no idea what I did now and I'm not sure how I would test to see what I did wrong. Any ideas anyone?

---

### Post by avynth on 2009-06-21
Okay, I think I've tracked down my only snag right now, and it has to do with the /etc/network/interfaces file. It originally looked like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

and (per the guide I was following) I changed it to this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

address 192.168.1.2

netmask 255.255.255.0

network 192.168.1.0

broadcast 192.168.1.255

gateway 192.168.1.1

```

When I returned the interfaces file to its original state and restarted my computer, the internet worked again. Curiously, when I attempted to reach my router while the modified interfaces file was in effect, the usual [www.routerlogin.com](www.routerlogin.com) would not work, but typing in 192.168.1.1 did work.

Here is a link to the guide I was using (although slightly out of date, I was following it as best as I could: [http://www.corey-m.com/blog/?p=314](http://www.corey-m.com/blog/?p=314)

------------------------------------------------
edit: okay, nevermind, the internet seems to be working again now for no apparent reason after another restart with no changes, however I will leave this information up if it is of any help. I still can't get my computer to respond to pings...

---

### Post by E_K on 2009-06-22
you have to know what your telling it to do

```
address 192.168.1.2

netmask 255.255.255.0

network 192.168.1.0

broadcast 192.168.1.255

gateway 192.168.1.1
```

That has to be correct, though applicable to many routers, this is sometimes not the case.

for example if your local ip address' are in the format of 192.168.1.X this would be fine though if they are 192.168.50.XXX  like most sweex routers for example its the box is asking for an ip in a range the router is not willing to give out.

The reason you couldnt contact the router config page from that box is because you told it, it was somewhere else.

Just set everything back to how it was and look in your router config to see if you can give that boxs mac address a static ip and all should be fine, where some people will say this is not the proper way to do it, it is the simplest way to do it with the smallest chance of breaking stuff :)

Hope this helps

---

### Post by avynth on 2009-06-22
Okay, since my last post I've figured out a few things. Yes, I did have my NameCheap setup page configured incorrectly, but a quick chat with tech support got that straightened out. Now I know everything is straight on that end. Now everything seems to be working fine (my server now responds to ping via my domain name from an outside computer as well), except I still can't reach the domain name through the web browser. I type the domain in one computer and it times out, and when I type it in on the server, I get the error: 502 Bad Gateway (connection refused). So the domain name responds to ping, but still won't serve the web page (interfaces file is still the same as before).

(Oh yeah, and the internet on the server otherwise works great now too)

Any ideas?

edit: oh yeah, my router is a Netgear WPN824v2, if that helps

---

### Post by windependence on 2009-06-22
The reason you can't view your websites from inside your NATed network is because your router, like most SOHO routers does not do NAT reflection. 

What's really happening is that your router, when doing a DNS lookup on your domain name, resolves it to your outside static IP as it should. Your outside IP is not inside your network, so the router does not know where to send the request, and you get a timeout. You would think that the router would simply send the packet out to the internet and then it would come back in, but that is not the way routing works. 

So, to find your server from the inside, you put an entry into the /etc/hosts file on your client machine to tell it what IP to resolve the domain name to. Of course, you can always access the server using the IP of the server, which requires no DNS lookup.

Hope this makes it a bit clearer.

-Tim

---

### Post by mbeach on 2009-06-22
I don't see any reason you need apache to listen on 8080. Leave it with the default 80, but port forward public 8080 to your server's ip and private port 80 (to use dlink's terminology).

some routers won't resolve back to themselves, not sure if yours is one of those. If you are testing from the same lan as your server, edit your /etc/hosts file to have your domain point to your server's internal ip address. Once you are satisfied that Apache is serving up correctly, then ensure NameCheap is configured correctly.

edit: if testing from a windows machine, the hosts file is in c:\windows\system32\drivers\etc

---

