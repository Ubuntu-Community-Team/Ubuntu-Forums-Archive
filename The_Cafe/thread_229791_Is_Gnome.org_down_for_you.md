---
title: "Is Gnome.org down for you?"
date: 2006-08-04
forum: The Cafe
---

### Post by mostwanted on 2006-08-04
It's been down for me the last 24 hours :S

I miss my planet Gnome.

---

### Post by scxtt on 2006-08-04
nope, works for me ...

---

### Post by 23meg on 2006-08-04
Down right now.

---

### Post by scxtt on 2006-08-04
still works for me :p

---

### Post by Jucato on 2006-08-05
Works for me. I'm also still receiving feeds from Planet GNOME.

---

### Post by mostwanted on 2006-08-05
Damn, this is strange. I see no other reason than the probability that they somehow blocked my IP.

---

### Post by OffHand on 2006-08-05
> **mostwanted said:**
> Damn, this is strange. I see no other reason than the probability that they somehow blocked my IP.

can you ping it in the terminal?

```
ping www.gnome.org
```
```
ping 209.132.176.176
```

---

### Post by mostwanted on 2006-08-05
I got some help at #gnome and did a *tracepath* to gnome.org and it told me that traffic wasn't even leaving my network, so I restarted all networking devices I could find in my house and it works now :)

I feel pretty stupid to have created a topic about this when it's a local problem, but just found it strange that it only affected gnome.org and subdomains.

---

### Post by OffHand on 2006-08-05
> **mostwanted said:**
> I got some help at #gnome and did a *tracepath* to gnome.org and it told me that traffic wasn't even leaving my network, so I restarted all networking devices I could find in my house and it works now :)

I feel pretty stupid to have created a topic about this when it's a local problem, but just found it strange that it only affected gnome.org and subdomains.

At least it is working again  :)

---

### Post by ComplexNumber on 2006-08-05
its fine for me. i've just gone there now.


> **mostwanted said:**
> Damn, this is strange. I see no other reason than the probability that they somehow blocked my IP.
i think thats probably it. it happens with everyone from time to time. when it happens again, just switch your router on then off, and try again (this will change the IP address). it will then work.
strangely enough, this problem only seems to occur on windows - never on linux :-k

---

### Post by OffHand on 2006-08-05
> **ComplexNumber said:**
> when it happens again, just switch your router on then off, and try again (this will change the IP address). it will then work.

This will not change the ip address. Your modem and router will pick up the same lease again if there isn't a new lease available.

---

### Post by ComplexNumber on 2006-08-05
> **subsonic_shadow said:**
> This will not change the ip address. Your modem and router will pick up the same lease again if there isn't a new lease available.
it does. it changes the last block. for example, if the IP that appears to the external network(ie the internet) is currently 111.22.33.444. if you switch the router off then on again, the IP may become 111.22.33.*123. *its never failed to change it, ever.
perhaps you're referring to the IP address on the internal network that connects the router to your PC. in that case, switching the router off then on doesn't change that.

---

### Post by OffHand on 2006-08-05
> **ComplexNumber said:**
> it does. it changes the last block. for example, if the IP that appears to the external network(ie the internet) is currently 111.22.33.444. if you switch the router off then on again, the IP may become 111.22.33.*123. *its never failed to change it, ever.
perhaps you're referring to the IP address on the internal network that connects the router to your PC. in that case, switching the router off then on doesn't change that.

I was talking about the ip address that is visible to the world, not the internal network. When you powercycle the modem/router it will just send a new request to the dhcp server of your isp. If the lease that is available for you is the same as the lease that you had before the powercycle you will get the same ip address again.

---

### Post by ComplexNumber on 2006-08-05
> If the lease that is available for you is the same as the lease that you had before the powercycle you will get the same ip address again. like i say, its never failed to change it on my router.....ever.

---

### Post by OffHand on 2006-08-05
> **ComplexNumber said:**
> like i say, its never failed to change it on my router.....ever.
I suppose it depends on the way isp use dhcp

---

### Post by scxtt on 2006-08-06
i've never seen the IP address for a cable modem just change ... and i've unplugged them numerous times -- this is also w/ different modems and 2 different cable providers ... my parents have had the same IP for years, spanning 2 or 3 different routers and mines been the same for the 6 months i've been living here ...

---

### Post by TravisNewman on 2006-08-06
Mine has only changed about twice in the past 2 years and I have reset my router a bunch of times, mostly because of power failures. I've had the router off for a week and got the same IP address when I plugged back in.

---

