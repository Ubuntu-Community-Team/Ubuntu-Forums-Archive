---
title: "How To Access Website From My Internet Connection"
date: 2012-07-26
forum: Server Platforms
---

### Post by Guy Faux on 2012-07-26
Hi!

I've successfully setup my first LAMP server :) I know this stuff isn't for amateurs; my web server is very restricted and will stay this way. I still have a lot to learn but I feel I have accomplished a huge thing here.

I don't know why (I think I might know why) but I cant access my website from any device on my internet connection unless I go to it's private IP address.

The only way I know how to access the public IP or domain name is through an online proxy server. ie hidemyass . com

Anyway --for testing purposes I'd love _an easy way_ to see the site live without having to access it directly. In other words, experience what a visitor would. I hope this makes sense...

Go easy on me :D it's still my first day...

Thanks!

---

### Post by darkod on 2012-07-26
Step 1. Did you confirm your ISP is not blocking port 80? You can check open ports here:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/). You might need to do the other steps too before you try, or until it works.

Step 2. Are you trying to access it by domain name or public IP? If it's domain name, you have to create A record pointing to your router public IP (or something like dynamic dns) so that typing the domain will make it look for your public IP.

Step 3. Did you forward port 80 (and 443 if you need it) on your router to the private IP of your server on the LAN?

---

### Post by Guy Faux on 2012-07-26
Thanks darkod let me try to clear up any confusion... I kind of had a feeling this would happen and I should have tried to be more clear.

The website works perfectly and can be accessed from any computer on any Internet connection except for mine; the same connection as the server.

I can go to a coffee shop and visit the website at it's www . domain name . com or public IP

However, when I am at home on the same Internet connection as the server I can only access the site if I go to it's private IP address. I believe its connecting directly to the server no?

Hope this clears things up. Thanks for your help!!

---

### Post by Cheesemill on 2012-07-26
You need to add an entry for the site to your /etc/hosts file:
```
192.168.1.1     www.example.com     www
```
Obviously use your own domain name and the internal IP address of your web server.

---

### Post by darkod on 2012-07-26
Well, if it works fine from the outside, why would you want to access it like that too? It should be even faster accessing it from your LAN.

Although I was under the impression too that you should be able to access it by typing the domain.

Just make a host entry as Cheesemill suggested and enjoy the fast access through the LAN.

---

### Post by Guy Faux on 2012-07-26
> **darkod said:**
> Well, if it works fine from the outside, why would you want to access it like that too? It should be even faster accessing it from your LAN.

Although I was under the impression too that you should be able to access it by typing the domain.

Just make a host entry as Cheesemill suggested and enjoy the fast access through the LAN.

Haha Well I'm a bit obsessed with seeing it as a visitor would. It's super fast direct and that's awesome for developing, but I want my site to load in < 2 seconds. For me to feel good about its speed - I just have to see it to believe it...

Thanks a lot guys but holy poo I have no idea how to do this:confused: I'm pretty ashamed to admit that, but if you could instruct me it would be amazingly appreciated!

In the mean time Ill give it a go on my own but Im pretty nervous.

---

### Post by Cheesemill on 2012-07-26
Open a terminal and type:
```
gksudo gedit /etc/hosts
```
Then add the line that I posted above, changing the details to your actual domain and internal IP address.

---

### Post by darkod on 2012-07-26
> **Cheesemill said:**
> Open a terminal and type:
```
gksudo gedit /etc/hosts
```Then add the line that I posted above, changing the details to your actual domain and internal IP address.

Wouldn't that open the website using the LAN and private IP? That's what he does NOT want to do.

He wants to access it like from outside, if I got it right, going outside the router and coming back in.

But shouldn't that just work when you type the domain without having an entry in hosts? Why doesn't it?

