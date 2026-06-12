---
title: "anybody managed to setup a working ubuntu server in MS virtual PC?"
date: 2008-03-03
forum: Server Platforms
---

### Post by Radio91 on 2008-03-03
Hi

I'm a total newbi to Linux and servers in general and I am currently at college studying web development. One of my classes is web server management and we are using linux sme server installed on microsofts virtual pc in a XP computer. And so far he has got it working as if we are all actually running pcs with Linux sme server installed on them as the OS and all the servers are talking to each other as we can access each others test pages.

My lecturer says there is no reason why the same thing cant be done with any linux version and that an actual real server could be run from within virtual pc in windows XP. I thought this is a great way to learn so Iv installed ubuntu server 7.10-i386 on a virtual PC. So far Iv got the LAMP system installed and I managed to set it with a static ip address within my local network. I then set port forwarding port 80 in my router to the Ubuntu server which it can see.   MY actual ip address from my isp is dynamic but it does not change unless i reset the router. If i type in the local static ip address [http://192.168.1.67](http://192.168.1.67) I can see the apache2-default folder and if I open it I get the message" it works!" in the browser. So I assume this means my server is actually working? However I cannot connect to it via My actual ip address from my isp even with port forwarding set. 

can somebody talk me through what to do next. How do I install some kinda test html page to the www folder in the server via the command prompt? then get it working so I can access it from else where on the net and  log in and configure it remotely? and so on. Id also like to install ftp and some kind of control panel. I looked at webmin but what others are there? I like the look of isp config but im really trying to figure out how to set up a server for a dedicated website. 

all help and advice is appreciated but dont just say look at the server guide because Iv already done that and half of its double dutch to me and is not much help. I have access to the root user and can do some basic commands in linux but thats it.

cheers

---

### Post by Radio91 on 2008-03-04
Even if somebody can help me figure out why my router is not allowing me to view the server from the internet that would be a big help as I can probably figure out the rest myself. The server is clearly working as I get the it work! message from the local ip address.

---

### Post by Alekc on 2008-03-04
> ...I can see the apache2-default folder and if I open it I get the message" it works!" in the browser. So I assume this means my server is actually working? 
Yes

> How do I install some kinda test html page to the www folder in the server via the command prompt? 

Just put your html test page in /var/www/apache-default (until you change DocumentRoot in /etc/apache2/apache2.conf or create some virtual site)
> ... I can access it from else where on the net and  log in and configure it remotely? and so on.

Install openssh-server and openssh-client and you'll be able to access your ubuntu box by using putty from another computers.

I'd suggest to not install ispconfig and similar since for your need it would be better manual way.

> Even if somebody can help me figure out why my router is not allowing me to view the server from the internet 

What do you mean? You can't access it on port 80?

---

### Post by Radio91 on 2008-03-04
Thanks for your reply. 

Yeah as far as I can tell Iv setup port 80 to be forwarded to the local ip address of the server but its not working.  It just times out.

I have this running in virtual pc on xp and have virtual pc set to use the same ethernet card as xp is using for my main connection to the router. Could this be causing a problem? I have dual gigabit lan on my pc so I could set virtual pc to use the other lan connection then get a lan cable and connect it to a different port on my router if that would make a difference?

---

### Post by Alekc on 2008-03-04
It doesn't matter which card you are using. I don't know ms virtual pc (i prefer vmware workstation instead), but you should see if your virtual pc box is visible on your lan or not (if it's bridged it should be visible on all pc on the lan and router). 

If your router permit it try to ping your ubuntu box directly from router and see if there is any reply. If not try to check network settings for virtual machine, especialy type of connection. In vmware there are 3 kinds: Bridge (the one you need), host only, nat, dunno in virtual pc.

---

### Post by MjrNuT on 2008-03-04
> **Radio91 said:**
> Hi

I'm a total newbi to Linux and servers in general and I am currently at college studying web development. One of my classes is web server management and we are using linux sme server installed on microsofts virtual pc in a XP computer. And so far he has got it working as if we are all actually running pcs with Linux sme server installed on them as the OS and all the servers are talking to each other as we can access each others test pages.

My lecturer says there is no reason why the same thing cant be done with any linux version and that an actual real server could be run from within virtual pc in windows XP. I thought this is a great way to learn so Iv installed ubuntu server 7.10-i386 on a virtual PC. So far Iv got the LAMP system installed and I managed to set it with a static ip address within my local network. I then set port forwarding port 80 in my router to the Ubuntu server which it can see.   MY actual ip address from my isp is dynamic but it does not change unless i reset the router. If i type in the local static ip address [http://192.168.1.67](http://192.168.1.67) I can see the apache2-default folder and if I open it I get the message" it works!" in the browser. So I assume this means my server is actually working? However I cannot connect to it via My actual ip address from my isp even with port forwarding set. 

can somebody talk me through what to do next. How do I install some kinda test html page to the www folder in the server via the command prompt? then get it working so I can access it from else where on the net and  log in and configure it remotely? and so on. Id also like to install ftp and some kind of control panel. I looked at webmin but what others are there? I like the look of isp config but im really trying to figure out how to set up a server for a dedicated website. 

all help and advice is appreciated but dont just say look at the server guide because Iv already done that and half of its double dutch to me and is not much help. I have access to the root user and can do some basic commands in linux but thats it.

cheers

Hey Radio91,

I have done the exact same thing as you.  Host OS is XP Pro and running MS VPC 2007 and successfully installed the Ubuntu 7.10 Server LAMP.  I have all the components of the LAMP working.

Alekc has helped with some of your items and i concur with them.  

Let me see if I understand your latest issue.

You have forwarded the 80 (http) to the IP address of the VPC Ubuntu installation.  Now, the only way to confirm that is working is to go to a PC off the LAN of your VPC.  Why, b/c it's external.  Locally, you have already confirmed it works.  Not sure if you tried the following though:

1.  In VPC, you've accessed the apache correctly as stated previously (i.e.,// localhost/....)

2.  Go to your HOST OS, XP, and you should be able to access it as well.  Enter the //IP address/...

3. Go to another PC on your campus, I would guess it would be on the campus LAN and No. 2 should work again??? 

4.  If No. 3 doesn't work, you need to know the Ip address of the router.  I can't tell if you know, but the router IP will be different from the IP addresses of your HOST and VPC.

I hope that helps, unless I misunderstood something, then we'll try again.

(btw- im running my server w/ the Desktop GUI)

---

### Post by matt79 on 2008-03-04
Hi, 
I am running a ubuntu server on a pc too. I had it so I could connect to it from a ssh connection out on the web. But that was port 22. I could not access it through the web port 80. I think my ISP blocks port 80. As to adding a page to the www folder I did it through ssh. However, you have to use this command to allow you to add files.
 "sudo chown username /var/www"

if you do not you might get these errors:
Permission denied.
Error code: 3
Error code:message from server: Permission denied
Request code: 3

---

### Post by vpsville on 2008-03-04
It sounds like your router is not forwarding port 80, probably nothing to do with Ubuntu.

---

### Post by Radio91 on 2008-03-04
Ok my router is a Thomson speed touch st585. according to an online guide to enable port forwarding on this router the host system has to have a static ip address so I followed the guide and set it to static.  the link is here [http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/HTTP.htm]("http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/HTTP.htm")

So as far as I can tell the ports are forwarded correctly. I can see Ubuntu on the network from my router and I can access it from the browser in xp from the local ip address. The public ip address of the router is  79.68.108.141 according to a website that shows your ip address. 

so Iv no idea why this is not working. Can somebody try and connect via that ip addy for me? 

Oh and my isp is tiscali and they say they dont block any ports

---

### Post by MjrNuT on 2008-03-04
> **Radio91 said:**
> Ok my router is a Thomson speed touch st585. according to an online guide to enable port forwarding on this router the host system has to have a static ip address so I followed the guide and set it to static.  the link is here [http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/HTTP.htm]("http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/HTTP.htm")

So as far as I can tell the ports are forwarded correctly. I can see Ubuntu on the network from my router and I can access it from the browser in xp from the local ip address. The public ip address of the router is  79.68.108.141 according to a website that shows your ip address. 

so Iv no idea why this is not working. Can somebody try and connect via that ip addy for me? 

Oh and my isp is tiscali and they say they dont block any ports

That IP address does not resolve anything when I try it.

How did you statically assign?  

This is how I did it:

Have you seen this Guide: [http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/)

---

### Post by Radio91 on 2008-03-04
I pritty much followed the exact same thing to set the static ip of Ubuntu

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

You see the part where it says address this is not the actual ip address of your xp system you use here is it. You just assign any number to the last digits right?

can you try [https://79.68.108.141/](https://79.68.108.141/)  now. It does not resolve to anything in my browser but it should'nt correct?

---

### Post by matt79 on 2008-03-04
it looks good from what I can see but I _*think*_ that you have to change the address to the static one like this.

auto eth0
iface eth0 inet static
address 79.68.108.141
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


have you tried your server on a local computer that is hooked up to the same gateway?

btw with a netmask of 255.255.255.0 you can change anything on the ip address after the last dot.

---

### Post by Radio91 on 2008-03-05
that dot seem right to me because you would be assigning the external ip address of the router to the Ubuntu server within your own network.

I thought the idea was you gave the server its own static ip address on your network then forwarded the ports from the external ip address to the static ip addy on your own network.

---

### Post by Radio91 on 2008-03-05
When I try to trace the ip address from another computer away from my home network it say my ip address resolves to 

79-68-65-9.dynamic.dsl.as9105.com 

My current ip address is 79.68.65.9

so maybe im doing something wrong with the dns ?

When i specfiy the dns servers in the resolv.conf I put in the ip address shown as the dns on my routers info page should I have put dynamic.dsl.as9105.com in or something.

---

### Post by MjrNuT on 2008-03-05
> **Radio91 said:**
> I pritty much followed the exact same thing to set the static ip of Ubuntu

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

You see the part where it says address this is not the actual ip address of your xp system you use here is it. You just assign any number to the last digits right?

can you try [https://79.68.108.141/](https://79.68.108.141/)  now. It does not resolve to anything in my browser but it should'nt correct?

It looks like you and Matt are getting close.

Currently, you have said for your Ubuntu to have an ip address of *.10, considering everything else is correct.  The other items will be with respect to your router settings.

Now, I did not edit anything in the resolv configuration file.  I would suggest you put that back to default, if you remember, since fundamentally we need to get the raw pointers working correctly (i.e., IP addresses).

Your router just needs to forward port 80 to the *.10 address.

Router (public IP 79.68.108.141/) -->  statically assigns the HOST OS XPs IP address one of 2 ways:

1.  via MAC address as one way (*.9).  
2.  Could also use the LAN properties to obtain static IP rather than DHCP.

The settings file that you've been working w/ is specific to the Ubuntu install, which is similar to the obtaining Static like Option 2 above.

You would just make your router forward port 80 to *.10.

Done.

Your address currently does not resolve anything from my end.

---

### Post by Radio91 on 2008-03-05
But thats what Iv been trying to do I have forwarded to .10 and it just doesn't work some how. 

Im going to wipe the ubuntu and try again with fresh ip and reset my rounter so I get another ip.

---

### Post by Radio91 on 2008-03-05
ok Iv re-installed everything and set virtual pc to use my other lan connection to connect to the router. Iv not set a static ip address in Ubuntu or edited anything, all iv done is gone into my router and click on the Ubuntu test server and left it DHCP but clicked the check box to use the same ip address every time. I then set port forwarding in my router to point to the test server and it seems to be working. I can now connect to it via my current ip address of  [http://79.68.73.233/](http://79.68.73.233/).

please try it and let me no if it shows you the index of page.

edit:

Okey Iv had external verification IT WORKS!......  But where do I go from here? Do I now set it to a static ip or will the " use the same ip every time"  in the router DHCP settings be enough? Can I now set up some kind of dynamic DNS and get a domain name pointing to this server?

Iv now managed to install SSH and webmin control panel as well.

---

### Post by matt79 on 2008-03-05
DHCP is a automatic ip addressing done by routers. They can change if the server is turned off or if the lease time, on the ip,  is up. I would change it to a static one if you know how. You should be able to use the same ip on your server just make it keep that ip by making it static.

What you might want to try is "ifconfig" write down the info there and then edit interface 0 (assuming that is the networking card you are using) and put in the info you got from the ifconfig page only make it static. That way you have everything the same only not DHCP.

You also might want to make your router not be able to "dish out" the ip the server is using. Iif it deals it to another computer you will have a network conflict.

---

### Post by matt79 on 2008-03-05
BTW I clicked on your ip address and it worked for me.

---

