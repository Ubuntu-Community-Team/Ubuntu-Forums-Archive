---
title: "xampp server on ubuntu almost working..."
date: 2009-09-19
forum: Server Platforms
---

### Post by woodsonoversoul on 2009-09-19
Hello all. I moved this from the Wireless/Networking board hoping more people might see it here...

I've been developing locally on a little ubuntu netbook with xampp for about 7 months. Two weeks ago I got a computer I'd like to use as a server. I've installed the latest Ubuntu distribution and xampp, moved all my files over, and forwarded port 80. I've also got a domain name from dyndns.com which is being updated by a client which runs in my router (a Netgear WGR6154 v8).

Now, when I try to access my server by typing in the address I got from dyndns.com the browser loads until it timesout. I can access everything locally using localhost as the address so I believe xampp is running, just unable to connect with the internet.

also:
in httpd.conf Listen directive is set to: Listen 80
netstat -a output is here: [http://pastebin.com/ma18ae0d](http://pastebin.com/ma18ae0d)
output of ifconfig posted here: [http://pastebin.com/m35895c8b](http://pastebin.com/m35895c8b)

In order to be able to view my files over the internet what should I do next?

Thanks to all in advance

---

### Post by SoftwareExplorer on 2009-09-19
If you are trying to test the website from the same internet connection as it is on, most routers don't handle that too well. You might test it by using a proxy. This very problem drove me nuts for about a month until someone at ubuntu forums told me it would work for everyone but me!

---

### Post by woodsonoversoul on 2009-09-19
No luck from outside sources either...

---

### Post by woodsonoversoul on 2009-09-22
Bump for fresh eyes...

---

### Post by halitech on 2009-09-22
> **woodsonoversoul said:**
> Hello all. I moved this from the Wireless/Networking board hoping more people might see it here...

I've been developing locally on a little ubuntu netbook with xampp for about 7 months. Two weeks ago I got a computer I'd like to use as a server. I've installed the latest Ubuntu distribution and xampp, moved all my files over, and forwarded port 80. I've also got a domain name from dyndns.com which is being updated by a client which runs in my router (a Netgear WGR6154 v8).

Now, when I try to access my server by typing in the address I got from dyndns.com the browser loads until it timesout. I can access everything locally using localhost as the address so I believe xampp is running, just unable to connect with the internet.

also:
in httpd.conf Listen directive is set to: Listen 80
netstat -a output is here: [http://pastebin.com/ma18ae0d](http://pastebin.com/ma18ae0d)
output of ifconfig posted here: [http://pastebin.com/m35895c8b](http://pastebin.com/m35895c8b)

In order to be able to view my files over the internet what should I do next?

Thanks to all in advance

If you can see the files using [http://localhost](http://localhost) then apache is running and the issue is not with apache.

> **SoftwareExplorer said:**
> If you are trying to test the website from the same internet connection as it is on, most routers don't handle that too well. You might test it by using a proxy. This very problem drove me nuts for about a month until someone at ubuntu forums told me it would work for everyone but me!

I've had 4 different routers (different brands and models) and never had a problem connecting using either my no-ip.com address or dynu.com address. Maybe some older routers didn't handle it well but newer ones should.

Is it possible that your ISP is blocking port 80? Use this site to find out.

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by woodsonoversoul on 2009-09-22
When using canyouseeme.org I get a timeout error. My router configuration says it's forwarded though. The thing that confuses me the most right now is all the different addresses. For instance, I have port 80 on the address my router gave the server forwarded (according to the router), but it won't let me forward a port on the address of the router (the address I see at canyouseeme.org), So a likely possibility is that I have addresses mixed up somewhere, but I have no idea where. I've added to and taken away from all my config files. Would it be a better idea to delete everything and install Ubuntu Server Edition? I know there'll be configurations with that too though, and plus I'm used to xampp. I really just want a single file to be visible to the world from my home server. The process I'm going through makes it seem like an impossible task...

Thanks for the ideas, anything else that might help? I can post anything you need to check...

---

### Post by halitech on 2009-09-22
so it shows your routers external IP address fine but when you enter port 80 in the box and click [check] it times out? Basically its not testing the router in anyway (from my understanding) its simply testing to see if port 80 is blocked or not by your ISP.

When I test, I get this message
```
Success: I can see your service on 24.224.xxx.xxx on port (80)
Your ISP is not blocking port 80
```
(address changed to protect myself from hackers)

---

### Post by woodsonoversoul on 2009-09-22
I was getting that message too until a few days ago when a tree limb fell and knocked out my cable (internet). They came this morning to fix it and now it's saying port 80 is blocked. Nothing has changed in what my router shows me. I don't know how my cable being knocked out could affect my router's port forwarding settings, but nothing else has happened, and I sure haven't been messing with it while it's offline... Do you think Comcast might be blocking port 80 for some reason? I have no idea if they do that or not, but other posters have brought it up...

---

### Post by halitech on 2009-09-22
if it was working and now its not and you say nothing has changed internally (is your IP the same?) then maybe they are now blocking it in your area or maybe jsut yours if they found you are running a server on port 80.

---

### Post by t0p on 2009-09-22
> **woodsonoversoul said:**
>  Do you think Comcast might be blocking port 80 for some reason? I have no idea if they do that or not, but other posters have brought it up...

It's certainly possible that Comcast are blocking port 80.  As it says on [www.canyouseeme.org:](www.canyouseeme.org:)

> Most residential ISP's block ports to combat viruses and spam. The most commonly blocked ports are port 80 and port 25.

Port 80 is the default port for http traffic. With blocked port 80 you will need to run your web server on a non-standard port in conjunction with a port 80/web redirect from No-IP.com. 

So if your ISP *is* blocking port 80, a solution may be to use a different port.  8080 is a common choice, but really you can use any.  The thing to do now though is to tell apache to use a different port, then see if the service is visible.

---

### Post by woodsonoversoul on 2009-09-22
I'm assuming I could do that through the 'Listen' directive in httpd.conf? (I'm still learning :) )

---

### Post by woodsonoversoul on 2009-09-22
Wow. Now it seems like it's sporadically changing. Just a second ago I was looking through my router options and I saw that there was a difference in the IP address the router had listed in "Attached Devices" and the address I had entered in the "Port Forwarding" section. I changed that and canyouseeme.org changed and listed my port 80 as open! But then after trying to connect to site a few times (the address in the url bar changed to the location of the file, ie: ***.com changed to localhost/foldername/index.php, which I don't understand either but it seems like a good thing) I couldn't connect at all and now canyouseeme.org list my port 80 as closed. I know it must be something I did but it only lasted a few minutes, and I didn't change anything. Could having a server running on another machine on the network interfere?

Thanks to all who are responding :)

---

### Post by woodsonoversoul on 2009-09-23
bump for the night crew...

---

### Post by halitech on 2009-09-23
Do you have a static IP set up on the machine in question? Does your router support static IPs based on the MAC address? You need to ensure that the machine will always have the same IP, otherwise the port forwarding will break.

not sure if a server on another machine will affect things or not but it might if its running a web server then posible.

---

### Post by woodsonoversoul on 2009-09-23
I was under the impression that using a service like dyndns.com took the place of a static ip address and that a static ip usually cost extra from your isp. Is this incorrect?

---

### Post by halitech on 2009-09-23
partly correct in that getting a static IP for your connection with the ISP will usually cost more and services like dyndns.com can take the place of having a static IP but I was referring to the server behind the router having a static IP so that it always had the same address.

---

### Post by woodsonoversoul on 2009-09-23
How would I check that?

Thanks for all the help, I really appreciate it...

---

### Post by halitech on 2009-09-23
in the terminal run
```
cat /etc/network/interfaces
``` and post the results

---

### Post by woodsonoversoul on 2009-09-23
cat /etc/network/interfaces returns:

auto lo
iface lo inet loopback

---

### Post by halitech on 2009-09-23
ok, not being managed there as that is only showing the loopback interface

if you look in the network manager, does it show DHCP or static for the connection type?

---

### Post by woodsonoversoul on 2009-09-23
In Network Connections>Edit under IPv4 settings it says that the method is Automatic (DHCP)

---

### Post by halitech on 2009-09-23
since you are using it for a server, I would set it to STATIC and assign the required info so it doesn't change again. Just make sure the IP is out of range of the ones the router may assign to other computers.

the other option, if your router supports it, is to assign the MAC address a permanent IP address so that any time the computer requests an IP, the router will assign that IP address.

---

### Post by woodsonoversoul on 2009-09-23
Through the Network Connections>Edit under IPv4 settings I can change the method to manual and enter additional info., there is a "Static Routes" option in my router, in which I can add static routes, and, also in the router, under "Basic Settings", for "Internet IP Address" I have the options: 
Get Dynamically From ISP
Use Static IP Address

Where should I change it, and where can I find info on subnet mask and gateway ip address? Thanks again, I keep feeling like it's right around the corner...

---

### Post by volkswagner on 2009-09-23
> **woodsonoversoul said:**
> Through the Network Connections>Edit under IPv4 settings I can change the method to manual and enter additional info., there is a "Static Routes" option in my router, in which I can add static routes, and, also in the router, under "Basic Settings", for "Internet IP Address" I have the options: 
Get Dynamically From ISP
Use Static IP Address

Where should I change it, and where can I find info on subnet mask and gateway ip address? Thanks again, I keep feeling like it's right around the corner...

> **woodsonoversoul said:**
> When using canyouseeme.org I get a timeout error. My router configuration says it's forwarded though. The thing that confuses me the most right now is all the different addresses. For instance, I have port 80 on the address my router gave the server forwarded (according to the router), but it won't let me forward a port on the address of the router (the address I see at canyouseeme.org), So a likely possibility is that I have addresses mixed up somewhere, but I have no idea where. I've added to and taken away from all my config files. Would it be a better idea to delete everything and install Ubuntu Server Edition? I know there'll be configurations with that too though, and plus I'm used to xampp. I really just want a single file to be visible to the world from my home server. The process I'm going through makes it seem like an impossible task...

Thanks for the ideas, anything else that might help? I can post anything you need to check...

> **woodsonoversoul said:**
> Alright! Using '192.168.1.3' In my router controls, I was able to successfully forward port 80 (Or at least that's what canyouseeme.org says...) One question I have is, why does canyouseeme.org show a different address than '192.168.1.3'? It shows some 68.52.***.* number. And when trying to load '192.168.1.3' in my laptop's browser it loads it's local 'localhost' page. I've never set a firewall up, so unless one is installed by default in Ubuntu 9.04, then I shouldn't have one. My router is a Netgear WGR614v8. I'll plug my laptop into the router and see if that gives me different results than wirelessly...Thanks for all the advice/suggestions

A word from a fellow newbie.

You need to get the basics down both for your own benefit and for those trying to help you.

I am a newbie so I can offer a little advice.  You need to grasp the difference and purpose of local (LAN) and internet addresses (WAN).

LAN = local area network.  Simply put this is all devices or address location on the house side of your router....usually start with 192.168...but not always.  The purpose for LAN ip address is the world wide web ip scheme does not have enough address "numbers" for every computer, phone, or other internet device.

WAN = Wide Area Network simply put is the WWW.  Your internet provider gives you (your router) this address.  This is the address when typed into an address bar on your favorite browser allows you to find other sites on the web.  Using a domain name needs DNS which basically maps the WAN ip to the domain name.

Both WAN and LAN have subnet mask's and gateway's.  You should be able to find both sets of information from your router config.  On my linksys router the WAN info is found at Status>Router>Internet.  The LAN infor is found at Status>Router>Local Network.

Again both WAN and LAN address can be static or dynamic.  Dynamic has advantages for ISP's as they can have more customers with less pysical addresses.  For a LAN connected laptop via wifi, dynamic may be preferred for easy roaming to different locations.

Again the above is my simplistic view and is my belief you need to understand the above minimal information, to effectively troubleshoot and configure a server or other network settings.

Good luck.

---

### Post by woodsonoversoul on 2009-09-23
Thanks for the advice and an excellent write-up. There needs to be a forum of newbs helping newbs. Thanks again, this definitely opened up my understanding of the matter. GREAT write-up...

---

### Post by SoftwareExplorer on 2009-09-24
Subnet mask is usually 255.255.255.0. Gateway ip would be the LAN ip of your router.
You don't need static routing on your computer, you are looking for something like port forwarding or advanced port forwarding.

---

