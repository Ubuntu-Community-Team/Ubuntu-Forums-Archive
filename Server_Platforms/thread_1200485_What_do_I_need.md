---
title: "What do I need?"
date: 2009-06-30
forum: Server Platforms
---

### Post by kyle99 on 2009-06-30
Hi! I'm looking to install a web server in my basement with an old computer. The computer is only a couple years old, but it has 2gb of ram and a 250gb hard drive, so it should do fine. I'm wondering what do I need to have a web server. I have internet through Comcast, if that matters. I think that I NEED to buy a domain, but is it absolutely required? What other things do I need?

Thanks a lot in advance :)

~Kyle

---

### Post by kixome on 2009-06-30
I recommend your own domain name, though you can just use your ip address since comcast's ips rarely change, and apache is probably hands down the best web server thou maybe not so noob friendly.

---

### Post by kixome on 2009-06-30
Oh, you will have to configure any firewalls to allow traffic to port 80 for http, 21 for ftp and so on.

---

### Post by kyle99 on 2009-06-30
> **kixome said:**
> Oh, you will have to configure any firewalls to allow traffic to port 80 for http, 21 for ftp and so on.

Ok, so I don't really need anything to buy. Do you know any noob-friendly ubuntu server tutorials?

Thanks :)

~Kyle

---

### Post by LepeKaname on 2009-06-30
If you don't want to buy a domain, you can always free name-to-ip services like no-ip.com between others. I suggest to buy a domain if you are planning to have different subdomains for each site like: pics.mysite.com music.mysite.com and so on...

As kixome suggested, install LAMP if you know or want to learn to create dynamic websites with PHP or just install apache or lighttpd if you just want simple HTML content.

---

### Post by kyle99 on 2009-06-30
> **LepeKaname said:**
> If you don't want to buy a domain, you can always free name-to-ip services like no-ip.com between others. I suggest to buy a domain if you are planning to have different subdomains for each site like: pics.mysite.com music.mysite.com and so on...

As kixome suggested, install LAMP if you know or want to learn to create dynamic websites with PHP or just install apache or lighttpd if you just want simple HTML content.

Alright, so just install LAMP on my machine, and then configure the firewalls, and that's it?

---

### Post by windependence on 2009-06-30
> **kixome said:**
> Oh, you will have to configure any firewalls to allow traffic to port 80 for http, 21 for ftp and so on.

I don't know where you are, but Comcast has to be one of the worst ISPs for doing something like this. On all the customers I have, they block port 80 so I don't know how you are serving from a Comcast account.

-Tim

---

### Post by kyle99 on 2009-06-30
> **windependence said:**
> I don't know where you are, but Comcast has to be one of the worst ISPs for doing something like this. On all the customers I have, they block port 80 so I don't know how you are serving from a Comcast account.

-Tim

Oh, so is this not going to work with comcast?

---

### Post by windependence on 2009-06-30
Got to canyouseeme.org and check port 80 to see if they have it open. If it is, you will be able to do it until they figure out what you are doing which will probably only happen if you have tons of traffic.

-Tim

---

### Post by LepeKaname on 2009-06-30
In the case that you port 80 is blocked by your ISP, you can still do it.

This is from no-ip website:

> Port 80 Redirects

Many residential ISPs Block port 80, No-IP Free DNS enables you to run a webserver on a non-standard port, yet users accessing your site never have to enter a port number. For example [http://yourname.no-ip.com/](http://yourname.no-ip.com/) can redirect to [http://yourname.no-ip.com:8833/](http://yourname.no-ip.com:8833/) 

No-ip it is not the only one, so you may search for Dynamic IP's services and choose the one that fits what you need.

---

### Post by doogy2004 on 2009-06-30
> **windependence said:**
> I don't know where you are, but Comcast has to be one of the worst ISPs for doing something like this. On all the customers I have, they block port 80 so I don't know how you are serving from a Comcast account.

-Tim

I have the $69.99 tier on Comcast and I have never had a problem with them blocking any ports.  Just my experience, this may not apply to every Comcast customer/plan/frachise.

---

### Post by kyle99 on 2009-07-01
Alright, thanks for all the help guys, I really appreciate it.

I found out that comcast DOES NOT block port 80, so were good on that.

I setup my lamp server, which can be found at [http://192.168.1.7](http://192.168.1.7), which is a local ip, I think. So what I'm wondering now is how do I get this on the World Wide Web, by just using my IP address? Is there a way to do this without paying?

My IP is 98.225.6.134

---

### Post by LepeKaname on 2009-07-01
Sure, just with your public IP is enough: 98.225.6.134
If you type that IP from any other computer it should work. Just don't forget to allow port 80 in your firewall. 

As I said before, you can use "Name to IP" services so you don't have to pay for a domain name.

---

### Post by kyle99 on 2009-07-01
> **LepeKaname said:**
> Sure, just with your public IP is enough: 98.225.6.134
If you type that IP from any other computer it should work. Just don't forget to allow port 80 in your firewall. 

As I said before, you can use "Name to IP" services so you don't have to pay for a domain name.

Oh ok. Do you see files at 98.225.6.134?

---

### Post by hetx on 2009-07-01
Port 8080 is open and requires a password, if that's right then you're doing good!

---

### Post by LepeKaname on 2009-07-01
The 8080 is not his web server, is his router... because it said: "NETGEAR WNR834Bv2".

[COLOR="Red"][SIZE="4"]You must to change your password of your router... as it has the default!!.
Be aware that someone may change your routers settings![/SIZE][/COLOR]

I think you are missing to assign the port 80 to your local ip (192.168.1.3 or 192.168.1.7)

---

### Post by kyle99 on 2009-07-01
Ok, I've been spending the last 4 hours on this, I can't get it working. I have apache, php, mysql, and all of that installed. I even bought a domain name from GoDaddy, kylet.info. I did a bunch of stuff that different web sites told me to do, and when I go to kylet.info, it shows my www directory, but when I go to kylet.info on other computers it doesn't work. I'm really lost here, anybody know what I should do?

Thanks :)

Kyle

EDIT:

AHHHHHHH YES I THINK I FINALLY HAVE IT :D

Can you go to kylet.info and see if anything shows up?

---

### Post by LepeKaname on 2009-07-01
Yes, I can access to kylet.info.

Cheers!

---

### Post by kyle99 on 2009-07-01
> **LepeKaname said:**
> Yes, I can access to kylet.info.

Cheers!


YAY! Thanks for the help guys :D

---

