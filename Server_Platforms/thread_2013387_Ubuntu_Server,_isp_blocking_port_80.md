---
title: "Ubuntu Server, isp blocking port 80?"
date: 2012-06-30
forum: Server Platforms
---

### Post by pirates712 on 2012-06-30
Hi,

I'm trying to set up an apache webserver on ubuntu server 12.04 as a sort of educational project. I can access my basic webpage from other computers on the network but when I try using my registered domain it comes back as "unable to connect". I think the problem could be one of two things-

1 - Time Warner is blocking port 80
2-  I'm forwarding port 80 through a linksys router to a dlink router, and from the dlink router to my server. Not a pretty way of doing it but it's the most reliable way to get internet to my server. 

How would I go about checking if either port 80 is blocked or if I'm not forwarding it correctly?

Thanks!

---

### Post by rmaultz on 2012-06-30
Most  Mainstream  ISP  Block Port  80 

you can check using the below link :  
[www.canyouseeme.org](www.canyouseeme.org)

Look further into dynamic Ip  hosting  with dyndns.com  or noip.com  to configure a redirect  to a higher port  Number  say 8080

---

### Post by Ji Ruo on 2012-06-30
> **pirates712 said:**
> 
1 - Time Warner is blocking port 80

I would have said no way but apparently some ISPs do... just give them a call and ask.

> **pirates712 said:**
> 
2-  I'm forwarding port 80 through a linksys router to a dlink router, and from the dlink router to my server. Not a pretty way of doing it but it's the most reliable way to get internet to my server.

How many networks are you going across here? Is it all one network, and the dlink router is acting as a switch? Or do you have two separate private networks (say one 192.168.x.x and one 10.x.x.x)? You might be going wrong with the forwarding here. The simplest way, if you can do it, is to have just one network and the linksys router doing the port forwarding. If you have 2 networks, I would suggest posting all the port forwarding and addressing details and *maybe* it can be fixed.

You can also try using your external IP to access the web pages instead of the domain name, to make sure it is a connectivity issue and not a DNS issue.

---

### Post by kennethconn on 2012-07-01
My first point to troubleshoot this would be to look at the way you are going through a second router. Provide more details on this part of the set-up.
 
As  Ji Ruo posted, always get it working by IP address first, then DNS names.

---

### Post by pirates712 on 2012-07-01
Ok

The linksys router, which is connected to the cable modem, is set up to forward 80 and 443 to 192.168.1.249, which is the static ip address of the dlink router. The dlink router is set up to forward 80 and 443 to 192.168.0.250 which is the static ip of my server. On my server I have shorewall firewall set up to block everything except ssh (22 i believe) and port 80. I've tried stopping shorewall but it doesn't make a difference, except I am unable to ping my server with shorewall running, not sure if that's anything of significance. 

My domain name does resolve to my public IP

My network "interfaces" file looks like this:

iface wlan0 inet static # i'm connecting via a wireless adapter
wpa-ssid network name
wpa-psk network passcode
adddress 192.168.0.250
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1


I'm not sure about anything after "address", so there could a pretty major goofup in there :P


Oh, and I must have changed something because instead of "unable to connect" the browser now comes back as "the server at ____ is taking too long to respond".

---

### Post by computerfox on 2012-07-01
> **kennethconn said:**
> My first point to troubleshoot this would be to look at the way you are going through a second router. Provide more details on this part of the set-up.
 
As  Ji Ruo posted, always get it working by IP address first, then DNS names.

I was just thinking that too actually.  When I first tried to set up my network, I too used two routers and it didn't seem to work.  I took out that second router and BAM, I was live. So deff check this first because it's true that some ISP's block port 80, but if Verizon doesn't block it then it's actually less of a chance that your ISP is blocking yours.

Plus, it doesn't make sense to have two routers, try making things simpler....

---

### Post by Ji Ruo on 2012-07-01
> **pirates712 said:**
> Ok

