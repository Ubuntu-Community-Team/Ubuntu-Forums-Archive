---
title: "SSH into different servers behind same firewall"
date: 2012-03-16
forum: Server Platforms
---

### Post by CrusaderAD on 2012-03-16
I have a server setup roght now behind my firewall that I can SSH into from outside. I have port forwarding rules setup obviously for SSH going to that machine. What if I wanted to SSH into another maching on the same network? Do I have to make SSH listen on a different port and setup port forwarding on this new port?

---

### Post by haqking on 2012-03-16
> **CerealCypher said:**
> I have a server setup roght now behind my firewall that I can SSH into from outside. I have port forwarding rules setup obviously for SSH going to that machine. What if I wanted to SSH into another maching on the same network? Do I have to make SSH listen on a different port and setup port forwarding on this new port?

change the ssh port

edit

```
/etc/ssh/sshd_config
```

cheers

---

### Post by CrusaderAD on 2012-03-16
Nice, thanks for the reply! Is there a list of ports I can use?

---

### Post by spynappels on 2012-03-16
You could just ssh to the normal machine and from there ssh to the other one you want to access, saves changing port numbers. If you want them both to be accessible from outside, you will need to do what you said.

you can use pretty much any port you like, use some above 1024 though.

---

### Post by haqking on 2012-03-16
> **CerealCypher said:**
> Nice, thanks for the reply! Is there a list of ports I can use?

well known 0-1023 (dont use)
registered 1024-49151 (you can use but be careful and make sure nothing is currently using any of them)
Dynamic 49152-65525 (safest option)

Dont just choose any, make sure no current service or installed app is using it.

Cheers

---

### Post by spynappels on 2012-03-16
> **haqking said:**
> well known 0-1023 (dont use)
registered 1024-49151 (you can use but be careful and make sure nothing is currently using any of them)
Dynamic 49152-65525 (safest option)

Dont just choose any, make sure no current service or installed app is using it.

Cheers

Yeah, sorry I should have said to use any above 1024 that is not in use by anything else.

Listen to Haqking, he is wise.

---

### Post by CrusaderAD on 2012-03-16
Thanks everyone for the input! Solved!

---

### Post by haqking on 2012-03-16
> **spynappels said:**
> Yeah, sorry I should have said to use any above 1024 that is not in use by anything else.

Listen to Haqking, he is wise.

no worries, not so sure about wise, it is based on the amount of whisky left in the bottle ;-)

Peace

---

### Post by CrusaderAD on 2012-03-16
> **haqking said:**
> no worries, not so sure about wise, it is based on the amount of whisky left in the bottle ;-~)

Peace

Liquid courage, it what's tomorrow is all about! That and St. Patrick, of course.

---

### Post by Vishal Agarwal on 2012-03-16
you can get he port list in 
less /etc/services

---

### Post by Ms. Daisy on 2012-03-26
> **Vishal Agarwal said:**
> you can get he port list in 
less /etc/services
That was very helpful, thank you! 

It took me some googling just now to figure out how to connect to a non-standard port. Thought I would add the syntax here for others:
```
ssh -p 61808 user@server
```

---

### Post by OliverHaslam on 2012-03-26
Quick question for my own curiosity, unless I've completely missed the point due to my relative n00bness!

Why not just SSH in using the local IP?

---

### Post by haqking on 2012-03-26
> **OliverHaslam said:**
> Quick question for my own curiosity, unless I've completely missed the point due to my relative n00bness!

Why not just SSH in using the local IP?

because the OP is SSH'n from outside to more than one machine inside, if its internal then of course you just SSH to the IP, from outside you can only SSH to the public facing IP not a LAN address

---

### Post by OliverHaslam on 2012-03-26
> **haqking said:**
> because thew OP is SSH'n from outside to more than one machine inside, if its internal then of course you just SSH to the IP, from outside you can only SSH to the public facing IP not a LAN address

Ah, with him saying he wanted to SSH into another machine from the same network I thought he meant locally. I must have misunderstood.

---

### Post by haqking on 2012-03-26
> **OliverHaslam said:**
> Ah, with him saying he wanted to SSH into another machine from the same network I thought he meant locally. I must have misunderstood.

No worries

from the OP

> I have a server setup roght now behind my firewall that I can SSH into from outside

Which is the point, he has 2 machines on the same network which needs to SSH to, to do that from outside requires different SSH ports for forwarding to appropriate IP on the LAN

Cheers

---

