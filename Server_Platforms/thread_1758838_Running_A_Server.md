---
title: "Running A Server"
date: 2011-05-15
forum: Server Platforms
---

### Post by vikkyhacks on 2011-05-15
I am new to ubuntu and i am good at web designing but i don't know how to run a FTP or a Web Server .Please tell me some softwares which run on ubuntu for hosting a website of FTP server. I would also like to know if there is any software to run virtual server and softwares to run INTRANET. I need a GUI software and i don't mind if i have to buy it.

---

### Post by crispy_420 on 2011-06-15
Will this just be a test machine on your local LAN or will you need to upload remotely?

Also, the machine you do your designing on has which OS? Windows or Linux?

---

### Post by kroq-gar78 on 2011-06-15
> **vikkyhacks said:**
> I am new to ubuntu and i am good at web designing but i don't know how to run a FTP or a Web Server .Please tell me some softwares which run on ubuntu for hosting a website of FTP server. I would also like to know if there is any software to run virtual server and softwares to run INTRANET. I need a GUI software and i don't mind if i have to buy it.
I'd love to help if I can, but I'm not sure what you want to use your GUI for. GUI for server management? GUI for making your HTML (or whatever) files? There is one maini program for the web hosting (local, at least; I'm not exactly sure how to use it over the internet): apache2. It's for windows, too, but as far as I know, no GUI. I think (not sure, but you definitely can through command line/console) you can install it through Software Center by searching "apache2".

---

### Post by nirab on 2011-06-15
Web Server : Apache 
FTP server : TFTPD
Intranet: Open VPN
Virtulization : VirtualBox

I however do not understand what you mean when you say you want GUI  software. In my opinion these are the best solutions available.

---

### Post by vikkyhacks on 2011-06-15
Thanks for the reply ,I don't need softwares to edit HTML, I need to know how to host a website(over Internet or INTRANET), I need to know about a linux webhosting for managing and running websites .And is there any softwares like APACHECONF for linux.

---

### Post by nirab on 2011-06-15
If you are looking for Graphical tool for configuring apache server then there is a tool called webmin

as there are downsides to using a graphical tool for configuring apache servers i  recommend you to edit configure file manually.

This link might be  helpful :

**[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch20_:_The_Apache_Web_Server)**

---

### Post by crispy_420 on 2011-06-15
I don't think there is a decent graphical tool to manage apache, sorry for that piece of bad news. If I'm wrong let me know but I have yet to see one. 

There are free options for for dynamic dns hosting as well. This can be done with many home routers and involve the services of DynDNS. What they do is provide a way to track your dynamic IP address and give a free host name too.

Also there would be setup of said router to forward the appropriate ports to your server. That depends on the capabilities of the router but should be possible on even low-end units.

So the steps I would follow would be:

1) Setup and test apache locally. Make sure it works.
2) Harden the server to prevent attacks.
3) Setup router to forward appropriate ports. Most likely 80 and maybe 443 if you are use SSL.
4) Setup DynDNS account and configure router for the service.

This is really basic but it should provide a rough guide.

---

### Post by greentrees on 2011-06-15
I use Virtualmin it can host multiple sites and is a simple install.  It's incredibly comprehensive which will seem quite daunting to start with.  You'll need to be running Ubuntu 10.04 either the 32 or 64 bit version.

---

### Post by kroq-gar78 on 2011-06-15
> **crispy_420 said:**
> I don't think there is a decent graphical tool to manage apache, sorry for that piece of bad news. If I'm wrong let me know but I have yet to see one. 

There are free options for for dynamic dns hosting as well. This can be done with many home routers and involve the services of DynDNS. What they do is provide a way to track your dynamic IP address and give a free host name too.

Also there would be setup of said router to forward the appropriate ports to your server. That depends on the capabilities of the router but should be possible on even low-end units.

So the steps I would follow would be:

1) Setup and test apache locally. Make sure it works.
2) Harden the server to prevent attacks.
3) Setup router to forward appropriate ports. Most likely 80 and maybe 443 if you are use SSL.
4) Setup DynDNS account and configure router for the service.

This is really basic but it should provide a rough guide.
+1,

good ideas

---

### Post by lisati on 2011-06-15
I use DynDNS for my main web site's domain name, apache2 to deal with incoming requests to view my web page, webmin for a browser-based management of my server, and ssh for when the command line suits my management needs better. There are one or two other things I've installed to help prevent abuse, but in the interests of a brief reply, I'll skip mentioning those for now.

---

### Post by crispy_420 on 2011-06-15
I say start small and work up to something better over time. Along the way document everything so if there is an issue it will be easier to trace back the issue later. Also don't invest any money yet, see how successful you are first. You can get pretty far for free now.

---

### Post by vikkyhacks on 2011-08-17
Very sorry for the late reply i had trouble accessing my account ,I got my http apache running from ubuntu as well as windows 7,need help on increasing the security ....Any help is appreciated

---

