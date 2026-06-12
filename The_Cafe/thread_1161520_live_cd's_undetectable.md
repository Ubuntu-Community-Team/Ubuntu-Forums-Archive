---
title: "live cd's undetectable?"
date: 2009-05-16
forum: The Cafe
---

### Post by Zom-b on 2009-05-16
I was wondering if I was running a live version of linux on a network if it would be visiable to the network admins? anyone have mroe experiance in this sort of thing or any thoughts on on the matter?


edit: also if someone does know where more info on this sort of subject is that would be awesome

---

### Post by pwnst*r on 2009-05-16
> **Zom-b said:**
> I was wondering if I was running a live version of linux on a network if it would be visiable to the network admins? anyone have mroe experiance in this sort of thing or any thoughts on on the matter?



if it gets an IP, of course it's visible.  don't be pissing off network admins.

---

### Post by sailthesea on 2009-05-16
If you don't opt to connect to the network with the LiveCD it wouldn't be seen But a boot log would easily show you up to an Admin  
 Stealthing onto your home network is not a good idea 
 But that doesn't mean it can't be done (Ahem ! Google!)
;)

---

### Post by ice60 on 2009-05-16
it would be like a normal OS, on a LAN they'd even know it was you causing all the trouble by your MAC address lol.

---

### Post by Zom-b on 2009-05-16
hehe, I dont' plan on trying to piss off the network admins, I was just wondering, because I was looking at a distro live cd here at work and I didn't really mess around with it, because I was thinking "I"m not doing anything on the network but are they going to still see this activity?

---

### Post by MaxIBoy on 2009-05-16
If something connects to a network, it's going to show up. You could plug an Ethernet cable into an empty slot, chop the cable in half, and randomly fool around with the wire stands and a small battery. Chances are, it'll turn up on a log somewhere. (Okay, maybe not, but you get the idea.)

---

### Post by calrogman on 2009-05-16
> **ice60 said:**
> it would be like a normal OS, on a LAN they'd even know it was you causing all the trouble by your MAC address lol.

```
sudo ifconfig eth0 hw ether it:wa:sn:tm:e0:00
```

---

### Post by Zom-b on 2009-05-16
well I am going to have to make a home network and try out that battery idea lol

---

### Post by sailthesea on 2009-05-16
They will notice
 And they won't be happy!

---

### Post by ice60 on 2009-05-16
> **calrogman said:**
> ```
sudo ifconfig eth0 hw ether it:wa:sn:tm:e0:00
```
don't get clever with me, if you tried that on my LAN i'd still know because the MAC wouldn't have changed lol :D

---

### Post by Vostrocity on 2009-05-16
I tried that on a school computer once, but they were smart enough to have changed the boot order and locked the BIOS. :o

---

### Post by Nasaki on 2009-05-16
Depends on how attentive your admins are! I blatantly admit to running a frugal install of slax, on an FSF card at my prep school. Our IT department runs basic client management software, Bradford Network's NSA. Since the persistent client would not be running during a linux boot, it would be more then simplistic for them to tell if you were "misbehaving".

I have been booting Linux for several months without issue. My advice, if they try and check, they will know some thing is wrong...Don't let them know it was you! Write a bash script that runs at boot, reads Window's default hostname, etc. I see It is completely a situational.

Good luck! And abide to all policies!

---

### Post by init1 on 2009-05-16
> **Zom-b said:**
> I was wondering if I was running a live version of linux on a network if it would be visiable to the network admins? anyone have mroe experiance in this sort of thing or any thoughts on on the matter?


edit: also if someone does know where more info on this sort of subject is that would be awesome
Well they would know that you were using the network, but I'm not sure if they would know you were using Linux.

---

### Post by .Maleficus. on 2009-05-17
> **Vostrocity said:**
> I tried that on a school computer once, but they were smart enough to have changed the boot order and locked the BIOS. :o
Not at my school...  I've got Arch on an 8GB flash drive and can easily boot to it.  Then again, our IT department isn't exactly smart..  I Nmapped the wireless network with my iPhone and found something like a couple hundred open ports on their firewall, for things like Direct Connect and squid.  I KNOW they don't actually use either of those.

And port 22 is open.  Duh....

---

