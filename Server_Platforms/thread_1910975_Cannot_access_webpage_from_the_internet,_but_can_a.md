---
title: "Cannot access webpage from the internet, but can access it via loopback"
date: 2012-01-18
forum: Server Platforms
---

### Post by mohitdaksh on 2012-01-18
Hello, I need to setup a web server at my home computer for some college project. I have installed apache2.
I made some sample html files,saved them in "/var/www". I can access the website when I use the loopback address 127.0.0.1 but when I try to run the website using my dynamic  IP address but finding it from the available websites on the web it opens up my router configuration page instead of the webpage. And when I try to open it from other computers then it does not send anything. 

I have opened port 80 for HTTP requests from anyone in the firewall settings.
```
mohitdaksh.linkpc.net
```This is the domain I have created by the one of the dynamic DNS websites and it should point to my web page.


I do not know much about hosting and may be missing something obvious although I have tried working according to the tutorials. Can anyone please guide me?

---

### Post by Savio2010 on 2012-01-18
You need to configure port forwarding on your router/firewall, that all incoming connections on port 80 are forwarded to your server.

Google for port forwarding

---

### Post by haqking on 2012-01-18
> **mohitdaksh said:**
> Hello, I need to setup a web server at my home computer for some college project. I have installed apache2.
I made some sample html files,saved them in "/var/www". I can access the website when I use the loopback address 127.0.0.1 but when I try to run the website using my dynamic  IP address but finding it from the available websites on the web it opens up my router configuration page instead of the webpage. And when I try to open it from other computers then it does not send anything. 

I have opened port 80 for HTTP requests from anyone in the firewall settings.
```
mohitdaksh.linkpc.net
```This is the domain I have created by the one of the dynamic DNS websites and it should point to my web page.


I do not know much about hosting and may be missing something obvious although I have tried working according to the tutorials. Can anyone please guide me?

Is port 80 set to forward to your machine IP on the router ?

The dynamic DNS will go to your router, but your router needs to port forward port 80 requests to the machine running the web service.

Cheers

---

### Post by mohitdaksh on 2012-01-18
Thank you very much haqking and Savio2010. 
Embarrassingly, I do not know anything about port forwarding and that it was needed. I will look up on google about what needs to be done and how it needs to be done. Thanks once again :)

---

### Post by haqking on 2012-01-18
> **mohitdaksh said:**
> Thank you very much haqking and Savio2010. 
Embarrassingly, I do not know anything about port forwarding and that it was needed. I will look up on google about what needs to be done and how it needs to be done. Thanks once again :)

It depends on your router.

log in to your router, often the setting page for it is simply called port forwarding, sometimes not thought but it is usually self explanatory.

Enjoy

---

### Post by mohitdaksh on 2012-01-18
Okay I followed a guide from [here  ]("http://www.boutell.com/newfaq/creating/hostmyown.html")although its not specifically for my router ( I could not find any specific info for my router :(  ) I did the following settings in the Virtual Server page for my router configuration menu.

```

Private IP = 192.168.1.3
Protocol = Any
Private Port = 80
Public Port = 80

```

And still the problem is same as before. 
My router is UT-304R2 if it helps..

---

### Post by haqking on 2012-01-18
> **mohitdaksh said:**
> Okay I followed a guide from [here  ]("http://www.boutell.com/newfaq/creating/hostmyown.html")although its not specifically for my router ( I could not find any specific info for my router :(  ) I did the following settings in the Virtual Server page for my router configuration menu.

```

Private IP = 192.168.1.3
Protocol = Any
Private Port = 80
Public Port = 80

```

And still the problem is same as before. 
My router is UT-304R2 if it helps..

[http://envisagedlife.wordpress.com/2008/07/12/port-forwarding-in-ut-304r2/](http://envisagedlife.wordpress.com/2008/07/12/port-forwarding-in-ut-304r2/)

adjust to suit your requirements

---

### Post by mohitdaksh on 2012-01-18
I did see that page after I posted and it is also basically the same thing that I have already done, although the interface of my router is different from there. I don't know whats wrong. I think I will have to ask my ISP to give me a linksys router :(

EDIT: Okay now it seems to work if I enter the current IP address assigned to me by the ISP that means the request is being forwareded correctly. Somehow the domain given to me by the dynamic dns service is not working. I will work it out. Thanks a lot!! :)

---

