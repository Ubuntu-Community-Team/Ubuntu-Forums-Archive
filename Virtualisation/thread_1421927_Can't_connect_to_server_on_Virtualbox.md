---
title: "Can't connect to server on Virtualbox"
date: 2010-03-04
forum: Virtualisation
---

### Post by Imoen on 2010-03-04
I have Windows 7 with VirtualBox installed to run Ubuntu 9.10 inside of Windows so if I need to edit a file on a site I manage I don't have to change computers. On my laptop running Ubuntu straight, I can go to places, connect to server (ftp with login) and connect to my site host, where I can open the files on it, edit them, and save them etc.

When I try to do this on Ubuntu in the virtualbox it can't seem to connect, although I can connect to the internet without problems. I found [this]("http://www.virtualbox.org/wiki/Network_tips") but the directions saying "do the following" don't tell me anything that I understand because I tried to run those things in terminal and it tells me to install virtualbox and in Windows it tells me bad command. CAN someone help me out with this?

---

### Post by isaacobezo on 2010-03-04
are you running the free version of virtual box, or the non-free one. From experience I know that the non-free version has some of the network services off.

---

### Post by Imoen on 2010-03-04
the free one

---

### Post by kiranmurari on 2010-03-05
Hi,

Please check the network settings of the Ubuntu VM. If it is configured in NAT mode (which is the default mode), then you will not be able to access your windows 7 host from your VM nor will you be able to access your VM from outside. If that is the case, you can add another virtual network adapter to the VM and configure the network mode as "Host-only Adapter", so that it would get an IP address in the series of "192.168.56.xxx". Similarly, host will also acquire a virtual NIC and IP address 192.168.56.1. Now you would be able to communicate between the VM and the host using the 192.168.56.x network.
   
You can also try using the "Shared Folders" feature for Host-Guest interaction.
Please take a look at the following threads on sharing folders between host and guest.
[http://ubuntuforums.org/showthread.php?t=1407139](http://ubuntuforums.org/showthread.php?t=1407139)
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

Hope this helps.

---

### Post by cptncatholic on 2010-04-01
Imoen:

If I'm understanding you correctly, I just experienced the same problem, only I'm running Dreamweaver MX 2004 on a WinXP virtual machine in VirtualBox on an Ubuntu 9.10 host...

I just tried updating a website using Dreamweaver and couldn't FTP up to the remote server. I could connect to the server, but it wouldn't list the directory contents or let me upload. But I could connect and upload from the Ubuntu host.

I checked the network adapter settings in VirtualBox for the WinXP VM and like kiranmurari said, it was set to NAT by default. I changed it to 'Bridged', fired up the VM and was able to connect and update files like normal.

Hope that helps!
tc

---

