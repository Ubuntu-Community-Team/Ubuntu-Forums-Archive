---
title: "5 minutes with the feisty cd"
date: 2007-04-19
forum: The Cafe
---

### Post by steve196 on 2007-04-19
* It runs very fast on a 1.4 GHz cpu with 512 Mbytes RAM
* It still ships with the nonworking dhcp program and you need to go online with another OS  to download the one that works (i have lost hope, they will ever fix this)
* Compiz is fast on a radeon 7500 (on the beta it was unusable and couldn't be turned off, but that is no more). Getting the cube is a matter of luck, but that is not really a problem. The manpage of compiz is not very informative and the "desktop settings" panel has only two checkboxes, so i couldn't do the stunning stuff that one sees in Youtube videos).
Overall: nice thing, but i do not see a good reason to upgrade from my current dapper system.

---

### Post by beniwtv on 2007-04-19
> **steve196 said:**
> * It runs very fast on a 1.4 GHz cpu with 512 Mbytes RAM

Yes, that's our Ubuntu :)  Running on AMD Duron 1.3GHZ 640MB RAM and it flies!

> **steve196 said:**
> 
* It still ships with the nonworking dhcp program and you need to go online with another OS  to download the one that works (i have lost hope, they will ever fix this)

Which program? Did you make a bug report?  :)  Keep in mind the developers can't fix bugs they don't know of...

> **steve196 said:**
> 
* Compiz is fast on a radeon 7500 (on the beta it was unusable and couldn't be turned off, but that is no more). Getting the cube is a matter of luck, but that is not really a problem. The manpage of compiz is not very informative and the "desktop settings" panel has only two checkboxes, so i couldn't do the stunning stuff that one sees in Youtube videos).

It runs very fast with the 3D cube on my AMD system! It has a Geforce4 :guitar: 

And also, I could very well disable it in the beta, just by clicking the 'disable' button. Hmm.. But keep in mind Compiz is still not stable software.

Now, the only two things I miss in Ubuntu are:

* Bluethooth GUI tools installed by default. Let's face it: When a dongle is supported in Ubuntu, the user should have the tools to interact with it.

* Proper networking support. The built-in Network manager still lacks manual configuration. The manual configuration tool lacks WPA/WPA2, ISDN, DSL, GPRS/UMTS and proper modem connections. Don't get me wrong we have already much of the required code if not ALL code, we just need a tool for the average Joe to get his internet connection working.

Other than that, Ubuntu is perfect for me! :) 

Now, let's join the Feisty party! :popcorn:

