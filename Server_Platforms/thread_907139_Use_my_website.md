---
title: "Use my website"
date: 2008-09-01
forum: Server Platforms
---

### Post by talsemgeest on 2008-09-01
Hi everyone, I have recently installed ubuntu server 8.04 on an old computer I got my hands on. I had the idea that I would use it to host a simple (almost) website. So I had LAMP (and all other options except mail server) installed when I installed ubuntu server, and then installed xubuntu-desktop for any gui needs. So all of that is installed.

So I put my php site into /var/www and went to localhost with firefox, and that worked. I typed the internal ip of the server from another computer on the network, and that worked. But since I am really new to this I have no idea how to access the website from any other computer on the internet.

What do I do?

---

### Post by cdtech on 2008-09-01
If you type (at the server command line):
```
ifconfig
```
You will see the ISP's provided IP address used for your connection.
```
eth0      Link encap:Ethernet  HWaddr 00:14:bf:59:e6:98  
          inet addr:**xx.xx.xx.xxx**  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345872509 errors:3 dropped:0 overruns:0 frame:4
          TX packets:25665342 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:966586655 (921.8 MB)  TX bytes:3424306845 (3.1 GB)
          Interrupt:16 Base address:0xc000
```
Just type that address into your browser.

**Update::.**
This is if you are using your server as a gateway/router. You should have a NIC contected to your ISP provided modem and a NIC for your intrenet.

---

### Post by tuskenraider on 2008-09-01
> **talsemgeest said:**
> Hi everyone, I have recently installed ubuntu server 8.04 on an old computer I got my hands on. I had the idea that I would use it to host a simple (almost) website. So I had LAMP (and all other options except mail server) installed when I installed ubuntu server, and then installed xubuntu-desktop for any gui needs. So all of that is installed.

So I put my php site into /var/www and went to localhost with firefox, and that worked. I typed the internal ip of the server from another computer on the network, and that worked. But since I am really new to this I have no idea how to access the website from any other computer on the internet.
What do I do?

i host my own website off my server at home... not an ubuntu server... =( but it is free and open source.. HFS is the handy dandy file server i use... its super great... 600k program.. great forum support and super nice people...  oh and it works!!! LOL [www.rejetto.com/hfs](www.rejetto.com/hfs)  anyway down to the nitty gritty...  

1. dyndns - do you have a [www.yoursite.com?](www.yoursite.com?) for example i have www. aguyin cookeville. com  when you type that in.. you connect to dyndns's servers...and they redirect you to the ip address that they have on file for my server. (which is a dynamic ip address so it changes.. fortunatly my router connects to dyndns and updates them on my ip addy changes!!) i highly suggest using a service like dyndns.. because idk about you.. but 97.84.165.58 (not my ip lol) is so much harder to remember than [www.blahblahblah.com](www.blahblahblah.com) :lolflag:

2. forward that port - what kind of router do you use?? thats more of a retorical question! lol the reason i ask... same for utorrent or an xbox or anything else that might need a PORT FORWARDED...  my website is running off of port 80.. (fortunatly charter doesnt block that port)  so anyway...  in your router you'll need to go in and forward what ever port you want to run your website off of.. i obviously dont know what kind of router you use... but with the help of the portforward.com youll be able to get it.. 

3. firewall - check... double check... and triple check to make sure that your firewall is permitting the port on your server to be open.. yes i know you said it was an ubuntu server... but i had ALL KINDS O TROUBLE out of the blasted firewalls... so i felt i needed to warn you! lol 

well that pretty much takes care of everything as far as a stranger getting to your server... your dyndns for your [www.blahblahblah.com](www.blahblahblah.com), forwarding a port and check your firewall...  good luck... and welcome to the fantastic world of your own server... 

p.s dont bother with the mail server... i had a windoze 2003 r2 mail server for a while.. i kept getting Do-uche-bags from tiawan trying to hack it... so needless to say... screw that idea. lol  

oh.. one more nifty thing to consider for your server... mythbuntu... gotta love dvr!!!! thats actually the main reason i have mine!!

---

### Post by talsemgeest on 2008-09-01
> **cdtech said:**
> If you type (at the server command line):
```
ifconfig
```You will see the ISP's provided IP address used for your connection.
```
eth0      Link encap:Ethernet  HWaddr 00:14:bf:59:e6:98  
          inet addr:**xx.xx.xx.xxx**  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345872509 errors:3 dropped:0 overruns:0 frame:4
          TX packets:25665342 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:966586655 (921.8 MB)  TX bytes:3424306845 (3.1 GB)
          Interrupt:16 Base address:0xc000
```Just type that address into your browser.

**Update::.**
This is if you are using your server as a gateway/router. You should have a NIC contected to your ISP provided modem and a NIC for your intrenet.

Thanks for your help! :) It tried simply typing in my external ip, but I didnt expect that to work because I have a 4 port adsl router. I will have a look through it tonight.


