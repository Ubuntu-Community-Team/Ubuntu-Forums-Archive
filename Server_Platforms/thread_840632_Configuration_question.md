---
title: "Configuration question"
date: 2008-06-25
forum: Server Platforms
---

### Post by newbie_andy on 2008-06-25
Hi all,

I have ubuntu server 8.04 installed on "server" (ip 10.1.10.100) and administer it using ispconfig on "PC1" ((os winxp) ip 10.1.10.101).  I have two virtual domains on the server and the websites work okay if I use internet from outside of my lan, but if I use PC1 and type the domain name in the URL, I get my router's login page.  Is there any way for me to access the website from PC1?

---

### Post by Thanoulis on 2008-06-25
Did you try *localhost* instead?

---

### Post by newbie_andy on 2008-06-25
when i type *localhost* into the URL (on PC1), I get websites as if I was searching for it on the web.  Same goes if I type 127.0.0.1 in the browser URL.  

I checked the hosts file on PC1 and all it has is: 
127.0.0.1       localhost

my "server" hosts file (/etc/hosts) has:
127.0.0.1       localhost.localdomain localhost
10.1.10.100     server.innovativesearchit.net   server

---

### Post by newbie_andy on 2008-06-25
oh, and if i add the http:// to localhost, i get "Internet Explorer cannot display the webpage" msg.

---

### Post by chuck jessup on 2008-06-25
change the server's ip address to XXX.XXX.XX.102 instead of XXX.XXX.XX.100 this will prevent the webbrowser from finding teh routers firmware setup. you should be able to do this in this setup, if you need help visit the manu. site and they should be documentation on how to do this. it really shouldnt be that hard to do.

Best Reguards

---

### Post by newbie_andy on 2008-06-25
The router's setup page is actually 10.1.10.1.  I believe my setup is wrong.  I have a static IP.  My provider gave me this information: 

Static IP: 75.145.143.135 (not actual, but close nuff)
Gateway IP: 75.145.143.136 
Subnet: 255.255.255.252

I have my domain name abcd.com, pointing to 75.145.143.136.  This is why I always get the router's login page.  I never really used the 75.145.143.135 address.  Since my router's IP is 75.145.143.136, I have my server and PC connected to it and opened port 80 to my server (10.1.10.100).  Is my setup wrong?  Please help....

---

### Post by Mr_Whippy on 2008-06-26
Edited due to first post being completly of after re reading,

shouldnt your domain abcd.com be pointing to your server ip and not your gateway, as your gateway will be your router and not the server?

---

### Post by newbie_andy on 2008-06-26
I have my server ip as an internal IP (10.1.10.100) and have my router port forward 80 to that IP.  here's my /etc/network/interfaces:

# The primary network interface
auto eth1
iface eth1 inet static
address 10.1.10.100
netmask 255.255.255.0
network 10.1.10.0
broadcast 10.1.10.255
gateway 10.1.10.1
 
I'm not sure how else to set this up.  I think another option would be to enter my public static IP as address and in the router put the server in the DMZ list. I'm confused.

---