To the OP, do you have maybe a domain set up in your home network, or anything mapping the domain name to some private IP (maybe even wrong IP since it doesn't open it by domain from the internal network). Something misconfigured maybe?

---

### Post by Guy Faux on 2012-07-26
Thanks again I added the entry but it didn't work...

>  He wants to access it like from outside, if I got it right, going outside the router and coming back in.Y! This is exactly what I want to do!

> Something misconfigured maybe?:mrgreen: Well my friend would you really be surprised if I did something wrong on my first web server?

>  But shouldn't that just work when you type the domain without having an entry in hosts? Why doesn't it?So this is abnormal then? You're saying I should be able to just go to the website- no problems? 

I am using (temporarily) a DDNS with a free sub DN from no-ip [dot] com until I get my static IPs

Could this be a problem? Hopefully not or I should have mentioned it in the 1st place.

If it helps heres a bit about my current setup:

The server is wired to my Actiontec m1000 DSL router/modem. Everything else is connected through wireless to the Internet via the Actiontec DSL modem. I dont know if this is a proper setup or not... I think I have an old Ethernet hub somewhere if needed (unless I donated it during my last old/obsolete hoard roundup)

---

### Post by kennethconn on 2012-07-26
I think you might need to set your router to update it's dyndns client. However, I think you are nit picking. If it's working it's working, and you said if you are accessing it from a coffee shop it works as expected. I'd focus your time elsewhere.

---

### Post by darkod on 2012-07-26
You have just about reached the end of my expertize. :)

However, I tend to agree with your logic. If everything is configured good on the outside and it works from the outside, typing the domain on your computer should find the website too.

When you want to avoid reaching it from the outside (which you don't want to), you add an entry in your hosts file. Otherwise, the temporary DDNS and sub-DN shouldn't be an issue or it wouldn't work from the outside too.

---

### Post by Guy Faux on 2012-07-26
> **kennethconn said:**
> I think you might need to set your router to update it's dyndns client. However, I think you are nit picking. If it's working it's working, and you said if you are accessing it from a coffee shop it works as expected. I'd focus your time elsewhere.

Well.. It is working... But I'd really like to know if this this normal? If so that's fine but it just seems so weird.

---

### Post by Guy Faux on 2012-07-26
> **darkod said:**
> You have just about reached the end of my expertize. :)

However, I tend to agree with your logic. If everything is configured good on the outside and it works from the outside, typing the domain on your computer should find the website too.

When you want to avoid reaching it from the outside (which you don't want to), you add an entry in your hosts file. Otherwise, the temporary DDNS and sub-DN shouldn't be an issue or it wouldn't work from the outside too.

Thanks for your time. I truly appreciate your advice and help. And I did learn some good stuff from you guys.

Ill keep looking for an outside solution. Online proxy servers work, it's just such a pain...

If you wanna know the truth & it's embarrassing but may help some poor soul reading this thread with the same problem later on down the road. It killed me when I couldn't figure out why I couldn't access the site from my computer at the public IP address or domain name! Of this whole endeavor this little bit was the most frustrating, confusing and time consuming. I spent so much time troubleshooting, cursing and fist-shaking until I finally went to a proxy server and there it was...

---

### Post by Cheesemill on 2012-07-26
There are 2 slightly different problems here with different solutions.

1 - Trying to access your website internally by using your external IP address.

This is all down to the settings in your router, it needs to support packet re-writing (sometimes called NAT loopback) to be able to correctly route packets from your internal network, via your external IP and then back into your internal network.
I've never come across a consumer grade router that offers this option though, only business class routers costing 100's or 1000's of pounds.


2- Trying to access your website internally by using your domain name.

Usually when your browser does a DNS lookup for your domain name it will return the external IP address of your site (you then run into the above problem). However, by adding a line to your /etc/hosts file you can alter that behaviour so that when your browser does a DNS lookup it will return the internal IP address for your website, letting you use your domain name to connect to your site internally.


If you're still not sure what to do after my posts #4 and #7 earlier then post back what your domain and webserver internal IP address are and post the output of:
```
cat /etc/hosts
```and I can tell you exactly what to do.

---

### Post by Guy Faux on 2012-07-31
@CheeseMill

OK Sorry for the break. Thanks a lot for explaining all of this. I get it now. It's really very simple :p

---

