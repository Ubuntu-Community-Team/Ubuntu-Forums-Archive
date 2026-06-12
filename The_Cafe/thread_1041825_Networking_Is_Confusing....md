---
title: "Networking Is Confusing..."
date: 2009-01-17
forum: The Cafe
---

### Post by kevin11951 on 2009-01-17
I need help...

My router allows me to connect the Internet via the wireless but not the wired connection...

have you ever heard of anything like this?

EDIT: just got weirder. i can connect to my wired server via ssh, and sftp, but i cant upload anything, and it wont download anything.

---

### Post by phrostbyte on 2009-01-17
Do you have MAC filtering?

---

### Post by kevin11951 on 2009-01-17
> **phrostbyte said:**
> Do you have MAC filtering?

no, and it does not matter which computer i connect to the router, they all dont work (via the wired)

---

### Post by FuturePilot on 2009-01-17
> **phrostbyte said:**
> Do you have MAC filtering?

MAC Filtering shouldn't affect the wired connections.

Some things come to mind:
Bad cable?
Bad port in the router?

Are you trying to connect to the wired connection on the same computer that you're connecting via wireless?

In that case, on the wired computer is there any firewall settings/blocked ports etc?
Bad Network card?

---

### Post by kevin11951 on 2009-01-17
> **FuturePilot said:**
> MAC Filtering shouldn't affect the wired connections.

Some things come to mind:
Bad cable?
Bad port in the router?

Are you trying to connect to the wired connection on the same computer that you're connecting via wireless?

In that case, on the wired computer is there any firewall settings/blocked ports etc?
Bad Network card?

none of those account for the fact that i can connect to the server, but it just wont download anything.  in fact the server part of it works: [http://99.20.92.234/](http://99.20.92.234/) see?

---

### Post by airjaw on 2009-01-17
Time to buy a new router.

In my experience, routers just aren't worth the trouble to troubleshoot. Too many variables, too many quirks of routers, too many router defects.

Routers break and/or have problems quite often. It sounds like you just have a faulty router. Buy a used 802.11b for like $15 and be done with all your troubles.

---

### Post by Mr. Picklesworth on 2009-01-17
> **airjaw said:**
> Buy a used 802.11b for like $15 and be done with all your troubles.

Uh, yah, except for the three foot wireless range and snail-tastic speeds.

I have a D-Link DIR-655 router. I used to not trust D-Link stuff since the brand sounds like Compaq; designed for "simplicity" and compromising quality. (Indeed it is with the cheaper routers, just like Linksys). This router is a major exception to that, though. It seems to be pretty much invincible for my network and has PILES of options. It hasn't existed in my house for a year yet so time will be the real judge, but it hasn't stumbled yet, whereas every router I owned previously needed frequent rebooting. The trick is to accept that they tend to be built with really frail, cheap hardware in the 'inexpensive' realm. Having gone through about 5 routers in as many years, I have finally accepted the fact that a well built router makes everything way happier.

I've seen people turn old computers into routers with good results, although I bet that's pretty ugly for power consumption.

---

### Post by LookTJ on 2009-01-17
Did you recently upgrade a new firmware to the router?

**EDIT:  **

by the way it could be "bricked" router which is usually caused by a bad flash of the firmware

---

### Post by handy on 2009-01-17
> **Mr. Picklesworth said:**
> 
I've seen people turn old computers into routers with good results, although I bet that's pretty ugly for power consumption.

I use an old PIII with [*_IPCop_*]("http://www.ipcop.org/") as a firewall/router/proxy (& some other services) I love it, my old Siemens SpeedStream 4200 was flaky, now it runs in bridge mode just as a modem & IPCop handles the routing faultlessly.

If you get one of the slower PIII's or better yet a PII you get the lowest power consumption, a MiniITX intel or VIA board is a great option for those that want to spend more than the $5- the PII & PIII's are worth these days. :-)

---

### Post by uzo on 2009-01-17
Let's see your network interface content in the /etc/network/interfaces

---

### Post by billgoldberg on 2009-01-17
> **kevin11951 said:**
> I need help...

My router allows me to connect the Internet via the wireless but not the wired connection...

have you ever heard of anything like this?

EDIT: just got weirder. i can connect to my wired server via ssh, and sftp, but i cant upload anything, and it wont download anything.

Never heard of anything like that.

You could try a hard reset *(this brings back the router to factory settings, thus you'll need to enter your enter account and password again to get on the web)* or a firmware update.

---

### Post by billgoldberg on 2009-01-17
Or buy a new one :p

---

