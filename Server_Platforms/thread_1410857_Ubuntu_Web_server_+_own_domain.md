---
title: "Ubuntu Web server + own domain"
date: 2010-02-19
forum: Server Platforms
---

### Post by Madsls on 2010-02-19
Hi, i dont know if i have post this right.

I look after a simple guide to setup own Webserver whit own Domain like madsls.cd or madsls.org

I have look on google an see i need DNS server, Phpmyadmin, Apache2, and more. but i need to configer fhe files and i dont know how to do it, i dont understand the guides. some one the know a Video Guide or a simpel web guide the tould all so esey, so noob like me can understand it :) i will bee happy if some one can help me. right now i have install Apache2, phpmyadmin, php5. Hope some one can help me :)

I use ubuntu Desktop 9.10

---

### Post by Madsls on 2010-02-19
No one the can help me?

---

### Post by mcarrara on 2010-02-19
You didn't say if you are from the US or not, but I will assume you are.  If not some ISP issues may be different.

1. Do you have a domain name?  You can't just pick an name and use it.  It must be registered with a domain registrar.  I use godaddy.  There is a yearly cost.

2. How do you connect to the Internet?  This where location matters. In the US you are not usually given a static IP address when you sign up for the Internet.  You must have a static IP address to run an web host.  Next is speed.  When you are told the speed of your connection that is a) optimistic and b) only one way.  Two way speed is MUCH slower.  With a web host you need fast two way speed.  What bandwidth capacity do you have?  ISP's don't like normal customers running web servers so they will put a cap on you capacity, go over the cap and you can be disconnected permenatley.  All this costs extra money for you connection.

3. Security, remember it is the WORLD wide web.  Every script kiddie and professional hacker will be looking for security holes in your system.  Do you have a hardware firewall?  Are you using IPchains?  Don't know?  You will be hacked within the first day.  Scary isn't?

4. Why do you want to host your web site?  If it is to learn how, then just run a intranet site, then the first three issues go away.  Set up one computer as the web host and connect another as the client, but NO outside connections.

You can see the setting up a web host is not a small job and we haven't even begun to discuss the software on the server.  That is why many small and medium companies rent space on severs from companies the host web sites for a living.  With many of these companies you just create the site and upload it to the server and sit back.  They do all the hard work.

Still want to do it your self?  Then there is no quick 5 minute tutorial.  Configuring Apache  alone will take you a lot of studing and practice and mistakes.  Setting up PHP is not that tough, and you will have you ISP set up your DNS when they sell you that static IP

My opinion go with a web hosting company.  There are dozens of good ones and hundreds of OK ones.  You can find one by searching the web or asking around.

Mark

---

### Post by Madsls on 2010-02-19
thanks,

I want to try to build my own host server, where i can make my own server. and make a bissney out of that, my internet is not the best, 10*1 but i only what to try it. when i can make a webserver, DNS server and all that. so i want to make a bisseny company. where i can sell website for thw world. but first now i just want to lern to how. and after that, get a bit internet, and start a company. i dont have a firewall right now, but i can get one, but maby not the best. but when i have a company i will get one.ofc. my IP is dynamic so i know it's can be a problem. but i will get a static IP.

Im from Denmark, i use Cable.

Sorry for my bad engelish. hope you can understand me.

---

### Post by KnottyMars on 2010-02-19
> **Madsls said:**
> thanks,

I want to try to build my own host server, where i can make my own server. and make a bissney out of that, my internet is not the best, 10*1 but i only what to try it. when i can make a webserver, DNS server and all that. so i want to make a bisseny company. where i can sell website for thw world. but first now i just want to lern to how. and after that, get a bit internet, and start a company. i dont have a firewall right now, but i can get one, but maby not the best. but when i have a company i will get one.ofc. my IP is dynamic so i know it's can be a problem. but i will get a static IP.

Im from Denmark, i use Cable.

Sorry for my bad engelish. hope you can understand me.

I think all of the questions that the previous posted outlined are very good ones to consider. If you want to try a server before you put one on the web, that would be my recommendation. This will give you a chance to mess with the configs and test the box out. I went through about 5 fresh installs before I was confident enough to put it on the web. 

I would not recommend a desktop program and install server services on it. I tried that at first and my box was hacked a couple times. In my attempts to make a nice gui server, I neglected to lock it down like I should. Now I use a server version of ubuntu and only install the services that I need. 

My first attempts with Ubuntu Server 8.04 went well, but it took a while before I wasnt reaching for the mouse anymore and just stuck to the keyboard to enter commands. Once you get a LAMP server up and running (I would add SSH too), hopefully you have an additional PC with a desktop OS to access the server and test it out in a LAN environment. When you get used to getting Apache2 MySQL server and SSH locked down and secure, start messing with virtual hosting to serve more than one website. Then look at Shorewall for a firewall solution. As you learn these basics, it will help you understand how to admin your server properly. 

There is another world of networking that deals with domain registrars and DNS that you will have to understand to point traffic to the right IP address. Godaddy is ok, but I prefer network solutions since they include a DNS manager that lets me change DNS records whenever I want (not sure if you can do that with godaddy or not) 

Another thing I saw you mention was that you wanted to sell things online. This involves the inclusion of SSL certs for encrypted traffic to ensure your customers credit card and personal information are safe. Usually this involves alot more setup with apache and using additional ports (443) for encrypted traffic. 

I dont mean to discourage you, this is all possible and really this is a great operating system to work with. Ive been at it for a little over a year and Ive learned alot in that time. Just keep at it, keep installing and playing and you will get better and better. For a server tho, keep it in the server operating system, Ubuntu desktop really shouldnt be hosting websites and DNS info along with MySQL databases and such.

Good luck

---

### Post by pwicken on 2010-02-19
If you just want to try it on and you have got a Ubuntu desktop running I think the easiest way is to install the webserver using **tasksel**.
[https://help.ubuntu.com/community/Tasksel]("https://help.ubuntu.com/community/Tasksel")

You could also try a free DNS-host as DynDNS or other.

---

