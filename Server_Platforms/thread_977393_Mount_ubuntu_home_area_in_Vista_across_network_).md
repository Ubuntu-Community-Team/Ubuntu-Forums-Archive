---
title: "Mount ubuntu home area in Vista across network :)"
date: 2008-11-10
forum: Server Platforms
---

### Post by brujoand on 2008-11-10
Hi, 
I have a dusty 8.04 server running in my university server-room. Now my brother has a Vista laptop (dont ask me why) and I have made a user for him on my server so that he can log in and store stuff. Now, I want to let him mount this area "/home/myBrother/" as a network drive on his Vista laptop.. What magic stuff do I have to do to fix this?

Thanx

---

### Post by PreviousN on 2008-11-10
Hi, when you say University Server Room...

Is the server accessible over the internet? Or is it firewalled...?

If it is accessible over the internet...then turn it off. That is very insecure o.0 ...

I'm going to suggest setting up a vpn for him. This will allow him to mount samba shares locally on his computer. 

I'm sure others will have other ideas, but I think that setting up a vpn is the best option for you. 

Good luck :-)

---

### Post by brujoand on 2008-11-10
It's accessible over the internett. Im hosting a few webpages there.
BUT, I found a really nice pice of software, SftpDrive will let me mount it up as a network drive AND provide the the encryption i need. But thanx for the suggestions :)

---

