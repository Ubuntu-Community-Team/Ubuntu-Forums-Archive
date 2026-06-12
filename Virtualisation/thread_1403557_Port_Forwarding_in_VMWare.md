---
title: "Port Forwarding in VMWare"
date: 2010-02-10
forum: Virtualisation
---

### Post by howcanireachthesekids on 2010-02-10
I have XP SP3 installed in VMWare. I am running Karmic Koala x86.

My question is simple. how do i get ports forwarded so they can be functional in XP ?
I can do port forwarding in Ubuntu, its quite easy. Here is some more info.

my static IP on my main OS ( ubuntu ) i set to 192.168.1.99

my  default gateway 192.168.1.1
subnet mask 255.255.255.0
my dns is  the google dns
8.8.8.8
8.8.4.4

so do i use NAT or Briged  connection on the XP in VMWare ? do i assign a static ip in XP ? if so,  is that possible and how ?

then what do i do ? how do i then proceed in the router page ?

thanks in advance :)

---

### Post by TJet1.8 on 2010-02-10
Well...the question would be "Why are you NAT'ing?"

If you don't need to NAT, then use Bridge.
There is no need to NAT unless you have a specific reason to.

As for your other questions...is your system used for home or work?

---

### Post by howcanireachthesekids on 2010-02-11
> **TJet1.8 said:**
> Well...the question would be "Why are you NAT'ing?"

If you don't need to NAT, then use Bridge.
There is no need to NAT unless you have a specific reason to.

As for your other questions...is your system used for home or work?
Doesn't mater if i NAT or brigde, i just want to port forward in the XP.

my system is all for home use. any help please ?

---

### Post by TJet1.8 on 2010-02-11
You don't need to port forward if you use a bridged connection.
Your XP vm will be wide open to your home LAN on a bridged connection.
Just setup your XP Operating System to use DHCP to get an IP address automatically from your home router.

Your routers DHCP service will provide your XP Operating System an IP address, Gateway, Subnet Mask, and DNS setting automatically.

Forgive me if I am wrong, but i get the feeling you don't understand the difference between a Bridged network connection and a NAT'ed network connection.

Do you understand the difference?

---

### Post by howcanireachthesekids on 2010-02-11
> **TJet1.8 said:**
> You don't need to port forward if you use a bridged connection.
Your XP vm will be wide open to your home LAN on a bridged connection.
Just setup your XP Operating System to use DHCP to get an IP address automatically from your home router.

Your routers DHCP service will provide your XP Operating System an IP address, Gateway, Subnet Mask, and DNS setting automatically.

Forgive me if I am wrong, but i get the feeling you don't understand the difference between a Bridged network connection and a NAT'ed network connection.

Do you understand the difference?

This forum is full of serious adult people willing to help :)
 thanks a lot !!! and i mean it. i could successfully go what i wanted to. and i think i know the basic difference between NAT and bridged.  i should study a little on that though :P its never bad to know something more...

problem solved, will add SOLVED tag

---

