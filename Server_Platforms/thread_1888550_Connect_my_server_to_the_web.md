---
title: "Connect my server to the web?"
date: 2011-11-29
forum: Server Platforms
---

### Post by nickos on 2011-11-29
Hey everyone.
I want to host my websites on the internet.
I have ubuntu 11.04 and istalled mysql,apache2,php.I can type localhost and i get the "it works!" message.

How do i configure apache to turn it into a web server?

Thanks!

---

### Post by arrrghhh on 2011-11-29
If it works on your LAN, there's nothing you need to configure on Apache.

The configuration that needs to happen is on your router - how is the server connected to the internet?  Are there any hardware firewalls restricting access?  Do you have UFW enabled?

Basically you need to punch holes thru any firewalls (software/hardware) to your server.  Port 80 is the default for apache/most web sites (the browser defaults to this port for unsecured pages... 443 for SSL).

If you have a dynamic WAN IP, you might also consider something like dyndns so you can automatically update the domain register to your new IP.  If this is for a business, I would highly encourage a static IP and a real domain hosting service tho.

---

### Post by nickos on 2011-11-30
> **arrrghhh said:**
> If it works on your LAN, there's nothing you need to configure on Apache.

The configuration that needs to happen is on your router - how is the server connected to the internet?  Are there any hardware firewalls restricting access?  Do you have UFW enabled?

Basically you need to punch holes thru any firewalls (software/hardware) to your server.  Port 80 is the default for apache/most web sites (the browser defaults to this port for unsecured pages... 443 for SSL).

If you have a dynamic WAN IP, you might also consider something like dyndns so you can automatically update the domain register to your new IP.  If this is for a business, I would highly encourage a static IP and a real domain hosting service tho.


thanks for the reply,is there any tutorial to help me achieve that?[http://localhost](http://localhost) seems to work

---

### Post by arrrghhh on 2011-11-30
> **nickos said:**
> thanks for the reply,is there any tutorial to help me achieve that?[http://localhost](http://localhost) seems to work

Yes, so now you need to configure your network.  This isn't an Ubuntu thing (other than if you have a software firewall, like UFW).  UFW is not enabled by default, so you should only have to configure your router.

You've given 0 information about your network, so I guess you just want me to throw you some generic guide...?  Every router is different, but [http://portforward.com/](http://portforward.com/) can help guide you thru how to configure your particular router.

Again, I'm making assumptions here (you need to provide more info!) - if you don't have a router and your server is directly connected to the internet then you don't need to configure anything.  If this is the case, I **highly** recommend configuring UFW.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by nickos on 2011-11-30
> **arrrghhh said:**
> Yes, so now you need to configure your network.  This isn't an Ubuntu thing (other than if you have a software firewall, like UFW).  UFW is not enabled by default, so you should only have to configure your router.

You've given 0 information about your network, so I guess you just want me to throw you some generic guide...?  Every router is different, but [http://portforward.com/](http://portforward.com/) can help guide you thru how to configure your particular router.

Again, I'm making assumptions here (you need to provide more info!) - if you don't have a router and your server is directly connected to the internet then you don't need to configure anything.  If this is the case, I **highly** recommend configuring UFW.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)


i have installed apache2,mysql and php.
I am connected to a wireless router in my house.
That is not the computer i am going to use as the server, i am going to use onother one(just practising on my pc for now)
So how can i turn it into a web server? lets imagine that i have a domain [http://example.com](http://example.com) how can i host in on my own computer?
What more info do i have to give to you really? :P 
My router is intracom netfaster-iad.
Would it be better if i install ubuntu server and not ubuntu natty with apache installed?


Thanks a bunch for your help!

---

### Post by arrrghhh on 2011-11-30
> **nickos said:**
> i have installed apache2,mysql and php.
I am connected to a wireless router in my house.
That is not the computer i am going to use as the server, i am going to use onother one(just practising on my pc for now)
So how can i turn it into a web server? lets imagine that i have a domain [http://example.com](http://example.com) how can i host in on my own computer?
What more info do i have to give to you really? :P 
My router is intracom netfaster-iad.
Would it be better if i install ubuntu server and not ubuntu natty with apache installed?


Thanks a bunch for your help!

I've already given you the info you need.

You need to open a port on the router.  Assuming you've purchased a domain name, you'll need to then point the domain name to your IP.  Dyndns is free, but if it's for a business you should definitely purchase a domain name.  A static IP is a really good idea as well.

---

### Post by nickos on 2011-11-30
hey man,sorry for dbpost,but i found this tut:

[http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick](http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick)

do you find it trustworthy?

---

### Post by arrrghhh on 2011-11-30
> **nickos said:**
> hey man,sorry for dbpost,but i found this tut:

[http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick](http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick)

do you find it trustworthy?

Linode is a good service, I'd say that's a good guide.

---

### Post by nickos on 2011-11-30
alright man thanks for the help!

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
is this okay?should i get my other pc going and follow that tutorial?Will everything be okay?

---

### Post by arrrghhh on 2011-11-30
> **nickos said:**
> alright man thanks for the help!

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
is this okay?should i get my other pc going and follow that tutorial?Will everything be okay?

Yeesh.  That tut really holds your hands... I can't say for sure if it's good, there's no way I'm reading through every step.

---

### Post by nickos on 2011-12-01
i seem to understand,but can you explain me step 8?

---

### Post by arrrghhh on 2011-12-01
> **nickos said:**
> i seem to understand,but can you explain me step 8?

What do I need to explain?  That step (as the rest of that guide) is pretty thorough.  Every router is different, you need to figure out how to forward the port to your server.  portforward.com will help you here.... (lol, this is already mentioned in this guide).

I honestly don't know how to explain it any better than is in that guide.  The creator of the guide was pretty verbose...

Just one pitfall, I would NOT use DMZ.  I would only forward the individual ports necessary for web access (typically just 80).

---

