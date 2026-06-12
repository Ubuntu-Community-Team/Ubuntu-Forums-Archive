---
title: "Can I setuo a Linux router on a VM?"
date: 2007-12-16
forum: Virtualisation
---

### Post by tuproxy on 2007-12-16
I don't want to run my PC 24/7 and use it only as a router.  I was wondering if I setup a small VM on my server and run it as a router.  This will be better than running my P3 system, burning 150 watts/hour.

---

### Post by kitofhawaii on 2007-12-17
Hey there,

Configuration depends on which VM host software you use.  In either case, it's about creating two bridges, one for the "outside" interface and the other for the "inside" interface, which is the one your server usually uses.

I'm going to assume that you already know how to use the VM software you're using for creating regular guests, so this'll be a basic summary of what you need to do:

VMWare -----
For VMWare Server, you use "sudo vmware-config-network.pl" to configure the bridges (I'd suggest using wizard mode.)  You also want to make sure to disable NAT when prompted, since this is not required.  I'd give the steps, but depending on how your VMWare was set up initially, the wizard runs differently.  But the key parts are making sure to set up bridging and disabling NAT.

When all is finished with the script, it'll list all the bridges your machine has and which interface they're mapped to.  You then set up and configure your guest with two network cards, one pointing to the inside bridge (probably vmnet0) and one to the outside bridge (possibly vmnet1 depending on your hardware.)

Make sure that your server's outside interface also does not have a static IP address, and does not run dhcp.

VBox -----
You have to manually create tap interfaces and bridges to use a VBox guest.  Here is a good explanation for setting up tap interfaces (you'll want to create two, one for your outside interface and one for your inside.)  

[http://www.virtualbox.org/discussion/1/141](http://www.virtualbox.org/discussion/1/141) 

You'll then need to create your vm guest, go to settings, network, and activate two network interfaces.  The types you want are Host Interface.  Under each interface, make sure to provide the TAP interface name (as explained in the above link,) one for outside and one for inside.

Also, as with VMWare, make sure that your server's outside interface also does not have a static IP address, and does not run dhcp (when creating the bridge as above for the outside interface, ignore the steps regarding setting up a static address.)

For both -----
After that, since you've already set up a Linux router already, it should be pretty self explanatory what to do.  Just treat the bridges as regular interfaces.  Whatever you are connecting to probably is retaining ARP information for your old PIII box, so you'll need to reset your modem to clear arp when you switch to the virtual machine.  You'll also want to make sure you're not binding any services like Apache from your server to the outside interface (this shouldn't cause any harm, since above you have to make sure the outside interface does not have an address.)

I hope this is a fairly clear summary, but if you need help with any particular steps, let me know.

-Kit

---

