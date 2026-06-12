---
title: "How do I fix my nic? (work fine with desktop ver., doesnt with server ver.)"
date: 2009-04-10
forum: Server Platforms
---

### Post by c3lica on 2009-04-10
Ok, so am trying to install ubuntu server on a computer. It has an ASUS P5QL Pro mobo. The nic works great when I boot to a live cd of ubuntu desktop (8.10) but when I try to install ubuntu server (8.10) it says that it can not detect a network interface. 

So, obviously the nic can work with ubuntu but it does not want to work when I install server. Does anyone have any suggestions on what I should do to get it working?



Here is a link to the mobo with the onboard nic...
[http://usa.asus.com/products.aspx?l1=3&l2=11&l3=710&l4=0&model=2307&modelmenu=2](http://usa.asus.com/products.aspx?l1=3&l2=11&l3=710&l4=0&model=2307&modelmenu=2)

If you need any other information let me know and I will try and find it for you.

):PThanks):P

EDIT: The LAN is atheros AR8121/AR8113 ... drivers can be d/led from asus for linux [here]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5QL%20PRO"). Should I just install server without the nic and then attempt to install the drivers after that?

---

### Post by windependence on 2009-04-10
There is usually no need to install any sort of drivers in Linux because they are built directly into the kernel. Load the OS, and then attempt to bring up the interface. Also, my experience is that 8.10 is rather buggy. Try the 8.04 LTS release. You're not gaining much of anything in 8.10 anyway. If you need help after you get the OS installed, we can help you. I am sure there is already support for your nic in the OS.

-Tim

---

### Post by c3lica on 2009-04-10
ok, well I can't instal 8.04 LTS cuz it doesn't recognize my hdd or nic and I would rather just fix the nic in 8.10... so I am going with 8.10. Now, how do I bring up the interface... when I do a ifconfig all i get is lo.

---

### Post by FrankT-Qc on 2009-04-10
ifconfig, by default, will only output interfaces that are up and running...

You could try ```
ifconfig -a
``` or ```
ip link show
``` to see if it's there 

Now, if it's there (let's pretend it's called eth0 and that your local net is 192.168.1.0 netmask 255.255.255.0) just try give it a simple configuration like this (as root)

```
ip link set up dev eth0
ip address add 192.168.1.254/24 dev eth0
```

After that, your box should sit at 192.168.1.254 (make sure no one else uses that address...), you might want to try to ping it... if it fails, make sure it's not a firewall problem...

---

### Post by c3lica on 2009-04-10
Thanks.
```
ip link set up dev eth0
ip address add 192.168.1.254/24 dev eth0
```

That worked... I was able to ping myself, my router, and other computers on the network. 

How would I go about making this happen from start up? just edit /etc/network/interfaces (I am going to make the server have a static IP anyways)

---

### Post by FrankT-Qc on 2009-04-10
Weepee !!!

If you want this to happen at boot, yes, you should put your configuration in /etc/network/interfaces ... it could look like 

```
auto iface eth0
iface eth0 inet static
	address 192.168.111.1
	netmask 255.255.255.0
        # ... anything else... 

```

Make sure you don't have "Network Manager" running on this machine if you're going to use static IP...

"man interfaces" at the command line will tell you more about /etc/network/interfaces ...

---

### Post by c3lica on 2009-04-10
Thanks a lot!

I had to add my gateway but everything is working now.

NOTE: I had to do a apt-get update before I could install openssh-server (or anything else)

but seriously, thank you. I bought the mobo open box from newegg and didnt know if the nic was defective.

---

