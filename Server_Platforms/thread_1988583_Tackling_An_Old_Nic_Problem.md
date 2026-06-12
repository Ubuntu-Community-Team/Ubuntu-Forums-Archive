---
title: "Tackling An Old Nic Problem"
date: 2012-05-27
forum: Server Platforms
---

### Post by Watchlord on 2012-05-27
This is it guys. I gave this up last year, but now I have some time to finally get to the bottom of this. I have a server with identical, dual NICs. I want to host a proxy and website through one NIC, and a Ventrilo and Minecraft server though the other. (I have all of that running fine on one NIC now). 

I tried for weeks last time and I was unable to figure out how to do that. It would set up one NIC and then the other perfectly and then they would stop working at all when I rebooted. It was almost as if the MAC address was traded at random between the two cards. Sometimes, after I got out of my frustration induced fetal position I would go to take another look and both cards would have the same MAC address...](*,) what!? I would configure both and then connect only one, when I rebooted it was a 50/50 chance whether I had internet or not. I am totally stumped.

I just had to give up and disable on of the cards, and everything ran smoothly. This is the only computer issue I've never been able to fix. I will fix it or die trying :evil:.

Anyway I'm running 11.04 Server on an [HP Proliant DL380 G3.]("http://h18000.www1.hp.com/products/quickspecs/11473_div/11473_div.html")

Questions, tips, comments,...words of encouragement?

---

### Post by NigelRen on 2012-05-28
I would have thought the MAC address comes from the BIOS rather than the operating system level.  If you Google - 'dl380 g3 mac address' there seems to be several things out there about MAC addresses not behaving/sticking.

---

### Post by Watchlord on 2012-05-28
> **NigelRen said:**
> I would have thought the MAC address comes from the BIOS rather than the operating system level.  If you Google - 'dl380 g3 mac address' there seems to be several things out there about MAC addresses not behaving/sticking.

I know...I've had people tell me the problems I'm seeing are impossible.

---

### Post by Watchlord on 2012-05-28
Sometimes I'd get that settled, then I would create two connections. Everything would work fine until I rebooted. It seems like it would try to apply both connections to one card when I rebooted. This would cause me not to have any connection. I couldn't get the settings to stick to the cards.

---

### Post by NigelRen on 2012-05-28
have you tried what's recommended in [http://h30499.www3.hp.com/t5/ProLiant-Servers-ML-DL-SL/Proliant-DL380-G3-lost-MAC-address/td-p/3166570?](http://h30499.www3.hp.com/t5/ProLiant-Servers-ML-DL-SL/Proliant-DL380-G3-lost-MAC-address/td-p/3166570?)

My desktop always complains about invalid MAC addresses at boot due to slightly iffy BIOS flashing practices, but never had any problems with either NIC.

---

### Post by Watchlord on 2012-05-28
To be honest, it's been a while, but I did everything I could hardware wise. Excuse my noob-logic, but I think it's an Ubuntu issue. Whenever I set up individual connections on each card, it seems like, when I reboot, all network configurations are applied to one card.

For example here's what I'd set up.

eth0 > NIC A
eth1 > NIC B

Then Ubuntu or whatever demon is living in my server would make this happen.

eth0 & eth1 > NIC A
herp derp > NIC B

I could not narrow down an error because multiple things would happen. I couldn't even figure out what card I was on half the time.

Please excuse my not knowing the exact names of everything. I'm in Windows right now. I would post from the server, but it's already 80 in my house and this server puts out more heat than an oven.

---

### Post by NigelRen on 2012-05-29
When this happens, can you run
```
arp -a
```
which should show the various connections along with the MAC address and post the results.

---

### Post by Watchlord on 2012-05-29
:shock: I fixed it...not sure what I was doing differently. I just decided to take another whack at it. I deleted all me connections and configured each card from scratch like I've done many times before. For some reason, this time it worked.

Maybe something was fixed in an update? I did the same fix that I've tried multiple times with no success.

---

