---
title: "interesting ubuntu server problem"
date: 2011-06-28
forum: Server Platforms
---

### Post by SOMDdan on 2011-06-28
Hi Guys, I was hoping someone can help me with a unique problem. 

I recently acquired a rather new laptop with a busted screen. It is a Compaq Presario laptop, and the lid was flimsy enough to accidentally bend it and crack the LCD, and now everything is a blur. Instead of replacing the screen (which I may end up doing eventually), I though that it would be useful to use the laptop as a Ubuntu server, since it has a 250 GB hard drive and enough memory, and all that good stuff. As a server, it would not necessarily need a working screen, because all communication with it would be over SSH anyway. The external monitor port does work, and I can use the computer that way, but I have found that getting the laptop to a point where the external video port is activated almost always requires that the operating system be loaded and running to a certain degree, but that also requires some input at startup, such as entering a password (or hitting a function key to boot from CD), but it is impossible to know when to do that because the screen is a technicolor blur. 

My first rather clever way of getting around this was to take the hard drive out, put it into another laptop and load Ubuntu server onto the disk and then putting the disk back into the gimpy laptop. Now the gimpy laptop runs and boots into ubuntu server automatically to the point where the external monitor activates. 

So problem solved, right?     Not so fast.

Although I can interact through the external monitor, the ethernet port is dead. When I installed Ubuntu server on the disk, (while it was in the other laptop), I did give it an ethernet address consistent with my network, and enabled OpenSSH. With the HD back in the gimpy laptop, I ran ifconfig and the only interface that showed up was the lo interface. Running lshw shows the ethernet controller, with the physical address of 0, so it is there. I have tried to assign a network address with the ifconfig command, but it keeps telling me that the device is not present ("etho: error fetching interface information: Device not found"). Trying to restart networking gives me similar results. My only guess is that because I installed the OS while the HD was in a different laptop, the installation program detected a different ethernet card and installed a different driver t hat the one in the busted laptop.

SO.....how do I get networking working, without being able to use an ethernet connection to get the right module?

---

### Post by thetopcat2010 on 2011-06-28
can you please verify are the two laptops 100% the same ?
if not that could explaine your problem .

---

### Post by Thegmandrive on 2011-06-28
Could be a Bios setting issue, with the broken Laptop. I'm not sure how you would be able to check the bios settings without a working screen. 

This may seem like an obvious question... Have you tried starting, or restarting the server, with an active Ethernet connected? Ubuntu Should be able to detect hardware changes when it boots.

---

### Post by TechSupportx86 on 2011-06-28
first off, let's hear it for the plug and play OS. makes life so easy =^_^=

second, this is a result of the plug and play OS >_<. 

I did the same thing, and am having the same problem. I was just going to re-install (it's only a crappy test server anyway with minimal install), but since someone else is having the same problem i shall try to figure it out (brb).

---

### Post by TechSupportx86 on 2011-06-28
wow, that was easy. Ok so i am guessing the 1st install saw eth0 as the device with the MAC: XX:XX:XX:XX:XX:X1

Now that it's in the new PC with a new network card (and MAC), it doesn't see XX:XX:XX:XX:XX:X1 anymore, but it sees XX:XX:XX:XX:XX:X02. Therefore the "eth" you need is most likely "eth1".

Here is what i did:

run
```
ifconfig -a
```and get the device name (it's probably going to be "eth1" as it is the second NIC the OS has seen)

Then open up the interfaces config with your favorite editor (i like nano)

```
sudo nano /etc/network/interfaces
```And simply change any reference to "eth0" to "eth1" (or whatever ifconfig -a showed you), then assign a static IP while your there. Save your work and either restart your PC or just ifconfig, doesn't matter.

So simple it's stupid :wink:

---

### Post by Thegmandrive on 2011-06-29
> **TechSupportx86 said:**
> wow, that was easy. Ok so i am guessing the 1st install saw eth0 as the device with the MAC: XX:XX:XX:XX:XX:X1

Now that it's in the new PC with a new network card (and MAC), it doesn't see XX:XX:XX:XX:XX:X1 anymore, but it sees XX:XX:XX:XX:XX:X02. Therefore the "eth" you need is most likely "eth1".

Here is what i did:

run
```
ifconfig -a
```and get the device name (it's probably going to be "eth1" as it is the second NIC the OS has seen)

Then open up the interfaces config with your favorite editor (i like nano)

```
sudo nano /etc/network/interfaces
```And simply change any reference to "eth0" to "eth1" (or whatever ifconfig -a showed you), then assign a static IP while your there. Save your work and either restart your PC or just ifconfig, doesn't matter.

So simple it's stupid :wink:

Octums Razor at it's best!!!

---

### Post by SOMDdan on 2011-06-30
> **TechSupportx86 said:**
> wow, that was easy. Ok so i am guessing the 1st install saw eth0 as the device with the MAC: XX:XX:XX:XX:XX:X1

Now that it's in the new PC with a new network card (and MAC), it doesn't see XX:XX:XX:XX:XX:X1 anymore, but it sees XX:XX:XX:XX:XX:X02. Therefore the "eth" you need is most likely "eth1".

Here is what i did:

run
```
ifconfig -a
```and get the device name (it's probably going to be "eth1" as it is the second NIC the OS has seen)

Then open up the interfaces config with your favorite editor (i like nano)

```
sudo nano /etc/network/interfaces
```And simply change any reference to "eth0" to "eth1" (or whatever ifconfig -a showed you), then assign a static IP while your there. Save your work and either restart your PC or just ifconfig, doesn't matter.

So simple it's stupid :wink:


As Johnny Carson used to say to Ed McMahon, "you are correct, sir!"

That did the trick!

---

