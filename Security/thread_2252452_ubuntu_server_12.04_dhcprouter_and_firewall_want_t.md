---
title: "ubuntu server 12.04 dhcp/router and firewall want to encrypting all internet traffic"
date: 2014-11-12
forum: Security
---

### Post by crashdogy on 2014-11-12
OK I have a Ubuntu server 12.04 dhcp router/firewall with 2 nic's one for network one for internet, and want to encrypted all internet traffic going in and out of my server ? 

I also have a VPS setup with Openvpn on it I use for laptops smartphone when in public places.

I am sure there's a easy why to do this LOL

---

### Post by crashdogy on 2014-11-13
Ok let me ask this a different way, I have 2 nic crads 1 nic is router,  second nic is wan and ever thing works.  I just want to encrypted everything going out and in on nic card 2 wan. Looking for a easy setup.

---

### Post by HermanAB on 2014-11-13
Easy? Use SSH.

---

### Post by crashdogy on 2014-11-13
> **HermanAB said:**
> Easy? Use SSH.

Thank you for the reply !

OK can you be a little more specific how would I use ssh ?   Is there a tutorial on this ?

---

### Post by fugu2 on 2014-11-15
where will the encrypted data be going to, from the wan interface card? Encryption requires a source and a destination.

---

### Post by crashdogy on 2014-11-15
> **fugu2 said:**
> where will the encrypted data be going to, from the wan interface card? Encryption requires a source and a destination.

Thanks for reply !

Well was hopping to do a tunnel, I guess from Wan to my VPS and just let it run in definitely, so if I login to my VPS with openvpn client from my phone or any one at home does work and there are any sniffers out there its all encrypted.

---

### Post by fugu2 on 2014-11-15
could you install a openvpn client on the 12.04 install? then it might take some iptables magic to forward the packets properly to your vps

---

### Post by crashdogy on 2014-11-15
> **fugu2 said:**
> could you install a openvpn client on the 12.04 install? then it might take some iptables magic to forward the packets properly to your vps

That's what I was thinking but will that forward all the Lan network traffic  to VPS ?

---

### Post by fugu2 on 2014-11-17
> **crashdogy said:**
> That's what I was thinking but will that forward all the Lan network traffic  to VPS ?I think it depends on how you setup your iptables. Some traffic is not affected by iptables at all (ARP packets for instance, but you don't want to forward those anyway), some traffic you might not want to forward to your VPS (if your ISP uses DHCP for getting a WAN ip addr, you don't want to send that data to your VPS), and some data you do want to send to the VPS. I'm not 100% on this but I think openvpn sets up a special interface for the tunnel, and you forward the datas you want to from the LAN interface of your router to the openvpn interface. You should probably setup a temporary tap at the WAN to make sure things are configured properly.

---

