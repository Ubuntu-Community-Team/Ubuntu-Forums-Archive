---
title: "Binding to IP's not assigned to Ethernet Card?"
date: 2011-05-26
forum: Server Platforms
---

### Post by ravingmad on 2011-05-26
Hi all

I'm hoping somebody could help me with this rather puzzling situation.

I have a server hosted with Hetzner in Germany and have had it there for over a year now without any glitches. Last week very abruptly they deactivated the server giving me a very vague reason of "I was using another IP that was not assigned to me". After several calls I had the server reactivated but am still puzzled by this and Hetzner Germany has been unable to provide me with any proof, logs, traces or anything for that matter to validate their claims.

My primary (physical) server has one IP allocated (static) and IPv6 is turned off. On top of this server I run 3 VMware servers, 1 Ubuntu, 1 Debian, 1 Windows and all 3 of these VM's have static IP's configured.

I've done traceroutes, netstats and looked through every single config file with a fine toothcomb without finding anything and the problem has not reoccured either.

What I would like to know is if there is some way that someone could craft an attack of some sort that could cause a server to do this, to latch onto another IP not assigned to its NIC? 

I am totally stumped on this and it would help if Hetzner could provide something concrete to subtantiate their claim or to help with diagnosing what happened but they have been unable or unwilling to assist in that regard.

Anyone with any insight or suggestions???

Thanks

---

### Post by sanguinoso on 2011-05-26
I have personally never heard of such a thing. Its possible that they made an error as they cannot provide you with a reason why they thought that.

---

### Post by ravingmad on 2011-05-26
> **sanguinoso said:**
> I have personally never heard of such a thing. Its possible that they made an error as they cannot provide you with a reason why they thought that.

Thanks for the quick reply. I've been in networking and hosting servers myself for 20 years and have never heard of this either and I also think they made an error and are not willing to admit it. The whole thing leaves me feeling very uneasy that at any time they can make such an error again. Would hate to relocate servers again but I am considering this after their actions.

Cheers ;)

---

### Post by sanguinoso on 2011-05-26
The only thing I could possibly think of was if they were monitoring that with DNS and there was a cache poisoning attack. That would be foolish on their part but so would mistakenly disabling a server.

---

### Post by hawkmage on 2011-05-26
With the proper permissions an application can build a spoofed packet with whatever address they want and send it out.  

On the VMWare configuration what VM Networks are configured and how are your VMs attached to the virtual networks?

---

### Post by koenn on 2011-05-27
I second that.

1- sending out packets with a spoofed sender IP address is not that hard. The capability is built-in in Linux. 

One sort of "Attack" that builds on that is a reflected denial of service : you send requests to a large number of servers on the internet, with a spoofed sender address. They all reply to that address. The server that actually has that address has to deal with all the replies. 


2- depending on how you set up your VM networking, your virtual machines might be directly visible on the internet, and your hosting provider could be seeing traffic from/to your (physical) server with IP adresses of the virtual machines, i.e. not the IP address of the server itself.

---

### Post by BkkBonanza on 2011-05-28
It's very easy to create a virtual interface in Linux with some other IP address associated to it. So if they assigned you 192.168.1.2 for your physical interface, you or someone with control of your system, could easily create a virtual interface and assign a static IP, eg. 192.168.1.25 or whatever. This is simple. 

However, whether that would be enough to create the situation they claim happened I don't know. Your machine could communicate on their LAN with that IP and may create conflicts with other systems. I could see that happening. It's doubtful that would happen by accident but it could by malicious intent or incorrect configuration perhaps. VMs in some network modes can create virtual interfaces internally that would assign arbitrary IP values that could cause conflicts.

To learn more about this google "virtual interface linux" where it shows you how to create one and what these are.

---

