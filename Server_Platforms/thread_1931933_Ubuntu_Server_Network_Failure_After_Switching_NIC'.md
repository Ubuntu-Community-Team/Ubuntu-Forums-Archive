---
title: "Ubuntu Server Network Failure After Switching NIC's"
date: 2012-02-26
forum: Server Platforms
---

### Post by jlacroix on 2012-02-26
Hello everyone. I have a standard desktop computer I'm using as a server. It only handles Unison syncing between a few laptops, and a few other things, so it doesn't have much of a work load. It is running Ubuntu Server 11.10. 

The PC I bought is a nice and fast machine, but the Gigabit network card it came with SUCKS. I've heard that this card is problematic on Linux anyway, so I bought a PCI 1X card to replace it with.

I chose to get an Intel Gigabit PCI 1x card that my local computer store is selling, and it said on the product page that it is Linux compatible. So, I bought it, I installed it and disabled the onboard NIC.

Now, whenever I boot the server I get "Waiting for network configuration" followed by "waiting 60 more seconds for network configuration" (or an error close to that, I don't have copy and paste capability since I have no network connection). 

Whenever I run "ifconfig" it ONLY shows the loopback device, and NOT the Intel card I purchased. If I run "lspci" it shows that I have an Intel card, model 82574L. So it does see the card, but it doesn't apply it to eth0 or eth anything as ifconfig shows nothing.

I Googled around for the errors above, and the only results I get are those from people having this problem after upgrading from one version of Ubuntu to another. Ubuntu Server 11.10 is the only thing this server has ever had.

From what I can tell, it appears this card is relatively well supported in Linux so I'm clueless why it won't enable it, perhaps it's still expecting my old card?

Sorry this is so wordy, trying to give as much info as possible beforehand ;)

---

### Post by CharlesA on 2012-02-26
Try running:

```
sudo ifconfig -a
```

You'd probably have to mess with /etc/udev/rules.d/70-persistent-net.rules to get it to read as eth0.

---

### Post by jlacroix on 2012-02-26
> **CharlesA said:**
> Try running:

```
sudo ifconfig -a
```

You'd probably have to mess with /etc/udev/rules.d/70-persistent-net.rules to get it to read as eth0.
Brilliant! You're a genius. Thank you!

---

### Post by rubylaser on 2012-02-26
+1 CharlesA.  This almost definitely the problem. You can do this the easy way like this.

```
sudo -i
cat > /etc/udev/rules.d/70-persistent-net.rules
reboot
```

Should come right up after the reboot

---

