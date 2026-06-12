---
title: "Virtualbox 3.0.8 Age of Empires II"
date: 2010-01-31
forum: Virtualisation
---

### Post by RoCkAs on 2010-01-31
Hello,

I'm using Virtualbox 3.0.8 with host Ubuntu 9.10 64bit and guest OS Windows XP Pro. I want to play Age of Empires II on lan but guest's ip is soooo strange (something like 10.0.2.15), not even close with my "original" 192.168.2.6. What i have to do to configure guest's ip to be able to play AoE II on lan?

Thanks in advance, RoCkAs :-):-)

---

### Post by fouadatmeh on 2010-02-01
Hello,

You have to make the network adapter for the virutal machine as a "bridged adapter" and it will take IP addresses from your LAN..
But you cannot play games on virtual machines in general because they still don't support 3d!!!

---

### Post by RoCkAs on 2010-02-01
I will try this and tell you the results. As for the gaming, yes, you are right, i can't play 3d games, but AoE II is 2d and soooo old. I' ve tested it and the game is working really smooth. :-) :-)

---

### Post by RoCkAs on 2010-02-01
Ok... Now i have "original" ip [192.168.2.4] and i can see the lan game that my friend creates, i press the join button but i stack there. When i create a lan game my friend can log in and see whatever i'm typing in chat, but i can't see what he is typing... So i guess is port forwarding problem. Any suggestions on how i can open the necessary ports on my Guest OS via Virtual Box? I've read the documentation and i can't really understand anything...

Thanks anyway!!! :-) :-)

---

