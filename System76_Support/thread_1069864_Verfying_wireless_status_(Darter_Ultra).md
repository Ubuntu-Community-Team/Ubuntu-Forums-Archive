---
title: "Verfying wireless status (Darter Ultra)"
date: 2009-02-14
forum: System76 Support
---

### Post by pseudotheist on 2009-02-14
So, I get that Fn-F11 supposedly turns wireless on and off, but:

a) does it really?  Seems like the wireless card still knows about all the local networks, it just won't let me talk to them.

b) how do I check which state it's in?  Looks like ifconfig only tells me if I've received DHCP info, not whether the card is active.

---

### Post by thomasaaron on 2009-02-15
If you right-click the network manager icon and then de-select "Enable Wireless Networking" you will not be able to see or connect to networks. 

I don't believe it removes power from the card (as it's still seen by iwconfig), but I think this keeps it from transmitting or receiving.

---

### Post by perce on 2009-02-16
Does unloading the driver turn power off to the card?

---

### Post by thomasaaron on 2009-02-16
Hmmm...

Yes, I just tried that and it worked like a charm.

To remove it...
```
sudo rmmod iwl3945
```

To re-install it...
```
sudo modprobe iwl3945
```

Your module name will vary. Run...
```
lsmod
```
...to find yours.

---

