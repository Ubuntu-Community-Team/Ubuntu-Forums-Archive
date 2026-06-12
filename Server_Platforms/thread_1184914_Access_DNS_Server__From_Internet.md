---
title: "Access DNS Server  From Internet"
date: 2009-06-11
forum: Server Platforms
---

### Post by ubila on 2009-06-11
Hi Everyone :D

Just got a few questions. Im trying to set up my own hosting, Ive got ubuntu 8.10 all sett up using the "Perfect Server Guide" - So all apache etc is set up correctly and im running bind9 DNS.

I purchased a hostname, and now am realy confused as to how to point it to my server.

My network setup is like this:

 Router
Internal IP : 192.168.2.1
External IP : xxx.xxx.xxx.xxx

Server1
Internal IP : 192.168.2.66
Contains Apache + webfiles + DNS bind9

I have configured Apache with VirtualHost on port 80 to point [www.example.com]("http://www.example.com") to Server1 -> /home/dev/client1/

And i have set up NAT Forwarding on my Router to :
prot : TCP 
public port : 4266 
private port : 80 
ip address : 192.168.2.66 (Server1)

And i tried setting my URL DNS at my Registra to xxx.xxx.xxx.xxx:4266 
But it doesnt seem to work.
My Registra is telling me i need to point it to example: ds1.example.com

I can successfully access my Sever1 from the internet by visiting:
xxx.xxx.xxx.xxx:4266

I Spose my questions are:

1. Have i done any of this wrong?
2. Is it just my Registra thats dissallowing me to point to this IP?
3. Should i transferr my domain name to a Registra that will allow me?

Im really confused at this point, read up alot about bind9 and DNS servers, all seems to be alot about internal access and not external.
Not even sure if im heaidng in the right direction. Any help would be realy appreciated.

Thanks for your time

---

### Post by drave99 on 2009-06-12
first off. its much easier to use your registra's dns if you just want to host a single web site. they usually have a control panel that allows you to edit the dns entries for your domain.

but ...

do you have a fixed IP address on the 'External IP : xxx.xxx.xxx.xxx' it MUST be fixed if you want to use it for dns

lets say you call your dns server ds1. somewhere on your registra's control panel (or whatever you use to edit the basic info on your domain) there is a place to specify the name servers for your domain and you would put ds1.yourdomain in there. possibly including the xxx.xxx.etc FIXED ip. this what gets published if you do a 'whois yourdomain'

on your router you must include a rule to route port 53 to your bind server.

---