> **tuskenraider said:**
> i host my own website off my server at home... not an ubuntu server... =( but it is free and open source.. HFS is the handy dandy file server i use... its super great... 600k program.. great forum support and super nice people...  oh and it works!!! LOL [www.rejetto.com/hfs]("http://www.rejetto.com/hfs")  anyway down to the nitty gritty...  

1. dyndns - do you have a [www.yoursite.com?]("http://www.yoursite.com?") for example i have www. aguyin cookeville. com  when you type that in.. you connect to dyndns's servers...and they redirect you to the ip address that they have on file for my server. (which is a dynamic ip address so it changes.. fortunatly my router connects to dyndns and updates them on my ip addy changes!!) i highly suggest using a service like dyndns.. because idk about you.. but 97.84.165.58 (not my ip lol) is so much harder to remember than [www.blahblahblah.com]("http://www.blahblahblah.com") :lolflag:

2. forward that port - what kind of router do you use?? thats more of a retorical question! lol the reason i ask... same for utorrent or an xbox or anything else that might need a PORT FORWARDED...  my website is running off of port 80.. (fortunatly charter doesnt block that port)  so anyway...  in your router you'll need to go in and forward what ever port you want to run your website off of.. i obviously dont know what kind of router you use... but with the help of the portforward.com youll be able to get it.. 

3. firewall - check... double check... and triple check to make sure that your firewall is permitting the port on your server to be open.. yes i know you said it was an ubuntu server... but i had ALL KINDS O TROUBLE out of the blasted firewalls... so i felt i needed to warn you! lol 

well that pretty much takes care of everything as far as a stranger getting to your server... your dyndns for your [www.blahblahblah.com]("http://www.blahblahblah.com"), forwarding a port and check your firewall...  good luck... and welcome to the fantastic world of your own server... 

p.s dont bother with the mail server... i had a windoze 2003 r2 mail server for a while.. i kept getting Do-uche-bags from tiawan trying to hack it... so needless to say... screw that idea. lol  

oh.. one more nifty thing to consider for your server... mythbuntu... gotta love dvr!!!! thats actually the main reason i have mine!!

Thanks for the help! :) I will look into port forwarding tonight. When I do, what sort of stuff should I be looking for? Like where should the port be forwarded to?

---

### Post by Iowan on 2008-09-01
If your server has a "local" address (192.168.X.X or 10.X.X.X) the router should forward requests to "it's" port 80 to the server's "local" address.

---

### Post by tuskenraider on 2008-09-01
> **talsemgeest said:**
> 
Thanks for the help! :) I will look into port forwarding tonight. When I do, what sort of stuff should I be looking for? Like where should the port be forwarded to?

the portforward website is pretty detailed in its help.. if you can set up an ubuntu server.. you will be able to figure it out....  depending on your router you should just have to select/type in the port number and the ip address you want to forward to... ex 192.168.1.100 or what ever your server is... and click apply and bada-bing.. your on..

tusken

---

### Post by Wiebelhaus on 2008-09-01
....my bad

---

### Post by talsemgeest on 2008-09-03
Awesome, everything is working nicely now. Thanks for your help!

---

### Post by cariboo on 2008-09-03
never mind

---

### Post by tuskenraider on 2008-09-03
> **talsemgeest said:**
> Awesome, everything is working nicely now. Thanks for your help!

your welcome... glad i could help!! :guitar:

tusken

---

