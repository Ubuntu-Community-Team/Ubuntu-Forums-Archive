---
title: "router with wifi, and a firewall"
date: 2010-08-09
forum: Server Platforms
---

### Post by fdelval on 2010-08-09
Hello all

My isp gave me a router which has wifi.
I added an ubuntu box acting as a router, so the layout is this:

router+wifi ---------------- ubuntu (as router proxy firewall) ---------- lan

Now, the lan has 192.168.2.0 subnet, and the external interface of the router is in the 192.168.1.0 subnet

So the problem is that the wifi assigns 192.168.1.0 ip's which doesnt belong or get filtered through my router/firewall...

what solutions can you give me??

---

### Post by arrrghhh on 2010-08-09
Turn off the DHCP server on your ISP's router, and make sure you have DHCP enabled/configured on your Ubuntu server, which you should already based on your description.

Then your clients have no choice but to get an address from the Ubuntu server.

---

### Post by Bachstelze on 2010-08-09
Don't use the wifi.

---

### Post by arrrghhh on 2010-08-09
> **Bachstelze said:**
> Don't use the wifi.

That's not exactly helpful.  I use wifi and love it.  I know it's not secure, and slow... but who cares, it's convenient!  Those who are concerned about security and speed use wired already.  If not, that's their issue.

---

### Post by fdelval on 2010-08-09
oh, just disabling dhcp will work? i will try...

i asked because i started messing around with ipcop, endian, pfsense and all those firewall distros, and i got intriged with the blue zones (wifi)

i never tryed wifi before, but i thought it would be a nightmare to get wifi going on ubuntu...

About security... you never know with wifis, but i think i got the best encryption available on the router so... cross fingers..

aside from that, any other tip to get it working even safer?


thank you

---

### Post by Bachstelze on 2010-08-09
> **arrrghhh said:**
> That's not exactly helpful.

It's the only correct answer. The wifi comes directly from the router, there's absolutely no way to make the signal go through the firewall.

---

### Post by arrrghhh on 2010-08-09
> **Bachstelze said:**
> It's the only correct answer. The wifi comes directly from the router, there's absolutely no way to make the signal go through the firewall.

My wifi router has the DHCP server disabled and DHCP is provided thru my Ubuntu server - so addresses are handed out from Ubuntu.  Perhaps I didn't understand the OP... Either that or you didn't understand the OP :P

---

### Post by Bachstelze on 2010-08-09
> **arrrghhh said:**
> My wifi router has the DHCP server disabled and DHCP is provided thru my Ubuntu server - so addresses are handed out from Ubuntu.  Perhaps I didn't understand the OP... Either that or you didn't understand the OP :P

You didn't. This is not just about IP addresses, it is about being on the wrong network.

---

### Post by arrrghhh on 2010-08-09
> **Bachstelze said:**
> You didn't. This is not just about IP addresses, it is about being on the wrong network.

I'm so glad you feel to thoroughly understand the OP's problem enough to tell him/her what they shouldn't be doing... but don't offer anything in the way of what they should be doing.

If you're not going to be helpful then don't post anything.

---

### Post by Bachstelze on 2010-08-09
> **arrrghhh said:**
> 
If you're not going to be helpful then don't post anything.

oh hey, youmad?

OP said they want to use an Ubuntu machine as a router/firewall. The problem is that since the wifi comes directly from the router, obvioiusly connecting with it will bypass the firewall. If they want traffic to actually go through the firewall, they must not use the wifi. I don't know what else I could say.

---

### Post by arrrghhh on 2010-08-09
> **Bachstelze said:**
> oh hey, youmad?

OP said they want to use an Ubuntu machine as a router/firewall. The problem is that since the wifi comes directly from the router, obvioiusly connecting with it will bypass the firewall. If they want traffic to actually go through the firewall, they must not use the wifi. I don't know what else I could say.

Eh I'm a little mad.  Posts like yours are what turn people away from Linux in general.  I prefer to try and help rather than just post stuff like "Don't use wifi".  This attitude is one of the main reasons that Linux has such a bad rep for being an elitist type system, one that if you don't know the answer already then you're worthless.

Like I said, if you're not going to be helpful just don't post.  I was going to try and work with the OP to see what he/she was trying to achieve.  You didn't offer any help, just what they shouldn't be doing.

---

### Post by fdelval on 2010-08-10
oh, peace guys, and thank you for stopping by the thread

i feel like Bachstelze is right, lets see the layout again


isp router with wifi --------------------------- ubuntu firewall -------------------------------- lan
internet // 192.168.1.1 ------------192.168.1.254//192.168.2.254-----------------------.......


well, all 192.168.2.x ip's will get filtered.

Wifi will only assign 192.168.1.x ips, so.... ?????????????????????

---

### Post by mr-woof on 2010-08-10
Do you have a switch on the Lan side of the ubuntu router? If yes, what you could do is turn off the wifi on the isp router. Buy a wifi access point and attach it to the switch on the lan side of the router, therefor getting  192.168.2.x addresses. 

The traffic will be filtered through the ubuntu router and you'll be able to still use wifi. :) 

Otherwise Bachstelze is right, you won't be able to use the isp wifi and want it filtered through the ubuntu router.

Out of interest, what are you using for the ubuntu firewall? 10.04 with the firewall on or ipcop/smoothwall etc?

---

### Post by JonathanSG on 2010-08-11
Not sure of your setup exactly but if you do have a switch, most modern routers can be used as network access points with DHCP, UnP&P, RIP switched off. All you need to do is plug the router into the switch and assign it a fixed IP something like 192.168.2.1 making sure that it is in the same subnet(255.255.255.0 or whatever you are using) as the Ubuntu server. plug in LAN port to switch
Then set the DHCP range on the ubuntu server at something like .30 to whatever you need. Your Ubuntu Server will handle all the IP assignment and you can configure your ubuntu firewall as you wish
If the router provided by the ISP is one of those combine modem / NAT routers this won't work.

---

### Post by fdelval on 2010-08-11
thank you all, i will try and report it back




> **mr-woof said:**
> 

Out of interest, what are you using for the ubuntu firewall? 10.04 with the firewall on or ipcop/smoothwall etc?


I first started with ipcop, which turned out to be very "small" for my needs, so i added tons of addons, but its too much puzzle
i followed with endian which is an enhaced ipcop, but i disliked the firewall, and the lack of wan failover and QoS habilities for my taste
ebox is a good replacement, but it messes a lot with the packages... i installed the VIM editor, and 5 packages got deleted...
pfsense is a BSD distro, and its far from my linux knowledge, so i dropped it despite it looks very good with all options you could think of
now, i have an ubuntu built from the ground

nothing like doing it for yourself

---

