---
title: "ubuntu server - www user access"
date: 2012-08-04
forum: Server Platforms
---

### Post by interscrilla on 2012-08-04
hi, 

I've installed the latest ubuntu server on my machine I've also  installed webmin (webadmin) both working 100%. my question are below.

1st. How can I put my server/websites live for www users to access?

2nd. Can I somehow configure webmin (webadmin) to do the job of question number 1?

Please post back with any helpful information, 

[LEFT] Thanks.[/LEFT]

---

### Post by Bachstelze on 2012-08-05
> **interscrilla said:**
> 1st. How can I put my server/websites live for www users to access?


Install Apache (or some other HTTP server) and forward port 80 in your router (if your ISP allows it).

> 2nd. Can I somehow configure webmin (webadmin) to do the job of question number 1?

No, this is something to be done on your router, Webmin has no control over it.

---

### Post by interscrilla on 2012-08-06
Hi Bachstelze, Thanks for the reply

I've figured it out but now I'm in another problem.

every time I access my domain, on a public network I end up on the main /www folder which is the default and wont directly let me access my other website for example...

I made two sites in /www folder and name them after my registered domain example.com 

edited Apache2 folder var folder and hosts file, enabled port 80 and setup A records to registrar, now every time I try to access my domain I end on the default /www folder.

**Index of /**

 [IMG]http://joinwink.com/icons/blank.gif[/IMG]Name Last modified Size Description
 [IMG]http://joinwink.com/icons/text.gif[/IMG]index.html05-Aug-2012 05:18  177
 [IMG]http://joinwink.com/icons/folder.gif[/IMG]my registered domain 1.com/05-Aug-2012 09:08    -
 [IMG]http://joinwink.com/icons/folder.gif[/IMG]my registered domain 2.com/05-Aug-2012 09:07    -     

Apache/2.2.22 (Ubuntu) Server at my domains .com Port 80

I've tried giving index.html a different name also but it still wont let me access my domain directly but instead I have to click on my domain to access it.

I hope I made my point across please ask if you need more information.

Thank You in advance for your important time and great help.

---

### Post by ubudog on 2012-08-06
Try:
```
sudo a2dismod autoindex
```

Best,
ubudog

---

### Post by rukiaEnix on 2012-08-06
Do you want access to two sites each one with its own domain?

---

### Post by interscrilla on 2012-08-06
Okay so I did manage to get it online within my network, so if I'm to type the url within my network range I do end on the right website.

I tried accessing my websites from multiple different networks and unfortunately none of the website responded.

can any one know what can be the problem?

@rukiaEnix Yes I have multiple domains registered with godaddy which I would like to use on my server via apache2/ubuntu server.

please guys help me out... as for now website/urls are only accessible through my network. I have enabled port 80 and also have setup my A records at godaddy as well.

---

### Post by rukiaEnix on 2012-08-06
You need to open the 80 port in your router and also NAT your public IP to the private IP of your server (that's also inside the router).

---

### Post by interscrilla on 2012-08-07
@rukiaEnix Thank you, but if you read my previous post I did mentioned that the port80 is enabled with the IP of this machine which I'm using for server. A records are also pointed to my public IP address fro godaddy.

I can not find what might be the problem here, any one else would know?

Thanks

---

### Post by rukiaEnix on 2012-08-07
Did you modify correctly your virtualhosts?

---

### Post by interscrilla on 2012-08-07
everything is working normal within my network as if I try to access my websites from my external/public ip address from any of my devices including my phone android and iphone or any computer that are connected. but any how if I try to connect/access it from some other network it does not work. so what I think my router is the problem, but I for some reason can not figure it out. Please help me out here...

note: my websites are accessible through my network using multiple computers but not from other networks.

---

### Post by interscrilla on 2012-08-07
So I came to find out today that the port80 is blocked by Cox my internet service provider. I thought I had it enabled it from my router so it would work fine but NO. it was cox who had it blocked. any suggestion on a different port?

---

### Post by rukiaEnix on 2012-08-08
Why you don't try 8080? Or are you already using it? But you need to have this in mind: People we'll have to access your site like this: domain.com:[port].

Example with 8080:

domain.com:8080

---

### Post by interscrilla on 2012-08-08
@rukiaEnix I've enabled 8080 from my router and also have confiremd it that it is not blocked from my ISP and upon running port check online it does shows that the port is open... but yet its not responding to my ip address.

any thing any one could think? again all my sites are accessible through my network but not on the internet...

---

### Post by rukiaEnix on 2012-08-08
Have you tried from outside accessing to your site like this?: domain.com:8080

---

### Post by interscrilla on 2012-08-09
is there a way to bypass example.com:(port#)

I've got it to work, though very disappointed  from the community members who do not like to help. 

Please if any one could guide me in this I'll be very happy and thankful.

server is running on latest ubuntu software, all domains are only accessible through the port only.

example.com(port#)

Thank you for your important time and great help.

---

### Post by rukiaEnix on 2012-08-09
It will only work as domain.com if it uses the 80 port, because it is the default www port. So if you are using a different port you will have to write it.

You could make a trick redirecting an online or cloud server site to your apache_server_ip:8080. An having that site with just site.com

---

