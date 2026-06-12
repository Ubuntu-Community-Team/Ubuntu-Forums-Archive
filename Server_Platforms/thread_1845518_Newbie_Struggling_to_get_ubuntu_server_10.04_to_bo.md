---
title: "Newbie: Struggling to get ubuntu server 10.04 to boot"
date: 2011-09-17
forum: Server Platforms
---

### Post by andylyon87 on 2011-09-17
I have done a full install of Ubuntu server 10.04 64bit onto an E-machines ER1401

It has all installed without a hitch, however on the restart it does automatically it hangs at a blank screen with an underscore!

I am aware that this is a command line OS, however I am also aware I should be asked to log in as the master user. I dont get this far.

The software I have selected started as LAMP server, Open SSH Server and Mail server.

However as I am now on my 3rd attempt I have changed this to Basic ubuntu server and SSH server.

The graphics car is Nvidia, however the problem isnt in the display as far as I know, it is in the bootloader not working correctly. 

I have serached high and low for an answer to this and cannot find anything!

Anyone got any ideas?

---

### Post by papibe on 2011-09-17
A few questions:
[LIST]
[*]Do you see the grub menu when you boot?
[*]Is the Nvidia card a PCI card?
[*]Does you computer motherbard have integrated video? (an integrated VGA output)
[*]In case it does, Does your BIOS have the functionality to switch between both graphic cards?
[/LIST]
Regards.

---