The linksys router, which is connected to the cable modem, is set up to forward 80 and 443 to 192.168.1.249, which is the static ip address of the dlink router. The dlink router is set up to forward 80 and 443 to 192.168.0.250 which is the static ip of my server.

...

My network "interfaces" file looks like this:

iface wlan0 inet static # i'm connecting via a wireless adapter
wpa-ssid network name
wpa-psk network passcode
adddress 192.168.0.250
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1


I'm not sure about anything after "address", so there could a pretty major goofup in there :P


I'm assuming the internal network address of the dlink router is correct (192.168.0.1)... and that port 80 is not being blocked by your ISP.

you have put the network directive wrong, it should be```
network 192.168.0.0
```

My main concern with your setup is that you are forwarding the port twice, when it is not really meant to be performed more than once. I'm not sure why you have decided to split your home network into two networks, but maybe you have a reason. Having just one network and thus one router would be simpler, so if I were in your position I would see if the dlink can be run as a switch and change the network on all equipment to /16 (network 192.168.0.0, subnet mask 255.255.0.0, gateway would be the internal address of the linksys). 

If you don't want to do that, I would see if you can set up static routes between the linksys and the dlink network, instead of any network address translation and port forwarding you may be doing now. So the linksys would forward all traffic for 192.168.0.0/24 to the dlink, and the dlink would forward all of its non-local traffic to the linksys. Then make sure the linksys is set up to perform network address translation for the dlink's network also, and set the port forwarding for 80 to your server's actual internal address.

---

### Post by darkod on 2012-07-01
Also, another thing you should check (on both routers) is whether port forwarding also means the packet is let through the built-in firewall automatically.

Usually I would expect a configured port forward rule to overturn the firewall, but you never know. The port forward rule is worthless if an activated firewall is killing port 80.

---

### Post by CharlesA on 2012-07-01
That's a complicated setup.

Why are you using both routers to separate subnets?

---

### Post by pirates712 on 2012-07-01
Our house is roughly a square shape, with the linksys router at one corner and my bedroom at the other. In the middle is a large concrete/stone chimney. The signal from the linksys has trouble going through the chimney, so I have my dlink router on the same side of the house connected via ethernet cable to the linksys router. I can't just run the cable directly to my room because my room is on the second floor and the router is on the first. Also, I'm a college student so when I go back to school the router will be coming with me, so I don't want to mess with my parents' wireless network too much. 


I feel so dumb. The main problem was that I didn't check the checkbox next to the port forwarding rule on the dlink router. Major facepalm right there. It works now :guitar:

Thanks for the help!

---

### Post by computerfox on 2012-07-01
> **pirates712 said:**
> Our house is roughly a square shape, with the linksys router at one corner and my bedroom at the other. In the middle is a large concrete/stone chimney. The signal from the linksys has trouble going through the chimney, so I have my dlink router on the same side of the house connected via ethernet cable to the linksys router. I can't just run the cable directly to my room because my room is on the second floor and the router is on the first. Also, I'm a college student so when I go back to school the router will be coming with me, so I don't want to mess with my parents' wireless network too much. 


I feel so dumb. The main problem was that I didn't check the checkbox next to the port forwarding rule on the dlink router. Major facepalm right there. It works now :guitar:

Thanks for the help!

HAHA!  That kind of stuff happens to me all the time too.  Glad you got it up and running.  My advice, if you don't need two routers (which you did kindda mention that it was a necessity), don't use the two.  You want to set up a simple network at home so that you can maintain it with ease.

---

### Post by CharlesA on 2012-07-01
> **computerfox said:**
> HAHA!  That kind of stuff happens to me all the time too.  Glad you got it up and running.  My advice, if you don't need two routers (which you did kindda mention that it was a necessity), don't use the two.  You want to set up a simple network at home so that you can maintain it with ease.
You can always set up the second router as a regular access point by plugging a network cable into a LAN port and disabling DHCP and whatnot on it. I've done that when I needed more wireless coverage. Everything will be on the same subnet and that makes it easier to deal with.

---

