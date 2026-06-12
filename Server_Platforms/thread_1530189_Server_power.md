---
title: "Server power"
date: 2010-07-13
forum: Server Platforms
---

### Post by Austin25 on 2010-07-13
I have an old desktop, a Dell Optiplex,(Pentium 4, 256MB RAM, 19GB Hard drive) that I got from a school a couple of years ago because they were upgrading. I was wondering, how much more use could I get out of it if I converted it to a server? I'm very new to servers, and I would like to get a little experience with these.

---

### Post by garfonzo on 2010-07-13
You could get a lot of use out of it, depending on what you want to do. If all you want is a file server for your home LAN, you're in great shape for that. I ran a file server with Ubuntu Server with lower stats than what you have and it was fine. I had multiple Windows computers accessing music, videos, documents via Samba from shares on the server without a hitch.

It all depends on what you want it to do.

---

### Post by Austin25 on 2010-07-13
Well, what I want to do with it depends on what I can do with it. Anything from file sharing to a website, to vpn. I would just like to put it to use. Also, right now it is running Windows, and it has a [Wifi Max]("http://us.codejunkies.com/Products/WiFi-MAX___EF000625.aspx") our family uses for just about everything, and I would like to know how/if I could get that set up under the server. Is it even possible?

---

### Post by CharlesA on 2010-07-13
You could probably install Ubuntu desktop onto it and configure sharing that way.

As for the wireless adapter, how well it works with Linux would depend on what chipset it uses.

---

### Post by Austin25 on 2010-07-14
Well, it's listed [here]("http://linuxwireless.org/en/users/Devices/USB"), but could I set it up as an access point? Could I do it under the server edition? Do I sound like a reality TV host before commercials? All these answers and more after the break. 

lol I couldn't stop myself, but seriously, is there a way to do it?

---

### Post by CharlesA on 2010-07-14
There might be, but I have no idea how to configure it as such.

---

### Post by Austin25 on 2010-07-14
I think I might be able to it with iwconfig. Amazing what you can learn from a command such as :```
man iwconfig
```

---

### Post by b@sh_n3rd on 2010-07-14
> **Austin25 said:**
> Well, it's listed [here]("http://linuxwireless.org/en/users/Devices/USB"), but could I set it up as an access point? Could I do it under the server edition? Do I sound like a reality TV host before commercials? All these answers and more after the break. 

lol I couldn't stop myself, but seriously, is there a way to do it?

lol :D about your original post on "what can I use it for?" I could give you an idea based on what *I* do myself...I have 4 systems between the ages of 10-12yrs...namely, 3 PII's and 1 PIII I use as my desktop..I use archlinux and I have the habit of trying to optimize everything as much as possible, like the kernel for example, so, you could just imagine how long it'd take on a single ancient system...so what I've done is, hooked up my PIII to the PII's in a server farm or cluster to use DistCC. That's what I use it mostly for, other than that I use one as a storage server and I even ran Win2000 Server in VirtualBox on top of linux, on a PII 400MHz system with just 128MB of RAM ;) :P

The thing is, with your system, many things are possible. All you need is some imagination and the will power to make it work :D I might use it just to play around with VB remotely..you know? install some OS'es, login remotely and play around with them? that's what they do in data centers for real actually...:P :P good luck and have fun! :) If you want some other tips based around something like this, just ask, I'd enjoy helping you out with what I've learnt so far myself :)

---

### Post by Austin25 on 2010-07-14
> **b@sh_n3rd said:**
> lol :D about your original post on "what can I use it for?" I could give you an idea based on what *I* do myself...I have 4 systems between the ages of 10-12yrs...namely, 3 PII's and 1 PIII I use as my desktop..I use archlinux and I have the habit of trying to optimize everything as much as possible, like the kernel for example, so, you could just imagine how long it'd take on a single ancient system...so what I've done is, hooked up my PIII to the PII's in a server farm or cluster to use DistCC. That's what I use it mostly for, other than that I use one as a storage server and I even ran Win2000 Server in VirtualBox on top of linux, on a PII 400MHz system with just 128MB of RAM ;) :P

The thing is, with your system, many things are possible. All you need is some imagination and the will power to make it work :D I might use it just to play around with VB remotely..you know? install some OS'es, login remotely and play around with them? that's what they do in data centers for real actually...:P :P good luck and have fun! :) If you want some other tips based around something like this, just ask, I'd enjoy helping you out with what I've learnt so far myself :)

Actually for Virtualization, I can do that directly on my laptop, an HP touchsmart tx2, but for instance, it's not a stable platform, as I turn it off frequently, or I'm out of range of wifi. If I were to make a website, what if it got visited too often, or it fell to the [slashdot effect.]("http://en.wikipedia.org/wiki/Slashdot_effect")

Hey, what about instead of a LAN party, a WLAN party?

---

