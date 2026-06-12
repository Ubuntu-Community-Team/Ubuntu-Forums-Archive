---
title: "Upside-down-ternet"
date: 2007-01-18
forum: Server Platforms
---

### Post by @trophy on 2007-01-18
Ok, so I've got a little bit of linux experience under my belt now, and I thought I'd try a little experiment that I saw on the intarwebs a little while ago... [Upside-town-ternet!](http://ex-parrot.com/~pete/upside-down-ternet.html)

What I'd like to do is have a list of MAC addresses that will see normal internet on my wireless network, and everyone else gets the funk-tified version.

The problem is, since I have an actual wireless router, instead of a computer acting like one, I'm not sure how the network topology needs to be to pull this off.  I've drawn a diagram of how my network is now and how I think I'm going to have to do it.  If there's a simpler way than putting 2 NIC's in the desktop (could I get all traffic going through the router to go first to the desktop and then out to the internet?) then please let me know.

[IMG]http://img.photobucket.com/albums/v353/afrotechmods/upside-down-ternet.jpg[/IMG]

---

### Post by jtc on 2007-01-18
I think you want to use the proposed solution you have. Without knowing what kind of wireless router you have I guess it is one of those standard-home-editions? You really don't want to have them trying to do any fancy tricks. It is better to leave it all to your PC. Besides, NIC's are cheap and easy installable.

As a long term solution I defiantly don't think you should rely on MAC-addresses. It isn't really that hard to sniff and spoof them. Still, I don't think that should stop you in the short run from playing some tricks with your neighbour :-D

---

### Post by @trophy on 2007-01-18
> **jtc said:**
> I think you want to use the proposed solution you have. Without knowing what kind of wireless router you have I guess it is one of those standard-home-editions? You really don't want to have them trying to do any fancy tricks. It is better to leave it all to your PC. Besides, NIC's are cheap and easy installable.

As a long term solution I defiantly don't think you should rely on MAC-addresses. It isn't really that hard to sniff and spoof them. Still, I don't think that should stop you in the short run from playing some tricks with your neighbour :-D


Ok, so a couple of questions: 

1:  I'm not real worried about MAC spoofing here... just wanting to have a bit of fun with the neighbors, but if I were worried, what would I do instead?  I was under the impression that with wireless you're not going to get any more secure than WPA + MAC address filtering + try to make sure you limit where your signal goes.  

2: Can you walk me through how to take care of NAT and IPs and all that with this setup?  Basically I'm hoping it's as easy as this:  The desktop checks all the packets coming into NIC 1 and if they're HTML, alters them before passing them on to NIC2, but basically it just passes the packets from NIC1 to NIC2 and vice versa.  So am I right in assuming that it won't need to provide any NAT functionality for the network?

---

### Post by jtc on 2007-01-18
> **@trophy said:**
> Ok, so a couple of questions: 
1:  ... but if I were worried, what would I do instead?  I was under the impression that with wireless you're not going to get any more secure than WPA + MAC address filtering + try to make sure you limit where your signal goes.
Well, a VPN-solution would be even more secure. Still, when it come to home-use a WPA-PSK solution is more then enough.
  
> **@trophy said:**
> 
2: Can you walk me through how to take care of NAT and IPs and all that with this setup? 
Actually, I haven't gotten that much experience of manually routing, so I'm not sure if I offhand can write a good walkthrough. Hopefully someone else in the forum can help you.

---

### Post by @trophy on 2007-01-19
> **jtc said:**
> Well, a VPN-solution would be even more secure. Still, when it come to home-use a WPA-PSK solution is more then enough...
  

... Actually, I haven't gotten that much experience of manually routing, so I'm not sure if I offhand can write a good walkthrough. Hopefully someone else in the forum can help you.

Ok, well thanks for your help... hopefully that someone else will reply to my post... replies seem to be fairly hard to come by around here...

Anyways I'd love to have some friends over, and let them use the internet for a while, then remove their mac address from the whitelist... hilarity ensues...

---

