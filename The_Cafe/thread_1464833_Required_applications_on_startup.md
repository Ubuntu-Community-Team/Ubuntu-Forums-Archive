---
title: "Required applications on startup"
date: 2010-04-28
forum: The Cafe
---

### Post by ShadowedSun on 2010-04-28
Hello, I just came to Ubuntu after using Windows XP for a very long time. My friend suggested it after I got a virus and could not get rid of it.
  
I am running on a fairly old laptop (and trying to optimize my startup time), and am wondering what Startup Applications are _actually_ required? 
Ubuntu 10.4 /GNOME:

I currently have these checked for startup:
1. Certificate and Key Storage 
2. Disk Notifications 
3. Network Manager 
4. Power Manager 
5. PulseAudio Sound System
6. Secret Storage Service
7. SSH Key Agent
8. Update Notifier
9. User folders update
I DO use my wireless occasionally. And sound. And rarely (but is useful) cordless/on battery.

Also, if you could help me out any what they actually do, that would be appreciated. 

Thanks!
(Oh and sorry if this has been answered before; I tried searching, to very little results...)

---

### Post by Mrs Twaddle on 2010-05-01
I'd like to know this too.
Cheers!

---

### Post by Bölvaður on 2010-05-01
remove the bold ones

1. Certificate and Key Storage  (giving the network manager super user rights to be able to connect to wifi networks... you are able to be without it, but it's noob friendly so keep it)
**2. Disk Notifications **
3. Network Manager (I as in 1. to connect to wifi, you dont really need it but it is noob friendly and being without the network manager can be difficult in some cases)
4. Power Manager (this is a laptop right?)
5. PulseAudio Sound System (you might want to change to alsa, but I love pulse so keep it just for me ;))
6. Secret Storage Service (never heard of this)
**7. SSH Key Agent (not needed unless if you use ssh)**
**8. Update Notifier (you are able to open the update application your self by going to system &#8594; administration &#8594; update manager, but if you remove this it will not automatically notify you when there are updates)**
**9. User folders update (it's not important)**


now install a program called boot up manager ([to install bum click here]("apt:bum"))
now you are able to cut more fat!
just look through what is there and use your own judgement, what you got on the list probably differs from every one else's list so you cannot ask anyone except the one's that got exactly the same install as you and havent done any changes.

---

### Post by ShadowedSun on 2010-05-01
Oh wow, thank you very much! :guitar:
Secret Storage Service has the description "GNOME keyring: Secret Service." I don't what that does either. I kept update manager just because it tends to slip my mind to update; plus, it's just easier for it to tell me. But I took all your other advices, and I'll try the boot up manager! I appreciated the descriptions as well :)

Thanks again!!

---

