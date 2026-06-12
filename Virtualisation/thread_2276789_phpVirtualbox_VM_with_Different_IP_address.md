---
title: "phpVirtualbox VM with Different IP address"
date: 2015-05-05
forum: Virtualisation
---

### Post by Phil_Jackson on 2015-05-05
Hello,

I am trying to configure a VM with a IP address that is the same as my LAN

currently the host has 192.168.x.x
guest has 10.0.x.x

i would like my guest VM to have something in the range like my host. So i'm guessing i need my router to issue my VM a IP address but i have been unable to accomplish this. I hope i am describing my problem correctly. Please post questions and i will respond, thanks Ubuntu community

---

### Post by etescartz on 2015-05-05
There is an option in Virtualbox , to select the particular networking scheme you're asking about. 
If you select "Bridged Adapter" under your VM's >Settings>Network > Attached to:  menu the Ip address will be assigned by the local network's DHCP server , and not by Virtualbox.

This works exactly the same in phpVirtualbox as it's just a web frontend for the headless Virtualbox service you installed on your Linux machine , and setting menu options are exactly the same.

Enjoy your Virtualboxing!

---

