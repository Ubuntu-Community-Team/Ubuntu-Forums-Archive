---
title: "Server networking configuration"
date: 2009-03-16
forum: Server Platforms
---

### Post by Jimmy9pints on 2009-03-16
Hi, I am trying to setup Ubuntu server for home use. I was trying to follow [this guide]("http://www.howtoforge.com/ubuntu-home-fileserver"), but somehow or other, I have completely goofed up the networking. 

Please have a look at that [guide]("http://www.howtoforge.com/ubuntu-home-fileserver") to see what he suggests. In any case, for me it didn't work. He suggests doing it all over Putty but when you change the IP (to static) it cuts off the connection - and I cannot then reconnect using the new IP. 

I then tried to follow the community documentation on [network config for servers.]("https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html") Still no luck. 

Now, if I sudo anything I get
```
sudo: unable to resolve host
```
and if I 
```
sudo /etc/init.d/networking restart
```
I get
```
* Reconfiguring network interfaces
SIOCADDRT: No such process
Failed to bring up eth0
```

Any help appreciated!

---

### Post by Jimmy9pints on 2009-03-16
To give you the info that you probably need I have brought across most of the files I have been messing around with (and messing up!). Including:
interfaces
hostname
hosts
resolv.conf
(all renamed to .txt so the forums will accept them)

They are attached. 

Cheers,

James.

---

### Post by volkswagner on 2009-03-16
```
 address 192.168.0.11
 netmask 255.255.255.0
 gateway 192.168.1.1
```

Should be

 ```
address 192.168.1.11
 netmask 255.255.255.0
 gateway 192.168.1.1
```

Is your windows machine on the same network?  If so, run ipconfig in a terminal on the windows machine to verify the ip address range for the third place being a Zero or One.  Both the gateway and ip address should have the same numbers in first, second, and third place.

---

### Post by Jimmy9pints on 2009-03-16
Cheers for your reply. 

I checked my interfaces file, actually it is indented like that. Maybe that got lost when I brought it over or changed it into txt. I still get:
```
 * Reconfiguring network interfaces.....
SIOCARDDRT: No such process
Failed to bring up eth0
```

Then I tried to ping google, and then my router, I got:
```
 ping: unknown host google.com
```
and
```
 connect: Network is unreachable
```

BTW, I did check my router's ip, it is indeed 192.168.1.1

Cheers,

James.

---

### Post by Jimmy9pints on 2009-03-16
ha ha, just noticed your sig:
> Nothing is ever easy, but if it is difficult you must be doing it wrong. 

In that case, I am definitely doing it all wrong.

---

### Post by BkkBonanza on 2009-03-16
The indentation doesn't matter but the address and the gateway need to be in the same subnet. The example above show address being ..0.11 not ..1.11 - don't know if that's a typo or actually your problem.

---

### Post by volkswagner on 2009-03-16
Just to confirm, I posted about inconsistent ip address not indent format.

Look at the address line.  Also the ip addresses in interfaces and hosts don't agree, although that won't stop networking from loading.

Did you edit the address line in /etc/network/interfaces file to reflect 

address 192.168.**1**.11   

?

Sorry but you last post did not indicate if you did the above edit.

---

### Post by Jimmy9pints on 2009-03-16
Yeah, sorry! I totally missed that! :oops:
 
This time, upon restarting it seems much more promising. But it seems to be waiting for something to complete after "Starting NTP server ntpd". 
........
I waited for 10 mins or so and it was still hanging - so I hit ctrl+C and I am back at the prompt. 

I can now log in using puTTY. Great, thank you.  However I still get > sudo: unable to resolve host

By the way, I wonder if you can tell me in the guide and the community documentation I pointed out in my original post, I don't really get the purpose of messing around with /etc/hosts and /etc/resolv.conf 

Could you explain in noob terms what that's all for? What would a real use of "mydomain.example" be? 

And also, when setting the nameservers in resolv.conf, do I just put the IP of my router (because that routes through to OpenDNS) or do I put OpenDNS's nameservers there?

Thanks for your help!

James.

---

### Post by volkswagner on 2009-03-16
> **Jimmy9pints said:**
> ......
By the way, I wonder if you can tell me in the guide and the community documentation I pointed out in my original post, I don't really get the purpose of messing around with /etc/hosts and /etc/resolv.conf 

/etc/hosts is handy for entering all local machines ip's and hostnames.  This allows one to ssh, or use other services with the hostname rather than the ip address.

> Could you explain in noob terms what that's all for? What would a real use of "mydomain.example" be? 

And also, when setting the nameservers in resolv.conf, do I just put the IP of my router (because that routes through to OpenDNS) or do I put OpenDNS's nameservers there?

Thanks for your help!

James.

Using actual name server ip's or your router, both work for various people.  

mydomain.example is if you want to setup a domain name.  Hopefully someone can give more detail on this one, but this is where you would put your FQDN, or you may make up a local one, I believe.

---

### Post by BradleyAtkins on 2009-03-16
I recently posted a question along these lines and was pointed in the direction of editing these files.

I wanted to get an ubuntu laptop and an ubuntu server configured with fixed IP's on my home network, (also my windows machines). 

Thankfully I found a simple answer that avoided the pain: -

My wireless router was acting as a dhcp server and had the facility to allow me to reserve IP addresses for each machine. So now my machines still dynamically go to the router on boot up to get their IP address but are always given the same IP. Kind of a "dynamic fixed IP" if you get my drift.

Now I can ssh and scp into my ubuntu machines. :P

Hope this helps

Brad

PS I should add I wanted to go this way as one of the machines is an ubuntu laptop and I still wanted it to be able to dynamically grab an IP if I visited friends and wanted to log into their router.

---

### Post by volkswagner on 2009-03-16
> **BradleyAtkins said:**
> .......
My wireless router was acting as a dhcp server and had the facility to allow me to reserve IP addresses for each machine. So now my machines still dynamically go to the router on boot up to get their IP address but are always given the same IP. Kind of a "dynamic fixed IP" if you get my drift...



Would you mind mentioning the router make/model?  I wish my Linksys WRT54G had the capability.

---

### Post by Jimmy9pints on 2009-03-16
> **BradleyAtkins said:**
> 
PS I should add I wanted to go this way as one of the machines is an ubuntu laptop and I still wanted it to be able to dynamically grab an IP if I visited friends and wanted to log into their router.

Smart!

Is there a way round that for the rest of us? ha ha. I can just imagine going round to my Windows-using friends:
"Yeah Linux is much better....yada yada yada... let me just hack this interfaces file and I'll be connected in no time"
:D

---

### Post by BradleyAtkins on 2009-03-17
Hi

Yes it is a Netgear DG834G v3, I have had it about a year and it seems very reliable.

Good luck

Brad

---

### Post by BradleyAtkins on 2009-03-17
:) Yes didn't strike me as too friendly either, although you could doubtless script it to change your settings back and forth if you know how to do it. (I don't as I am new to Ubuntu)!

---

### Post by BradleyAtkins on 2009-03-17
Looks like you may be able to flash this firmware to your router and then use it to get static ip's: -

[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)

They certainly mention your router type in the FAQ's although maybe not the exact model.

Saw a link to it on this forum: -

[http://www.wirelessforums.org/alt-internet-wireless/linksys-wrt54gl-assign-static-ip-mac-address-5537.html](http://www.wirelessforums.org/alt-internet-wireless/linksys-wrt54gl-assign-static-ip-mac-address-5537.html)

Don't blame me though if you kill your router!! :) 

Good luck

---

