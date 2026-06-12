---
title: "Just need you to test my server"
date: 2011-03-18
forum: Server Platforms
---

### Post by waddle1463 on 2011-03-18
I want to know if my server works with the whole world wide web and not just localy. Ive installed apache and all that, i just need to know if when you click this ip address that it loads and shows the apache default page. Here it is:
[http://192.168.1.144/](http://192.168.1.144/)
If it works, put WORKS, if it doesnt put FAIL
Thanks to all who helped

EDIT: try this URL: [http://69.242.39.62/]("http://69.242.39.62/")
It might work

---

### Post by matt_symes on 2011-03-18
Hi

> **waddle1463 said:**
> I want to know if my server works with the whole world wide web and not just localy. Ive installed apache and all that, i just need to know if when you click this ip address that it loads and shows the apache default page. Here it is:
[http://192.168.1.144/](http://192.168.1.144/)
If it works, put WORKS, if it doesnt put FAIL
Thanks to all who helped

That's a private IP address. FAIL

Look at [http://www.dyndns.com/](http://www.dyndns.com/) for url forwarding or find your public IP address. You will also need to open ports on your router.

Lock your server down

Kind regards

---

### Post by SeijiSensei on 2011-03-18
> **waddle1463 said:**
> I want to know if my server works with the whole world wide web and not just localy. Ive installed apache and all that, i just need to know if when you click this ip address that it loads and shows the apache default page. Here it is:
[http://192.168.1.144/](http://192.168.1.144/)
If it works, put WORKS, if it doesnt put FAIL
Thanks to all who helped

Everything in 192.168.0.0/16 is private and not routed over the public network.  I can tell you right now that no one can see your server.  If you're behind a router, you'll need to forward its external port 80 to the server.

---

### Post by matt_symes on 2011-03-18
Hi

> **SeijiSensei said:**
> Everything in 192.168.0.0/16 is private and not routed over the public network.  I can tell you right now that no one can see your server.  If you're behind a router, you'll need to forward its external port 80 to the server.

Spot on. The Sensei is exactly correct.

.... and also 192.168.1.0/24 which what i suspect you are using.

I will say it again, lock your server down.

Kind regards

---

### Post by Rasa1111 on 2011-03-18
yep, sorry man,
 FAIL.

---

### Post by waddle1463 on 2011-03-18
Thanks so much, thats all i needed to know,

---

### Post by waddle1463 on 2011-03-18
> **matt_symes said:**
> Hi



That's a private IP address. FAIL

Look at [http://www.dyndns.com/](http://www.dyndns.com/) for url forwarding or find your public IP address. You will also need to open ports on your router.

Lock your server down

Kind regards

Okay, thanks for the help, but could you explain what ports to open and how to do it, and what i need to enable on dyndns. Also whenever i go to my external ip address(public) it sends me to router config. Please explain as best as you can, im sort of a noob, been working forever on setting this server up

---

### Post by matt_symes on 2011-03-18
Hi 

Sorry. I am just about to go to bed (timezones :) ). There are plenty here who can talk you through it and if they don't i will respond tomorrow.

Kind regards

---

### Post by waddle1463 on 2011-03-18
o.k. 
Would be nice if someone helped me here

---

### Post by nickleboyblue on 2011-03-18
step one: set up your server with a static ip address from your router.

Step two: set up your router to do port forwarding on port 80 to your server.

Step three: get a free account at dyndns.com to point to your ip address.

NOTE: the service provided by dyndns requires your router to "log in" once in a while with a password in order to update your WAN ip address in their records.  A lot of routers support this, but some do not.  If yours does not, you'll have to go through the motions yourself every time your ISP changes your WAN IP address.

You see, in the internet, domains are always linked to an ip address.  If that ip address is a router, that router will examine it's settings and, if port forwarding is enabled, will send all outside requests forward to whichever machine port forwarding is configured for if they are in the specified port.  The default for web browsers is port 80.

Putting a website on your server and making it available on the internet will not make it visible, as it is a private address.  Only those to whom you give the address will even know it exists.  Therefore, if you want to test access to it, you should probably not post it on a forum, but instead, do it on your own time with a laptop outside of your server's network.  That way, you can keep your address private.  Unless you have a team of very skilled developers who have configured your server to be safe and secure, you will not want to make the address on it publicly known.

---

### Post by stmiller on 2011-03-18
You can use something like ipchicken to check your home ip address:

[http://ipchicken.com/](http://ipchicken.com/)

This ip address is what would be used to reach your server at home.


(Granted that you setup your router to forward port 80 to your machine at home.)

---

### Post by nickleboyblue on 2011-03-18
-oh, and while setting up the static IP, you don't necessarily have to set that up on the server its self.  You could just do that on the router.  If the server requests a re-lease of an IP address, the router will give it the same one every time if the router is set up to do that.

From my experience, you should not try to configure things on the server by hand unless you know exactly what you are doing.

---

### Post by crispy_420 on 2011-03-19
Most routers have an option to bind a device to an IP address, kind of like a permanent lease from DHCP (through MAC?). Then port forward the necessary ports to server (http=80 and https=443) through the router configs. As far as the dydns service that is also done through your router configs and is a free service.

How bout letting us know make/model of router to assist if config setup.

---

### Post by wolfbuddy on 2011-03-19
Don't forget to check with your ISP for a static IP address for your connection with them, otherwise you may find that it changes every time your router reboots. Setting up a fixed address in the router for the server on your internal network should be easy, it's done by the MAC address of the server's NIC. I have every machine on our network set up like this, even phones, to prevent any kind of odd address conflicts.

---

### Post by CharlesA on 2011-03-19
> **wolfbuddy said:**
> Don't forget to check with your ISP for a static IP address for your connection with them, otherwise you may find that it changes every time your router reboots.

That's why you set up dyndns. :) So if your ip changes, the address is updated to point to the new ip.

---

### Post by waddle1463 on 2011-03-20
If you didn't see my edit,  I followed your instructions and need you to test this URL: [http://69.242.39.62/]("http://69.242.39.62/")
Tell me if it works or not
Thanks

---

### Post by wojox on 2011-03-20
```
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
```

---

### Post by waddle1463 on 2011-03-20
Awesome, by the way, I created a temp. Ip for my router to forward to, then i used dyndns to forward that address to my external static ip, at least that's how I think it works.
Next on my list: setting up dns servers
Anyone wanna explain a summary of how you would setup dns?

---

### Post by jerenept on 2011-03-20
> **waddle1463 said:**
> Awesome, by the way, I created a temp. Ip for my router to forward to, then i used dyndns to forward that address to my external static ip, at least that's how I think it works.
Next on my list: setting up dns servers
Anyone wanna explain a summary of how you would setup dns?

Why would you want to set up a DNS server?

---

### Post by CharlesA on 2011-03-20
Shouldn't need any DNS servers if you are using dyndns.

---

