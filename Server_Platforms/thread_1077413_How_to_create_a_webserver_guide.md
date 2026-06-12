---
title: "How to create a webserver guide?"
date: 2009-02-22
forum: Server Platforms
---

### Post by Bankai56 on 2009-02-22
Ok i got Ubuntu interpid ibex on my pc and wondered how i could host a webpage.
This is only for learning purpose so my "Homepage" just consists of a few lines of html. But i would still like to lern how to use my Ubuntu to host it. 
I want it in the end that my friends or so can acces the webpage under [www.xxxxxx.com](www.xxxxxx.com) xx=name :)
How do i do that?
Thx in advance.
P.s. I am working with the normal ubuntu not the server version. That one will only come in 6 weeks and i already want to have the basics.
Thx

---

### Post by Iowan on 2009-02-22
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is one place to start.

---

### Post by Bankai56 on 2009-02-22
Hey thanks for the fast reply, but the website doesn't open. It says an error or doesn't open at all.
I love this forum for the fast replies.

---

### Post by Kareeser on 2009-02-22
You want just a plain webserver to display html files?

```

sudo apt-get install apache2

```

Then type "localhost" into your web browser, and voila!

You can edit the configuration at: /etc/apache2/sites-available/default
You can edit the pages at: /var/www

If you'd like advanced functionality, such as PHP rendering and a MySQL database, follow **Iowan**'s instructions above

---

### Post by Bankai56 on 2009-02-22
OK thanks i found out how to edit the html file.
But how do i make it public. Because now only i can see it.
I tried the website of IOWAN, but it won't open i get an error.
It says:
```
ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: http://help.ubuntu.com/community/ApacheMySQLPHP

The following error was encountered:

    * Unable to forward this request at this time. 

This request could not be forwarded to the origin server or to any parent caches. The most likely cause for this error is that:

    * The cache administrator does not allow this cache to make direct connections to origin servers, and
    * All configured parent caches are currently unreachable. 

Your cache administrator is webmaster.
Generated Sun, 22 Feb 2009 17:43:43 GMT by yangmei.canonical.com (squid/2.6.STABLE18) 
```

---

### Post by koenn on 2009-02-22
that's a problem at canonical, where that page is hosted. Nothing you can do about it.

try again, it seems to be up now.

---

### Post by Bankai56 on 2009-02-22
oh perfect thank you i will test it immediatlly!
But how do i make it public and let it be viewed by everybody on the www.

---

### Post by Bankai56 on 2009-02-22
Sorry for the double post.
Found out the how to solve the problem. is written in the tutorial. :D:D
I can only start following next weekend. I hope it will run without a problem. But my pc always tends to have problems.:(:(

---

### Post by Bankai56 on 2009-02-27
Ok i did the tutorial i can open the webpage with my internal ip 192.168.1.100
I could do that with apache alone so why did i install mysql and php and how do i set it, that other people outside my network can acces the webpage and how do i do a portscan to see which ports are open?

---

### Post by cariboo on 2009-02-27
I would suggest setting up a static ip address for your server and use port fowrding on your router.

To check if your isp is blocking ports you can use  [canyouseeme]("http://www.canyouseeme.org/").

Jim

---

### Post by Bankai56 on 2009-02-27
OK i found my ip but how do you set it up?

---

### Post by Iowan on 2009-02-27
Most routers provide an option to port-forward.  Most "modern" routers also have a browser-accessible configuration page, yours is *probably* at 192.168.1.1.

---

### Post by Bankai56 on 2009-03-12
Yeah found that but what name should i give in the portforwarding field and how do i know which port to use?
Can i change the port some wehere.
In the end the ip should looke something like 192.168.1.100:230
I know i have to change that ip with my outgoing.
Thx for your patience and help;)

---

### Post by Grey08 on 2009-03-12
Hi, I m doing the samething as what you are doing. So far i have solved with the Port Forwarding, but still, even the port forwarding is set, the page in /var/www wouldn't show up.

The port for web page normally is 80, so, in the rule you need to set is, 192.168.1.100:80

Hope this can help you to set port forwarding.

Does anyone know why the index.html wouldn't show even the port forwarding is set?
Could it be firewall? or?

---

### Post by Bankai56 on 2009-03-12
oh ok thx but what name should i give?
It's written name startingport endingport and typ and ip and enable.
But which app?
They said that maybe your isp blocks the port try a diffrent one or check the website [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by BkkBonanza on 2009-03-12
I think <name> is for your own reference and doesn't matter. Start port 80, end port 80, type would be TCP, ip should be the local server machines ip, eg. 192.168.1.100 and enable should be checked.

What you're doing is telling the router that any packets coming in for port 80 should be forwarded to this machine to port 80. Web servers only use TCP (not UDP). It's also true that your isp cannot be blocking traffic for port 80 - some do that. If they do you may be able to use some higher port like 8080 successfully. You would then need to forward router port 8080 to port 80 on your local server. 

You were asking about using a name to get to your site publicly. To do that you need to register a domain name or alternately if you like get a subdomain name on dyndns or some other service. Either way you then need to get the domain name pointing to your router's ip. If you have a static ip then it nevers changes and you only do this setup once. Most home type services do not use static ip's and so it changes quite often. In that case you need to google about dynamic dns and use a service like dyndns to keep your name pointing to your often changing ip address.

Also note that you don't need php and mysql to host plain html pages. PHP is a scripting language for making more complex programmed pages, and mysql is a database for storing data that may be used in building pages. But since you have those apps now it means that you could easily install Wordpress and have a blog running. There are many great other apps you can run on php/mysql. But just for plain pages you could remove them and save some memory and cpu cycles.

---

