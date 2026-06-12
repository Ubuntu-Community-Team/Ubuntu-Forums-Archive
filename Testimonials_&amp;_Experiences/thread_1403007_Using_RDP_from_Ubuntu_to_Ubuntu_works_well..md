---
title: "Using RDP from Ubuntu to Ubuntu works well."
date: 2010-02-09
forum: Testimonials &amp; Experiences
---

### Post by noelvh on 2010-02-09
Just an FYI......
I was helping my Dad out Sunday, and I needed to remote into his machines to get his IP printing to work. He has 2 machines at 8.04, and one at 9.04. I was able to have him enable RDP set his port in the router and I was able to get in and work. The hard part is port forwarding to his machine and that is not so bad.

Oh and he is using an IoGear print server (not sure what model but a new one) and we found it only works with windows and mac, but if you use the HP jetdirect protocol it works just fine. As a mater of fact I was able to connect his 3 Ubuntu machines to the printer in the same time it took me to connect on XP machine. Now I did have to get the driver for the XP machine, and then I did not have to get one for Ubuntu, as it had it all ready.


Noel

---

### Post by jdrodrig on 2010-02-10
Thanks for sharing...

Just curious, have you tried connecting from outside your network...

---

### Post by Tamlynmac on 2010-02-10
> jdrodrig
		thanks for sharing...


+1

---

### Post by running_rabbit07 on 2010-02-10
> **jdrodrig said:**
> Thanks for sharing...

Just curious, have you tried connecting from outside your network...
My CISCO teacher showed me how to do that, but I haven't tried it. You have to find out which port your router is translating to the proper port on your PC for the app. I wish I could explain it as well as my teacher, but that's why he gets the money.

---

### Post by noelvh on 2010-02-11
Well I did not do a ture test other than go from one laptop to the other from with in but using my external IP. But I was RDPing into my Dad's computers and he is 500 miles from my house so that kind of counts.

With my dad here is what I did.
I went into his xp machine using showmypc.com Very easy cool to for windows and mac, with a linux viewer only. once there I went into his router and set up port forwarding to and IP in the range. So for the first computer I set the port forwarding to it on port 5900/59002. I then from his xp machine went to ipcheckin.com to see what his external IP was.
From here I walked him through setting up the RDP with a password and such. I then killed the showmypc.com connection and went through the RDP to his external IP with the :5900 added to the end and was in like flyn.

You can try it your self from with in using you external ip.

Noel

---

### Post by running_rabbit07 on 2010-02-11
> **noelvh said:**
> <snip>

Thanks for sharing that. I think I'll play around with it. I have installed Ubuntu on the mother-in-law's PC, so it'll be nice to be able to help her without driving to her house.

---

### Post by jdrodrig on 2010-02-11
> **running_rabbit07 said:**
> Thanks for sharing that. I think I'll play around with it. I have installed Ubuntu on the mother-in-law's PC, so it'll be nice to be able to help her without driving to her house.

I can always hear the commercial playing....

"Ubuntu, zero dollars....Avoiding your Mother-in-law....priceless"

---

### Post by freebeer on 2010-02-12
Yeah, it's a very convienient thing to set up.  I do that for my father's machine.  He's very poor in descibing what's on hiw machine - "there's a blue thing in my thing that I want to get rid of".  :p  So I remotely accessed his machine, figured out what he was really trying to say, then show him how to do it.

---

