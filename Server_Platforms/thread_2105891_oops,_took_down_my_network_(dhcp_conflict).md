---
title: "oops, took down my network (dhcp conflict?)"
date: 2013-01-17
forum: Server Platforms
---

### Post by jamdis on 2013-01-17
Well I feel silly. I tried to set up Ubuntu Server 12.04 to run some simple web-based intranet stuff on the widnows network here at work. All I did was install Ubuntu, gave the machine a static IP, and plug it in. It seemd to be working reasonably well when I left last night.
 
When I came in this morning, the network had stopped working correctly. My coworkers couldn't reach our exchange server and people couldn't log in with active directory. I unplugged the ubuntu box, and rebooted our domain controller. Everything went back to normal.
 
My guess is that the ubuntu box was trying to act as a dhcp server and causing conflicts with the actual dhcp server. I thought, however, that ubuntu server wouldn't act as a dhcp server out of the box unless specifically configured to do so? Same with DNS right?
 
What did I do?

---

### Post by chadk5utc on 2013-01-17
> **jamdis said:**
> Well I feel silly. I tried to set up Ubuntu Server 12.04 to run some simple web-based intranet stuff on the widnows network here at work. All I did was install Ubuntu, gave the machine a static IP, and plug it in. It seemd to be working reasonably well when I left last night.
 
When I came in this morning, the network had stopped working correctly. My coworkers couldn't reach our exchange server and people couldn't log in with active directory. I unplugged the ubuntu box, and rebooted our domain controller. Everything went back to normal.
 
My guess is that the ubuntu box was trying to act as a dhcp server and causing conflicts with the actual dhcp server. I thought, however, that ubuntu server wouldn't act as a dhcp server out of the box unless specifically configured to do so? Same with DNS right?
 
What did I do?

I think this really depends exactly what you chose to install? If these services have been installed then it is possible they could be the cause of the issue. They will usually run but require some configuration to suit your network. To see what services are running try(offline of course)
> sudo initctl list 
OR I think this works too
> service --status-all

---

### Post by jamdis on 2013-01-17
> **chadk5utc said:**
> I think this really depends exactly what you chose to install? 
That's why I'm confused.  I didn't install anything except the LAMP and SAMBA packages offered by the live CD.  I didn't get around to installng the software I wanted to use this box for, so this is basically a pristine 12.04 install.  Does server 12.04 come with a DHCP server? If so, can I disable it completely?

---

### Post by chadk5utc on 2013-01-17
> **jamdis said:**
> That's why I'm confused.  I didn't install anything except the LAMP and SAMBA packages offered by the live CD.  I didn't get around to installng the software I wanted to use this box for, so this is basically a pristine 12.04 install.  Does server 12.04 come with a DHCP server? If so, can I disable it completely?

OK makes sense, and would/should cause no issue, the only other thing I can think of off the top of my head that would cause any type of conflict would be with or having set a duplicate IP

---

### Post by darkod on 2013-01-17
There should be no DHCP or DNS server by default. Did you make sure the IP you set on the ubuntu server doesn't clash with another windows server on the network? Or even worse, the router?

---

### Post by Warren Hill on 2013-01-17
There is a second concern here.  I had a similar problem in a network with a printer I had with a fixed IP address.

You need to be sure the IP address you assign can't conflict with anything else on the network but I still in the correct sub net.  

To solve this I have a DHCP server in my router at 192.168.0.1

It assigns DHCP in the range 192.168.0.2 to 192.168.0.249

Leaving 192.168.0.250 to 192.168.0.254 free for devices I want to have a static IP.
Printers and Network storage on my network

---

### Post by jamdis on 2013-01-17
> **darkod said:**
> There should be no DHCP or DNS server by default. Did you make sure the IP you set on the ubuntu server doesn't clash with another windows server on the network? Or even worse, the router?

Yeah, before I give something a static, I always check my records and ping the address to make sure it isn't taken, so I'm pretty sure that's not it.

---

### Post by CharlesA on 2013-01-17
DHCP reservation ftw!

Give it a shot and see if it does the same thing.

---

### Post by jamdis on 2013-01-17
> **Warren Hill said:**
> 

You need to be sure the IP address you assign can't conflict with anything else on the network but I still in the correct sub net.  


Okay, this makes some sense, but if I screwed this up (assigning the ubuntu box a static IP that is supposed to be saved for dhcp) how would that affect windows services on the domain controller? Surely it would only affect that particular machine, right?

---

### Post by Warren Hill on 2013-01-17
> **jamdis said:**
> Okay, this makes some sense, but if I screwed this up (assigning the ubuntu box a static IP that is supposed to be saved for dhcp) how would that affect windows services on the domain controller? Surely it would only affect that particular machine, right?

Not sure.  It depends which devices have the same IP every time you try and talk to one of them both will reply and this can cause a lot of data clashes on the network.

In theory it shouldn't because a lot of devices don't fully implement the standards.  Everything works provided everything behaves but one bad device can mess up an entire network.

---

### Post by jamdis on 2013-01-17
> **CharlesA said:**
> DHCP reservation ftw!

Give it a shot and see if it does the same thing.

Okay, I checked and I can confirm that the address I gave it was not taken by another device, and was not part of the ordinary dhcp address pool.  I'm tempted to try a DHCP reservation as you suggest, but I'm afraid of taking down the network again.  Are there any other possible culprits?

---

### Post by darkod on 2013-01-17
One thing is for sure, it doesn't mess up networks by default. As it happens, yesterday I installed 12.04.1 LTS 64bit server in VBox on my workplace to try few things. The network settings are set to Bridged, so it's the same as if I connected a physical machine directly to the LAN.

It didn't bring down the network, of course.

This has something to do with how you configured it, where you connected it, etc.

I'm also not sure whether IP conflict will affect only the two devices or not, but in any case I never use static IP addresses which are inside dhcp range. You have plenty of IPs available in the private range for any network size. Have your static IP pool outside of the dhcp pool.

---

### Post by jamdis on 2013-01-17
Okay, thanks for all your help guys.  My plan is to wait until everyone has gone home on Friday afternoon and try it with ordinary DHCP first, and then add a reservation if it seems like everything works.  I'll let you know if I figure anything out.

---

### Post by Warren Hill on 2013-01-17
It may be worth installing Wireshark on a machine (either Windows or Linux) if you have problems then you can see what's  actually happening over the network.

It's in the software centre for Ubuntu of you can get it from here if you want to use a windows PC.
[http://www.wireshark.org/download.html](http://www.wireshark.org/download.html)

---

### Post by CharlesA on 2013-01-17
> **Warren Hill said:**
> It may be worth installing Wireshark on a machine (either Windows or Linux) if you have problems then you can see what's  actually happening over the network.

It's in the software centre for Ubuntu of you can get it from here if you want to use a windows PC.
[http://www.wireshark.org/download.html](http://www.wireshark.org/download.html)

+1. Raw packets are sometimes hard to decipher, but it would help find out what is actually happening.

@OP: I have a Debian box on the network at work and it hasn't conflicted with anything - I have it set to use an IP outside of DHCP. The same should apply to Ubuntu.

---

### Post by jamdis on 2013-01-25
Not sure what actually went wrong here, but switching the server back to DHCP and creating a reservation seemed to take care of it.  Thanks for the help

---

