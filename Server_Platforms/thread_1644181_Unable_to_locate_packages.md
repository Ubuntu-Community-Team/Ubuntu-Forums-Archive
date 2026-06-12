---
title: "Unable to locate packages"
date: 2010-12-12
forum: Server Platforms
---

### Post by elkingrey on 2010-12-12
Hello,

I am a total noob in the process of trying to build my own server. I installed Ubuntu 10.10 but when I did that I didn't have the computer hooked up with an ethernet or have any internet connection. During the installation process it was unable to set up DHCP, so I figured I would just do that later, somehow. 

Anyways, I recently hooked up an ethernet cable from the server to another computer, which has internet.

I've been slowly working my way through the Server Documentation and am on the Networking chapter. It has given me the commands to install wireless-tools, ethtool, dhcp3 server and I've also tried to install gedit. Every time it gives me the error:

E: Unable to locate package XXX

When I ran the sudo lshw -class network command I find that it recognizes both an ethernet interface as well as a wireless interface(my wireless adapter). BOTH of them say *-network DISABLED. 

My goal is to enable both of those, but I am assuming I need to be able to locate the packages first. I installed the server edition using a USB pendrive. I still have the files on the pendrive, but I don't know how to make the server locate those files. I'm guessing it wants to access the installation files to locate the packages to install. 

Again, I'm a TOTAL noob, so if you can help me I would be very appreciative. But I'll need to be baby stepped through the process. Thank you!

---

### Post by Vegan on 2010-12-12
```
sudo apt-get update
sudo apt-get upgrade

```
than you can try install packages again

---

### Post by elkingrey on 2010-12-13
The updating failed to fetch and the upgrading did nothing, probably as a result. 

I currently have no internet connection running to that computer. The wireless adapter is plugged in, but never recognized and my ethernet has never been recognized either. So, do I need to get it hooked up to the internet before I can do anything? If so, how?

---

### Post by fistv on 2010-12-13
YOu can either figure out the networking as an exercise or just do a reinstall with EVERYTHING plugged in. That way the hardware will be detected.
Personally I would use a router unless you know how to setup the 'other computer' as a proxy. 
Ubuntu's hardware detection is and has been pretty good over the years but can be a minor annoyance when new hardware is added.
As far as updates are concerned, something is going on with the update servers and has been funky for the past 3 days. I have 7 ubuntu servers running here but have not installed any new ones for about 4 months now. I just installed this one  I'm on now on Friday the 10th as a test bed for netbackup 7 as a client before trying it on our development servers three of which are going to become production servers, but not until I have netbackup running.
It took me 5 hours to get a basic desktop installed. 
I would just do a fresh install, just make sure everything is plugged in.

---

### Post by snowpine on 2010-12-13
This command will display your networking interfaces:

```
ifconfig
```

If you see your ethernet card (usually eth0) then it is recognized. Plug it in to your router and:

```
sudo dhclient
```

That should get you connected so you can upgrade/install packages.

---

### Post by elkingrey on 2010-12-13
ifconfig gives me:

lo

and

vibr0

but not eth0. 

Is there another way besides having to plug directly into the router? Is plugging into the router only a temporary thing in order to quickly download some upgrades and then the server will be wireless ready? 

It would be kind of a pain to have to plug into the router, but if it's only a temporary thing in order to make it wireless ready then I'd do it. But if it's meant as a permanent setup I would need to find another way.

---

### Post by fistv on 2010-12-13
Sometimes the only way is to plug in especially if it did not pick it up on install. I usually keep my server on first install on the workbench then once it is in it gets moved to a rack and my adderview gets plugged in. That vibr0 is a virtual bridge, only seen that associated with xen.

---

### Post by elkingrey on 2010-12-13
Okay. So I am in the process of trying to reinstall and I have come upon the network part again. It says it recognizes multiple network interfaces, both the ethernet and the wireless. However, I have tried to install using either one of them and for both of them it says that my network is probably not using the DHCP protocol. This is probably the case because I don't even fully understand what DHCP is. Does this mean I have to do some stuff on some of the other computers in the house before I can get things rolling on this new server? 

On a side note, my wireless adapter DID find my router and when asked for the WEP password it failed to connect because it says it is probably not using the DHCP protocol. I do know we are using a WPA key and not a WEP key, but I don't know if that would be the problem. I am also not sure if the Ubuntu Server software would automatically come equipped with the driver necessary to utilize my wireless adapter. 

Any thoughts?

---

