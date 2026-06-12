---
title: "a rougue router"
date: 2010-09-08
forum: Security
---

### Post by gerontium on 2010-09-08
DIR-615
1c:bd:b9:b4:d8:40
unique identifier : 26c8980c-727e-2c4a-b7c0-1cbdb9b4d840
serial number 00000000
 
sits behind a firewall - but is using kde - possibly stealing passwords and other information
 
this may not be the original device this device may either be moving in a car or
be static and be being used by an outside signal - this device does not hack into your home router it attaches wirelessly to your laptop and possibly uses localhost loop device connections 
 
beware - have not heard of it attaching to linux machines but - all windows machines are definately vunerable
 
individual responsible has not been found yet

---

### Post by CharlesA on 2010-09-08
Right. What exactly do you expect us to do about it?

If you are connected to a wifi hotspot you should at least tunnel yer traffic so that it's encrypted.

---

### Post by HPD2 on 2010-09-08
We cant really do any thing about it so why worry. as long as your not connecting to it whats the issue?

---

### Post by uRock on 2010-09-08
If you use ubuntu, then activate ufw. This will block all incoming traffic that you didn't create.```
sudo ufw enable
```

---

### Post by BkkBonanza on 2010-09-09
Really. What's the point of telling us if you don't say what area he's operating in?
I mean I'm in Bangkok, Thailand. Has he been seen here lately?
And what's the point of listing info like MAC address that can be changed randomly anyway.

If you aren't configuring your wifi for WPA nowadays then you are being negligent with your own security. And at public wifi either use a tunnel or don't expect privacy. 

Besides rogue hotspots there are plenty of other techniques for joining and subverting insecure wifi networks.

btw ufw doesn't help in this situation. Sure it'll stop connect attempts but typically a rogue AP is interested in eavesdropping for passwords and without an encryption layer you're blabbing to the world.

---

### Post by uRock on 2010-09-09
> **BkkBonaza said:**
> Really. What's the point of telling us if you don't say what area he's operating in?
I mean I'm in Bangkok, Thailand. Has he been seen here lately?
And what's the point of listing info like MAC address that can be changed randomly anyway.

If you aren't configuring your wifi for WPA nowadays then you are being negligent with your own security. And at public wifi either use a tunnel or don't expect privacy. 

Besides rogue hotspots there are plenty of other techniques for joining and subverting insecure wifi networks.

btw ufw doesn't help in this situation. Sure it'll stop connect attempts but typically a rogue AP is interested in eavesdropping for passwords and without an encryption layer you're blabbing to the world.
I was under the impression the OP might have been running WPA. You are right, people should keep their networks more secure. The more hacked machines we have on the world wide web, the more DoS attacks we'll be seeing, amongst other things. I only use wireless at my school and then I do not go anywhere that requires a password. All but one system in my home are wired and I have done everything possible in my router to make the network safer, but I still have NIDS running.

---

