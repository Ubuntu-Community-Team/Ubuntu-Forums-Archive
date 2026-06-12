---
title: "No IP adress for Bridge Connection in Vmware Server"
date: 2008-09-29
forum: Virtualisation
---

### Post by SILLAT on 2008-09-29
hey ya'll i'm running Vmware Server 1.0.6 with win 2000 & win xp as Guests on ubuntu 8.04 host. 
i have them both set up as bridge connection in my Virtual Machine an not as NAT (sharing connection).
the problem i'm having is the win 2000 works well with the bridge connection but the win xp connection says "limited or no connection" meaning its not connected, i checked the Ip address an it says 169.x.x.x meaning its an apipa automated system generated ip address from windows.
How can i get a ip address for my xp bridge connection for my win xp guest? or get my connection to work as bridge connection with win xp. 
for the record it works great with NAT connection  i jus prefer the bridge connection.
thnx much !!

---

### Post by bodhi.zazen on 2008-09-29
It would help if you listed your hard ware.

For example, are you using a wireless network card ?

Both NAT and bridged network connections work out of the box on VMWare.

And you post almost begs the question, if it is not broken, why fix it ? 

If NAT works there is really no need to bridge. Is there some reason you need a bridged connection ?

---

### Post by SILLAT on 2008-09-29
Hey thnx for your reply
i'm not using a wireless card i'm actually using a 100 mps ethernet onboard Nic
I wanted to keep my virtual Windows box as isolated as possible for security reasons Windows boxes get compromised so easily.
is there a way i can  beef up security on the nat connection? or cud it be my on board ethernet nic?

---

### Post by bodhi.zazen on 2008-09-29
> **SILLAT said:**
> Hey thnx for your reply
i'm not using a wireless card i'm actually using a 100 mps ethernet onboard Nic
I wanted to keep my virtual Windows box as isolated as possible for security reasons Windows boxes get compromised so easily.
is there a way i can  beef up security on the nat connection? or cud it be my on board ethernet nic?

Hmm ...

Not sure why you are having problems then. Hopefully someone with some experience with wither VMWare or your card will offer some advice.\

As far as security, NAT is better then a bridge, and, IMO, you can not protect Windows by running it in VMWare, you need to harden windows just as if you were running on a physical box, ie, antivirus, firewall, etc.

---

### Post by SILLAT on 2008-09-29
OK KOOL :)
THNX FOR THE TIP guess i'm stuck using NAT but its all gud cuz windoze i rarely use windoze, jus trying to secure my pc
THNX AGAIN

---

