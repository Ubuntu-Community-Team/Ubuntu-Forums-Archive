---
title: "2 nic 's  with virtualbox"
date: 2015-11-23
forum: Virtualisation
---

### Post by angelo16 on 2015-11-23
Guys, I am a complete newbie in Ubuntu and I  need you help.

A installed Ubuntu which is my host and a Windows XP VM in virtualbox. Why XP ? well, I do have a software that only works in XP. This software connects to a PLC in the network ip range 10.0.1.XXX and I cannot change that range. 

Prior Ubuntu instalation, the computer had Win XP with one nic and another one  USB to ethernet adapter. The usb adapter was for  internet communication (IP from DHCP) and the nic was for PLC communication

Now that I have installed UBUNTU,  and XP in a VM I dont know how to setup the network. I had partial success setting the PLC to use the usb ethernet adapter and the nic for internet,  but the problem is that communication is not reliable with the PLC, so I need to revert this in order to use the nic for PLC and the USB adapter as I did when XP was the host  machine.
 

Can someone help me to configure the network and virtualbox ?

---

### Post by QDR06VV9 on 2015-11-24
See if this is of any help(Go to post of guyburns)
[https://forums.virtualbox.org/viewtopic.php?f=8&t=61096](https://forums.virtualbox.org/viewtopic.php?f=8&t=61096)
[COLOR=#333333][FONT=Lucida Grande] Windows XP will not automatically connect to the internet, though Windows 7 will.
Regards[/FONT][/COLOR]

---

