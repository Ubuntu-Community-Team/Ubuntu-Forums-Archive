---
title: "Blank Screen During Ubuntu Server Installation"
date: 2012-01-22
forum: Server Platforms
---

### Post by DrFoliberg on 2012-01-22
Hi,
I'm quite new to ubuntu and completly new to ubuntu server.
I downloaded ubuntu server 10.10 amd64 and burned it to a DVD. The problem now, is during the installation, right after the step that is (or while) detecting the networks, a blank purple screen with a grey bar at the bottom which I can type in, but it's not responsive stay and the next confguration screen does not appear: exactly like this thread [http://ubuntuforums.org/showthread.php?t=1913374](http://ubuntuforums.org/showthread.php?t=1913374) ,execpt it's the normal server edition, I don't even configure the network and rebooting does not help.
I am running an AMD 145, 8go of ram, integrated graphics, integrated NIC. Checked disk integrety and RAM is not faulty.
Sorry for my english mistakes (if there are any), I don't speak english as a primary language. 
Thank you.
EDIT: I forgot to add that if I disconnect the network cable and reboot, installation asks me if I want to continue and forget about network settings and I can complete the install, but I have no network connectivity...

---

### Post by SeijiSensei on 2012-01-23
What network adapter is it?  From the symptoms it sounds like the installaer doesn't have a driver for your network adapter.  

Do you have a spare PCI or USB network adapter lying around?  If so, try putting that into the server.

---

### Post by DrFoliberg on 2012-01-23
It is the integrated NIC from the msi 880gm-e41 motherboard.
I have a dge-530t from dlink in another computer, but I am almost certain it is not the NIC as debian doesn't have this problem.

---

