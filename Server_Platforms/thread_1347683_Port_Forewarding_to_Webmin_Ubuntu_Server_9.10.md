---
title: "Port Forewarding to Webmin Ubuntu Server 9.10"
date: 2009-12-06
forum: Server Platforms
---

### Post by MadHatter21 on 2009-12-06
Ok so heres the deal, Basically in a nut shell I wanted to make a server that could tunnel my http traffic from a remote computer, sort of like a proxy, by using the program called Webmin. I have sucessfully made the server and it works just fine on my own subnet so I know that it works, but i need to remotely access Webmin from a different place. Im pretty sure i have to set up my modem and or router to foreward any https connections to that server and send them to the specific port for this program Webmin to run on. Not sure how much sense im making to anyone so if questions please ask.

Madhatter21

---

### Post by ubhi on 2009-12-07
for webmin default port is 10000 for https 443

so you can access by opening 10000 & 443 port for that local ip of that server where webmin is installed. [do it in your router]

then you can access remotely by any palce

[https://your_public_ip:10000](https://your_public_ip:10000)

---

### Post by MadHatter21 on 2009-12-07
how do i open the port for https on the server? once i do that do i still need to set up some sort of port forewarding from my router?

---

### Post by bodhi.zazen on 2009-12-07
You open a port by installing and starting a server.

Are your running a firewall on the server ? If so, open a port in your firewall (by default there is no active firewall in Ubuntu, ie the firewall is permissive).

Forward the relevant ports from your router to your server, this varies with router.

---

### Post by MadHatter21 on 2009-12-07
Thanks alot for the help, I can set that up but how do i get a static ip in my subnet for the server? Ive tried everything and its not working

---

### Post by bodhi.zazen on 2009-12-07
I assume you are asking how to do this from the command line ;)

First you need to know your network and netmask.

List them with :

```
ifconfig
```

Note the "Mask", this is your netmask,

Now , bring down your networking 

```
sudo service networking stop
```

Edit /etc/network/interfaces

```
sudo nano /etc/network/interfaces
```

Assuming you want your server to have an ipaddress of 192.168.0.10 ...

Use this:

```
[FONT=monospace]
[/FONT]auto eth0
iface eth0 inet static
address 192.168.0.10
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1
```

Start networking

```
sudo service networking start
```

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

If you have gnome installed , you set these parameters in network manager.

---

### Post by MadHatter21 on 2009-12-08
Would it make a difference if i had a router inbetween the modem and server?

So my gateway would be to the router which would go to the modem or just straight to the modem?

Madhatter21

---

### Post by bodhi.zazen on 2009-12-08
No, just specify the correct gateway.

You may need to add your router ip to /etc/resolv.conf

```
nameserver 192.168.0.0
```

---

### Post by MadHatter21 on 2009-12-08
No, just specify the correct gateway.

## How do i find the gateway? what is it?

You may need to add your router ip to /etc/resolv.conf

## nameserver 192.168.1.1 ??? that is the ip to my router

I just posted this in a different thread... 

I am editing the interfaces file:

[FONT=monospace]
[/FONT]```
auto eth0
iface eth0 inet static
address 192.168.0.10
 netmask 255.255.255.0
 network 192.168.0.1
 broadcast 192.168.1.255
 gateway 192.168.1.1
```


But I am pretty sure i am not getting the correct info. Now eth0 is up but cannot resolve any websites and i is not because resolve.conf it is definetly the information above. How exactly do i get the information for each one of those. Just to let you know I would like the ip to be 192.168.0.10 and i have a router at 192.168.1.1 as well as my modem on 192.168.0.1, help

Madhatter21

---

### Post by bodhi.zazen on 2009-12-08
Well, you have to be on the same network a your router ;)

so, if your router is 192.168.1.1 , use an ip of 192.168.1.10 for the server

gateway is your router's ip, put this info in /etc/network/interfaces as well as /etc/resolv.conf

---

### Post by MadHatter21 on 2009-12-08
YESS! Great Success! So im almost positive its working. how can i know for sure? i have pingged google successfully and have a ip of 192.168.1.10!!!!

madhatter

---

### Post by windependence on 2009-12-08
[http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

-Tim

---

