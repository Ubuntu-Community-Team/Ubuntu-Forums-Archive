---
title: "New Server install 12.04"
date: 2012-07-15
forum: Server Platforms
---

### Post by pstonge on 2012-07-15
Hey guys, i am new to ubuntu and my boss at work gave me a server to look after, and of course its a server based ubuntu 9.04. Like there is no GUI, and i have no idea where to begin, So i purchased a book, with great commands. I have install server 12.04 at home, and was creating files, and stuff. But then i seen someone post about adding a GUI. sudo apt-get install desktopsomething close to that.My question i guess is, because i now have "desktop" can i still use terminal to "pretend" i was configuring from the command line. To kind of "see" my work. And also, if there is usefull things i should do after a new install, i want to make just a simple file server at home for now, to get fimilier with things. Thanks guys/girls

---

### Post by BkkBonanza on 2012-07-15
Yes. Just use the terminal app on the accessories menu. 

Or to be more like a real server with remote access you can use a second machine and ssh to connect in and do your work. For this you would install openssh-server to get the ssh server running. Then on another machine use ssh to connect. Or if from windows you can putty (which is a popular ssh client).

Using ssh is very common for server admin so it's a good thing to know. eg. If you had a VPS or hosting account or Amazon EC2 server you'd quite likely want to use ssh to manage it.

(ssh is "secure shell", the most popular remote terminal app on linux)

---

### Post by pstonge on 2012-07-15
Hey thanks for that.I familier with SSH, but i am new to server. Never created one before, i just learned about Windows Server 2003 in school, and currently studying for CCNA.
 But iam confused on how to set up my ip address for my linux (home) server to always keep the same static address. 
 
In my windows machine i tried going through TCP/IP, and setting my IP address. Then i looked up the DNS server i was using from ISP, and added that as my DNS server.But when i went and did ipconfig /releaseI lost my connection.
 So i was digging around in my router, 192.168.0.1, and i seen a DHCP enable/disable, but i was unsure whether to disable that or not
 so how to i keep my IP address in ubuntu to staty static..??
 Or should i just submit a new thread?THanks again

---

### Post by LHammonds on 2012-07-15
Check my sig for some step-by-step instructions.  After reading my server guide, you should have a pretty good idea for the majority of the steps required to setup a server.  However, my documentation was under a virtual machine scenario so I did not have to fiddle with hardware-specific drivers which may be problematic for bare-metal installations like yours.

LHammonds

---

### Post by BkkBonanza on 2012-07-16
> **pstonge said:**
> 
 So i was digging around in my router, 192.168.0.1, and i seen a DHCP enable/disable, but i was unsure whether to disable that or not
 so how to i keep my IP address in ubuntu to staty static..??
 Or should i just submit a new thread?THanks again

If your linux server is using DHCP then I expect it would be your router that would be assigning the IP address. You have a few choices on how to keep a static IP on the server. I'll give two scenarios here for you:

1) Set a static IP in your /etc/network/interfaces file. See plentiful examples on google or in the server guide above (or type "man interfaces" at the temrinal). In this case your router doesn't need to use DHCP but if you have other machines on your network and want DHCP then you will want to enable DHCP on the router and set an IP range that doesn't include the static IP of your server. 

eg. /etc/network/interfaces

auto eth0
iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0


2) Enable DHCP on the router and let it make assignments on your network. But tell the router the MAC address of your server and create a "static lease" (name varies by router brand and sometimes they have a "server" config page for this). This forces the DHCP server to always assign the same IP to your server. In this case you want to make sure the /etc/network/interfaces file has the correct DHCP setting on your server. Again see same docs as above method.

eg. /etc/network/interfaces

auto eth0
iface eth0 inet dhcp

In either case if you want your server to be exposed to the internet then you will need to configure a "port forward" on the router as well to tell the router to forward a port (eg. 80 for web server) to the correct static IP of your web server. Again the wording for this varies by router brand and some call it virtual server config.

---

### Post by pstonge on 2012-07-16
Thank you for your imput, i am at work and when i get home i am going to try these out and let you know how that is...
 
Thanks for all the help guys

---

### Post by dirtrider1 on 2012-07-17
Yes it is pretty much standard in most cases for a server to not have a gui running although there are a few web based admin solutions available. Yes even after there is a GUI installed in most cases you will find the command line is still the default method of interacting with Linux in general. 

Once the GUI is installed you can access the terminal through the default Gnome terminal which you will find is basically a regular app on the desktop or you can access the 7 virtual terminals by pressing CTRL+ALT+F(1-6) which will take you out of your current session and into a completely new session without X(GUI) and     [ **CTRL+ALT+F7 to EXIT **]. And of course you could always set up an ssh server and connect from another computer as well.

---

