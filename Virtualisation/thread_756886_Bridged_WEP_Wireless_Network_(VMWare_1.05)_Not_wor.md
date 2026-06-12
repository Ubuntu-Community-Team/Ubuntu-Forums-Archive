---
title: "Bridged WEP Wireless Network (VMWare 1.05) Not working"
date: 2008-04-16
forum: Virtualisation
---

### Post by thepossiblehuman on 2008-04-16
Hello,

I am running Gutsy on a Dell Latitude D610 with the restricted Broadcom 43xx Chipset driver installed for my wireless adapter.  I installed VMWare following this tutorial:

[http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/](http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/)

I am trying to run a Windows XP SP2 VM on my workstation.  When I use my actual ethernet port, I have no problems.  It gets an IP and all is right in the world. :)  When I attempt to use my wireless card, it won't get an IP at all.

Now, I bridged both network adapters, but when I add a second "bridged" network adapter to my VM it seems to just bridge to my ethernet port.  If I switch it to custom to use vmnet2 (where the wireless adapter is bridged to) it doesn't get an IP.

I've even removed my VMware server networking config and re-ran it adding only the wireless adapter as a bridged adapter and then added that to the VM, and still no joy.  

I have a WEP key for my wireless network, but shouldn't my adapter on the host machine take care of that?  I know with Paralells on a Mac it does, but all my Vmware Server experience is in the enterprise where I never had to have wireless support for vm's.  

The worse part is when there is no network connection, the VM itself slows to crawl.  I need the XP VM for some work apps that do not run in WINE, and it is a pain using a laptop but having to depend on a wired network connection.

Any ideas?

---

### Post by drdrewdown on 2008-04-16
there is a rule in some 802.11 protocol that says you cannot spoof a mac address over the wireless lan.  vmware is spoofing this mac of your VM thus not obeying that rule which is why you are not having any luck

if you choose to use your wireless connection the only way to do it, is with NAT on your vm.  i've certainly farted around with it enough to know it wont work unless you have some workaround i couldn't find.  just know the issue is with the wireless protocol in reference to spoofing mac addresses.

do a quick search on google or these forums & you will find more info.


cheers

---

### Post by thepossiblehuman on 2008-04-16
That makes sense.  I could very well have my Parallels VM NAT'ed and just forgot about it.  I'll check when I get home because if I don't then it is straight up bridged and breaking that rule.  It'd be an interesting note.  Thanks.  Anybody else know of a work around?

---

### Post by drdrewdown on 2008-04-16
vmware is a lot more stable then parallels & both support NAT networking.. i'd recommend using the vmware with NAT vs the parallels with NAT..

---

### Post by thepossiblehuman on 2008-04-16
I got a first gen Intel Mac, and Parallels was the only show in town at the time for Mac-hosted VM's.  It works and is stable, which is all I really need.  Again, it's just for work-related windows apps and some web apps that only work correctly with IE.  There is really no need for me to get VMWare for Mac.

I will say that I am impressed with Paralells performance compared to free VMWare Server on Windows though.  My Mac is dual-core 2.0Ghz with 2GB of RAM and only 330MB or so is allocated to the XP VM.  It is snappy and responsive with no lag what-so-ever.  The VM runs far better than other similar VM's I've built on server class machines with VMWare Server that have more powerful processors and considerably more RAM allocated to them.  I'd blame Windows as VMWare ESX doesn't show the same behavior.  Heck, even using a Linux console to connect to the Windows-hosted VM's is snappier than connecting to them via Windows console on the exact same model/spec machine.

---

### Post by thepossiblehuman on 2008-04-16
The NAT'ing worked.  Thanks for that.  VPN was funky as I had to connect through the host.  Connecting through the client was touch and go.  

As for Parallels, it is bridged, but they spoof an unique MAC address.  Pretty neat feature.

---