EDIT: AArrgg! Typo :(

---

### Post by steve196 on 2007-04-19
The nonworking dhcp program is named "dhclient", the working one "dhcpcd". It is not on the cd, which is annoying, because i get no internet without it. I had filed a bug report about it.

---

### Post by beniwtv on 2007-04-19
> **steve196 said:**
> The nonworking dhcp program is named "dhclient", the working one "dhcpcd". It is not on the cd, which is annoying, because i get no internet without it. I had filed a bug report about it.

Hmm. Strangely, dhclient never failed for me. Not in broadband and not in wireless either. Do you have a link to the bug report?

---

### Post by steve196 on 2007-04-19
[https://bugs.launchpad.net/ubuntu/+bug/83591](https://bugs.launchpad.net/ubuntu/+bug/83591)

---

### Post by steve196 on 2007-04-21
I have the general impression, that launchpad has been deserted by developers and the bug reporters are among themselves there. It seems to make more sense, to talk about bugs here.

---

### Post by Unterseeboot_234 on 2007-04-21
I have all my development work in Dapper. I followed the herd and .torrent download.  I was impressed Fiesty Live-CD could immediately go out to my DSL-internet link. I was online! I could mount any network drive to the shared partitions on my Win boxes. Dapper sure couldn't do that right out of the box. So, I wonder, if Dapper is "contaminating" my Fiesty. If I got rid of Dapper would I have to fumble through all the setups again?

I installed Fiesty (64-bit) on its own partition just to see what it does from the hard drive. I have to say it boots s-l-o-w compared to Dapper. That, and now I've got GRUB installed now. Now when I turn the computer on I have to wait for GRUB, select Dapper and then go get my cup of coffee. Fiesty was supposed to be ready for UbuntuStudio. I haven't checked that out just yet. But I did notice the Add/Remove interface has been sharpened up, and there are a lot of pre-built software packages I won't have to build again. Unless Fiesty has more features, I'm sorry I installed Fiesty with the GRUB. GRUB is difficult for me to get rid of and maintain a prior install.

I will have to be very cautious about development and always quesiton if Dapper borrowed anything or if Fiesty borrowed anything from the other's partition.

---

### Post by Unterseeboot_234 on 2007-04-21
(didn't mean to double-post, happened because the message window will timeout while I type)

---

### Post by Bezmotivnik on 2007-04-21
> **steve196 said:**
>  i do not see a good reason to upgrade from my current dapper system.
Especially when it doesn't seem to work as well on any of my systems. :( 

I don't get it.  Functional progress seems to have stopped for me at 6.06, which works reasonably decently for me.

Does the 64-bit version work any better in AMD 64 machines than the i386 one?

---

### Post by macogw on 2007-04-21
dhcp doesn't work? huh?  it works for me...always has.  seems like it works for everyone else or we wouldn't be able to go online to begin with and none of us would use ubuntu.  are you sure it's not that your driver is stupid about dhcp?

---

### Post by muguwmp67 on 2007-04-21
I just installed  feisty on my dell C610 laptop.  I'm pleased.  Its much snappier than edgy was.  The main reason I upgraded though was for the wireless networking stuff, which works great!  Straight out of the box support for my wireless card, no hassling with restricted drivers, and a net browser.

I'm not sure I want to upgrade my desktop just yet though.

---

### Post by Happy_Man on 2007-04-21
> **steve196 said:**
> * Compiz is fast on a radeon 7500 (on the beta it was unusable and couldn't be turned off, but that is no more). Getting the cube is a matter of luck, but that is not really a problem. The manpage of compiz is not very informative and the "desktop settings" panel has only two checkboxes, so i couldn't do the stunning stuff that one sees in Youtube videos).


You need to install "gnome-compiz-manager" for all the special stuff. Still not as much as Beryl gives you, though. :(

---

### Post by steve196 on 2007-04-23
I now have internet on the feisty cd!!
I brutally removed everything dhcp related (i do not know how, but it can do that on the cd) and installed dhcpcd from the harddisk. I had to give it the DNS adresses manually, because for some reason even dhcpcd never gets those (on any debianlike system).
For some reason, ubuntu-minimal depends on the broken dhcp client, so it went off with it, but i see no issues resulting.

---

### Post by steve196 on 2007-04-23
Just after submitting this, massive cd reading activity started and the system became more and more unresponsive and finally ended up in a complete freeze (mouse and numlock key and CtrlAltBackspace, CtrlAltDel, CtrlAltF1 not working)
But this may have to do with my half-defect cd drive.

---

### Post by 3rdalbum on 2007-04-23
> **macogw said:**
> dhcp doesn't work? huh?  it works for me...always has.  seems like it works for everyone else or we wouldn't be able to go online to begin with and none of us would use ubuntu.  are you sure it's not that your driver is stupid about dhcp?

For the record, DHCP doesn't work for me on Mac or Ubuntu (Ethernet ADSL modem). It does work OOTB on some other distros, and with a little bit of configuration on the XP. So I don't use DHCP - I typed in the DNS addresses, a static IP and the router's IP address. I guess it makes the system start up faster, and it's also easier to set up the port forwarding on the router too for when I want to run a web server!

---

### Post by angryfirelord on 2007-04-23
Post some of the errors you get when you run **dhclient** *your_network_device*. I've always used it under Debian and that has still worked fine.

Feisty overall was very impressive, but I didn't like the new installer. It seemed to take a while to go from page to page and the modified partitioner isn't as organized as plain GParted was.

---

### Post by steve196 on 2007-04-23
This was on the feisty live system:
> ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/[censored]
Sending on   LPF/eth0/[censored]
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$ 
Somehow this doesn't look very informative.

---

### Post by angryfirelord on 2007-04-23
Try **/etc/init.d/networking restart**.

If that doesn't work, then post your */etc/network/interfaces* file.

---

### Post by steve196 on 2007-04-24
Why should something suddenly work after restarting it a second time?
/etc/network/interfaces is the one on the feisty cd.
The problem must be dhclient itself, because dhcpcd gets an adress and a connection within fractions of a second.

---

### Post by Ymer on 2007-05-23
There is a problem with the dhclient, all of those distros using it are not able to setup my netwrok at home, only those with dhcpcd could do that properly. Actually I read somewhere (don't remember now where and I'm not expert in this either) that it doesn't work because of issues with IPv4 and IPv6.

---

