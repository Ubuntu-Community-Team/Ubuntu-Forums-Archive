---
title: "Email Server Setup.. From step one."
date: 2009-05-09
forum: Server Platforms
---

### Post by TheMagician001 on 2009-05-09
Hello everyone.. I am a newbie to the linux forum still having trouble figureing out where to start. But loving the linux world .. I have been reading the forums but am still not sure where to start so I just going to let you know what I want to accomplish and hopefully someone in this wonderful world of linux that knows what they are doing.. will take me under their wings and be my mentor. and Hopefully this thread will help some other newbie user....

I am a new business owner who wants to cut my expensis drastically. I also have allot of computer knowlege.. But but my knowlege is more in the BBS industry.. but that is long gone lol.. so here is my plans for my linux server

My linux server is going to be at a remote location (MY SHOP) I want to be able to have remote access from home to work on it etc..  (MY HOME COMPUTERS ARE 100% LINUX) but need my server to be able to serve email, files, webpage, calender (schedling software), etc.. All this needs to be compatible with winblows as well because my employees are still winblows users. My email server I would like it to be POP compatible as well as be able to log in remotely like (hotmail) 

So if anyone is able to mentor me thru my first server setup I would really appricate it.. email is my number one concern right off the bat....

Here is what I know....

I need a Static IP address from my ISP (WORKING ON THIS)
I need a Domain Name.
         - Where is the best place to register this for what I want to do?
         - Rememeber I want to be able to run and maintain my own servers

Thank-you in advance
   Mike

---

### Post by kustomjs on 2009-05-09
Mike here what you all need you can host your site on DHCP address if you use services like no-ip.com or similar sites. But its best to have a static IP address from your ISP. Yes you would also need a domain name I would go with godaddy for cheap domain names. Also do you have extra computer that you could put the server software on by any chance? and far as email I would use postfix+mysql+courier+roundcube for webmail if you need it. If you need any config settings for email server could help you out if you PM me about it. for webserver I would use LAMP+webmin added for it.

Also I could get a good firewall behind your server before going live. router I going to say is smoothwall if you know how to set that up and if you dont you can always PM me and ask me how to setup smoothwall. also smoothwall requires a other computer with very small specs on that. I also forgot on smoothwall you can have openvpn so your employees can login from there home to your internal network and still access everything from internal IP.

---

### Post by TheMagician001 on 2009-05-09
I have some older computers that i could use as well as a fairley new computer i would like to use for all the main processing. I beleave once my internet gets changed to bell business account next week i get a static ip and they will give me a domain of my own that i can change where my dns servers are etc.

how many computers am i going to need to make my setup? and what hardware (routers, switches, etc) am i going to need to get ready for next week?

---

### Post by ugm6hr on 2009-05-09
Sorry I can't help directly (I changed my home server to FreeNAS), but I think your best bet is to install Ubuntu Server with Citadel.  The file server and web server functions will need to be added separately, but Citadel includes everything else you need.

[http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian)

Intrepid+ have Citadel in the standard repos, Hardy is available:
[http://www.citadel.org/doku.php/installation:debian](http://www.citadel.org/doku.php/installation:debian)
[http://ubuntu.citadel.org/ubuntu/hardy/](http://ubuntu.citadel.org/ubuntu/hardy/)

---

### Post by HermanAB on 2009-05-09
Howdy,

Get your domain name at Godaddy and install Citadel.  If you know what you are doing then you have that all running in one evening.

[http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

---

### Post by TheMagician001 on 2009-05-09
Ok I went to godaddy and registered my domain names

mdsmallenginerepair.com
mdsmallenginerepair.ca

now i guess its just a waiting game for my static ip or can I move on to setting up my servers????

Do I need to setup dns servers for my network? Do they go onto 2 seperate computers? So much information to read but i dont know where to start..

---

### Post by kustomjs on 2009-05-09
I have four domain names going to one static IP all my domains are on virtual hosting so and no you really don't need any dns servers just use your ISP dns servers because I am using my ISP dns server for mine.

---

### Post by HermanAB on 2009-05-10
An ISP will usually give you a minimum of 2 static IP addresses.  That should be enough for all your servers, since the services run on different ports, but you can start configuring things using non-routable addresses (192.168.x.y)

You can probably do everything you want to do on one physical machine using Vmware or Virtualbox to keep things separated.

It is possible to do everything on a single server, but then it becomes a maintenance pain, so two or three virtual machines is easier.

You can download a preconfigured Citadel VM - it only needs some basic settings to make it work: [http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)

---

