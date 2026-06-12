---
title: "Need help with setting up network."
date: 2007-08-06
forum: The Cafe
---

### Post by NoSmokingBandit on 2007-08-06
I think i work at the only business in Pa that still doesnt have wireless internet, so my boss wanted to change that so he could use his laptop anywhere in the office, not just his desk. Anywho, i told my boss to get a linksys wireless access point which i could set up really easily, but instead he went out and bought a Netgear wireless-N router. I was going to just replace the old router with the new one, but the Netgear only has 4 wired ports and they need 6. So i guess what i need to do is get the netgear router to act like a wireless access point, but i dont know how. The main router is a Linksys besfr81 and the Netgear model is wnk854t. How can i set it up so one router works off of the other, or is it even possible?

---

### Post by tcpip4lyfe on 2007-08-06
Internet <===== Router <====== (uplink port) Switch < ====== Computers

The easiest way is to replace the linksys router with the netgear router and buy a switch. They are fairly inexpensive.  Make sure you buy more ports then you need.  Its cheaper to buy a 12 port switch now then a 6 port one and have to upgrade to a 12 later.   Then connect the netgear router to the switch (make sure you connect it to the uplink port).  Then plug in your comps.

You can connect the two routers together and use the linksys as just a switch (gateway mode) but that really isn't a good solution because after you connect the 2 routers together you'll only have 6 ports available. (assuming they both have 4 switching ports.) I can **guarantee** that you at some point they will want to connect a 7th computer down the road. 

Make your boss spend the money on a 12 port switch.

---

### Post by mips on 2007-08-06
Might be doable. It would be best to assign it a static IP address. Configure the wireless to use a different subnet and let it assign IPs to the host via DHCP. Use WPA encryption for security.

I have not looked up the router specs yet so I'm only taking a stab at it.

---

### Post by Turboaaa2001 on 2007-08-06
If you have a growing office then get a used Cisco 2600 24 port switch from e-bay. I got a 2600XL from there and it works great. The other thing you can do is attach the access point to the switch and configure the switch to have that port on a seperate vLan. This way wireless access is restircted to the internet and computers that are necessary for your boss.

As far as making things wireless. The best way is to just get an access point. They coist more than routers but it's all you need.  Just make sure to secure it ok!!!

---

### Post by NoSmokingBandit on 2007-08-07
Our office isnt growing at all, so i dont need to worry about adding more.

Ignore this thread from here on, i accidentally posted the same thing twice, so just ditch this thread. Im going to disable dhcp on the wireless and see what happens.

---

