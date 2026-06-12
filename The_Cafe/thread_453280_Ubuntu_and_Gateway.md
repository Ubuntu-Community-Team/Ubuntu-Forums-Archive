---
title: "Ubuntu and Gateway"
date: 2007-05-24
forum: The Cafe
---

### Post by MattSMiddleton on 2007-05-24
Hello, I'm loooking into getting a new laptop and am interested in getting the Gateway MT3707.  I was wondering if anyone has had experience with Gateway laptops and Ubuntu specifically how well the wireless cards work.  If anyone has this particular model and has had experience with it it would be great to hear from you.  Thanks!

Matthew

---

### Post by reckless2k2 on 2007-05-24
Post the wireless card specs of the laptop and it can quickly be found whether there will be any bumps along the road with wireless setups.

---

### Post by maniacmusician on 2007-05-24
i asked the same question a while ago and heard that gateways are not too good for Linux.

Ideal linux-friendly vendors are Lenovo, System76 (of course), Dell, and I believe the fujitsu computers are linux-friendly as well.

---

### Post by MattSMiddleton on 2007-05-24
I'm going to do some digging a little later on the wireless chipset it's using Gateway's site doesn't seem to list it.  I'm not worried if it will take some work to get it up and running, I just don't want to buy into a laptop that will never be wireless.  I guess I could always buy a card too, anyone know which cards are linux-friendly?

---

### Post by Quake on 2007-05-24
.

---

### Post by reckless2k2 on 2007-05-24
You'll be able to get it running. It just depends on how easy the initial setup will be. There are many ways to get any card to work from ndiswrapper to a builtin module.

---

### Post by Andrewie on 2007-05-24
I'm running a Gateway mx3410

1) my laptop sleeps and wakes up but the screen is blank
2) internal sound card doesn't work, I don't have sound ( :( its been almost a year)
3)wireless card is detected, it finds networks but I can't connect
4) its got a nvidia card so beryl is super easy to set up and works good

I believe there is forum has a thread to make the card work, so it does work.

The sound issue is annoying enough to keep me out of Linux (Music+Video+Programming+Star Craft is all I do)

I like the laptop looks pretty good, and its pretty strong but your main issue is going to be sound. If your card has a intel network card its going to be even easier, can you post the specs of that model?

to summarize: no sound, won't wake up from sleeping are my issues right now

---

### Post by maniacmusician on 2007-05-24
> **Andrewie said:**
> I'm running a Gateway mx3410

1) my laptop sleeps and wakes up but the screen is blank
2) internal sound card doesn't work, I don't have sound ( :( its been almost a year)
3)wireless card is detected, it finds networks but I can't connect
4) its got a nvidia card so beryl is super easy to set up and works good

I believe there is forum has a thread to make the card work, so it does work.

The sound issue is annoying enough to keep me out of Linux (Music+Video+Programming+Star Craft is all I do)

I like the laptop looks pretty good, and its pretty strong but your main issue is going to be sound. If your card has a intel network card its going to be even easier, can you post the specs of that model?

to summarize: no sound, won't wake up from sleeping are my issues right now
I read: Gateway for Linux is really awful.

I exchanged some emails with Gateway customer service when I was looking at one of their computers, and their outlook towards Linux was basically "We don't care". If you want to get a Gateway laptop working, you'll have to use a lot of ugly hacks and workarounds which will most likely affect the stability of your system.

---

### Post by MattSMiddleton on 2007-05-24
Thanks to everyone for your input, I'll probably end up going with another system, I'll let you know how it works out.

Matthew

---

### Post by steven8 on 2007-05-25
Go with a Dell Pre-Installed Ubuntu machine!!

---

### Post by MattSMiddleton on 2007-05-25
I probably will eventually but seeing as how I can only pay w/cash as of right now (no checking or credit card set up yet) I'm probably going to get something retail and then in a little grab a Dell machine.  I definitely want to support that effort, just kind of need a laptop now and don't have time to set up everything and wait for delivery.

Matthew

---

### Post by MattSMiddleton on 2007-05-25
Looks like the Gateway I was looking at (MT3707) uses a RealTek 8185 Wireless chipset with is marked to work out of box w/6.06 and 6.10 so I'll let everyone know how it works out for me.

---

### Post by Andrewie on 2007-05-25
> **MattSMiddleton said:**
> Looks like the Gateway I was looking at (MT3707) uses a RealTek 8185 Wireless chipset with is marked to work out of box w/6.06 and 6.10 so I'll let everyone know how it works out for me.

my laptop has the same card

---

### Post by macogw on 2007-05-25
> **maniacmusician said:**
> i asked the same question a while ago and heard that gateways are not too good for Linux.

Ideal linux-friendly vendors are Lenovo, System76 (of course), Dell, and I believe the fujitsu computers are linux-friendly as well.

Hey! My Gateway MX6920 works great with Ubuntu!  Dapper/Edgy overheat (acpi problem), but that's gone with Feisty.

Not all Gateways have the same wireless cards.  Get a Centrino (Intel cpu, chipset, and wireless), and it'll work out of the box (true for any company).

---

### Post by SFCampbell on 2007-06-02
> **MattSMiddleton said:**
> I probably will eventually but seeing as how I can only pay w/cash as of right now (no checking or credit card set up yet) I'm probably going to get something retail and then in a little grab a Dell machine.  I definitely want to support that effort, just kind of need a laptop now and don't have time to set up everything and wait for delivery.

Matthew

Matt you may be able to buy a Dell Ubuntu system over-the-counter at their local kiosks in many shopping malls.  Also, I don't have any accurate information about the time frame but I have been told that Dell will soon be retailing their systems out of WalMart, so keep your eyes open.

Campbell

---

### Post by lsalminen on 2007-06-02
I have a Gateway MX3228 and it uses a Realtek RTL8185L wireless adaptor, and after I unblacklisted the drivers, the wireless worked right away. 

So, after 3 minutes of work, it was working fine.

---

