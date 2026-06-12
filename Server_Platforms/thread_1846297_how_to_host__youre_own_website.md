---
title: "how to host  youre own website"
date: 2011-09-18
forum: Server Platforms
---

### Post by mujahied on 2011-09-18
There are many ways you can host you're own website 
i have read on some forums and even on howtoforge but didnt find something that was easy for the normal user so i decided to do my own research how to host my own website and be able to type in my browser a website address i am not sure if this will help others if not admins please delete the thread

First off all you will need sa [B]Control Panel/Software for Ubuntu Server

i use hcnix [/B]```
http://hostingcontroller.com/ddirect.html
```reason why i am using this is its easier to control everything and you are able to add more websites on this system easier ps please note if you are using the same as me read the read me file in the archieve

ok when we have done that lets contineu to the next step get youre public ip adress
there are muliple websites where you can get that but i preferr
```
http://www.whatismyip.com/
``` once you have it note it down

ok now lets create an account on ```
http://dyn.com/dns/dyndns-free/
```when you finish creating youre account add a new hostname and point it to youre public ip adress you can choose basicly any subdomain they have available because that will not be youre domain name it will serve as you're dns note it down we will need it for the next step

ok now head down to ```
www.co.cc
``` and create a free domain name 
And setup youre domain using name server type the dyndns link that you have created as name server wait for 24 hours or less you will be able to enter youre public ip thru a link 

i hope with this tut i will be able to help some folks 
ps for how to install a tarball please search the ubuntu forums you will find enough tuts how to do so and others that are using normal sql and php with httpd please make sure u have a proper dns system installed and configured otherwise this will not work

---

### Post by haqking on 2011-09-18
The server would need to be in a DMZ or have port forwarding on the home router to forward port 80 requests to the local LAN ip of the server also.

If it is in a DMZ then it needs to have its own firewall with security tied down, if using port forwarding the the router usually protects the server.

For a home server as you suggested that is ;-)

Peace

---

### Post by fatalfurry on 2011-09-18
I put a switch between my cable modem and my home router. That way I have two public ip addresses. One for my "server" (old laptop) and the other for my personal home network.

---

### Post by mujahied on 2011-09-19
> **haqking said:**
> The server would need to be in a DMZ or have port forwarding on the home router to forward port 80 requests to the local LAN ip of the server also.

If it is in a DMZ then it needs to have its own firewall with security tied down, if using port forwarding the the router usually protects the server.

For a home server as you suggested that is ;-)

Peace


Thanks haqking forgot about that option

---

### Post by mujahied on 2011-09-19
Guys please note you are not obliged to use co.cc 

you can use
alot of other free domains

```
http://www.dot.tk/en/index.html?lang=en
```

```
http://www.freedomain.co.nr/
```


there should be much more out there on the net but these are just a few out of all

please note most of these domains are for a year free

---

