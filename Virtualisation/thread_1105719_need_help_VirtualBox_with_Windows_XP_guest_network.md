---
title: "need help: VirtualBox with Windows XP guest network setup"
date: 2009-03-25
forum: Virtualisation
---

### Post by nacrotek on 2009-03-25
I am having a heck of a time getting my guest OS a network connection. I have followed the instructions I found in the VirtualBox article [here]("https://help.ubuntu.com/community/VirtualBox") and I still can't get things working in Windows XP.

Here is my setup:
Ubuntu 8.10 host OS using Sun VirtualBox v.2.1.4
Windows XP Pro guest
I have a router that assigns addresses to the host machine via DHCP.

The problem:
When I boot up into Windows XP the IP of the network adapter is always 0.0.0.0 and I can not ping, ssh, ftp, or http out from that machine. I also can not do ipconfig /renew or repair the connection. I have tried using all 4 of the virtual network adapters with the same results each time. I have also tried configuring the VirtualBox Host Interface networking with both eth0 and eth1 and no dice.

So....is there anyone out there who knows what I'm doing wrong? Or who can point me in the right direction? My Google-Fu has not served me well on solving this problem.

I know it's not a hardware issue as on another setup I had a Windows XP host OS with Ubuntu 8.10 as the guest OS. So I know it's possible :)

Thanks in advance.

---

### Post by blazemore on 2009-04-19
There's lots of information about networking in Virtualbox over at the Ubuntu Wiki.
The page you want is here: [https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)

If you find the answer, please try and post here so others can benefit as well.
Hope this helps!

---

