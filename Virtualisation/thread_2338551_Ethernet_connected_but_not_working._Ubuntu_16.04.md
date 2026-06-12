---
title: "Ethernet connected but not working. Ubuntu 16.04"
date: 2016-09-29
forum: Virtualisation
---

### Post by qnkeee on 2016-09-29
internet connection is present and connected but no internet connection
[http://imgur.com/a/wtPtW](http://imgur.com/a/wtPtW)

---

### Post by ajgreeny on 2016-09-29
That IP of **130.204.96.100** is very unusual in my experience, as most modems or routers that I have seen have an IP of 192.168.#.#.

What router or modem are you using and do you have any other machines connected to it?
If you do, it may be possible to see the correct IP from one of them.

Can you actually ping the 130.204.96.100 which is your local hardware connection according to ifconfig?

---

### Post by qnkeee on 2016-09-29
[http://imgur.com/a/jNBiR](http://imgur.com/a/jNBiR) here you go

---

### Post by ajgreeny on 2016-09-29
Not sure what's going on here, but your router is certainly not 130.204.96.100.

It looks as if your computer's IP may be 192.168.0.2 so perhaps the IP of your router is 192.168.0.1, so try **ping 192.168.0.1** to see if that gets you anywhere..  Very often the router's IP is written on the label so have a look there if you can get to it and you may find its IP.

In the "Editing wired connection" window you show in your images, is that before or after you have made any changes to any configuration?

Sorry I can't be more definite on all this but I'm sure we can get the problem solved eventually, even though I am no expert in networking.

---

### Post by qnkeee on 2016-09-29
yo is there some way we can like chat in PM, so we can you know work this out faster if its not a problem? [http://imgur.com/a/jNBiR](http://imgur.com/a/jNBiR)[FONT=arial] [/FONT][http://imgur.com/a/wtPtW](http://imgur.com/a/wtPtW) check these tho

---

### Post by jeremy31 on 2016-09-29
Is this a virtual install as it appears to be or is Ubuntu the host?  I only tried a VM once with a Windows 7 host and Ubuntu 16.04 as the guest and I didn't have to touch anything to have internet access to the Ubuntu guest OS with VMware

---

### Post by qnkeee on 2016-09-30
yeah its on windows 10 hyper v virtual machine downloaded from: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

---

### Post by jeremy31 on 2016-09-30
*Thread moved to **Virtualisation**.*

There is a chance someone in this forum knows about any quirks that might be present in hyper v

---

### Post by qnkeee on 2016-09-30
what do i do now :( i need to work i have projects to do

---

### Post by heiko_s on 2016-10-01
With Linux as host, you would create a bridge and then connect the VM to the bridge. Can't say how this is done in Hyper V.

Inside the guest, it's easiest to use DHCP. Does your Ubuntu VM get the IP etc. via DHCP? Check your network setup in the Ubuntu guest. If you use Network Manager, open it up and see if DHCP is selected.

Your ifconfig output is rather irregular:

IP:                       130.204.**96**.100
Gateway (Bcast):   130.204.**111**.255

My advise: Enable DHCP in Network Manager or in the /etc/network/interfaces file (if you do not use Network Manager - make sure it's disabled). Then close the VM and go to Hyper V to set up networking. Have a look at [https://technet.microsoft.com/en-us/library/cc770380(v=ws.11).aspx]("https://technet.microsoft.com/en-us/library/cc770380(v=ws.11).aspx"), perhaps it helps.

Hyper V may require a network driver inside the Ubuntu guest, see [https://technet.microsoft.com/en-us/library/cc742460(v=ws.11).aspx]("https://technet.microsoft.com/en-us/library/cc742460(v=ws.11).aspx").

The drivers can be downloaded here: [https://www.microsoft.com/en-us/download/details.aspx?id=46842]("https://www.microsoft.com/en-us/download/details.aspx?id=46842")

Note: I have never used Hyper V, but created plenty of Linux and Windows VMs under VirtualBox, Xen, and lately KVM. Hope it helps.

---

