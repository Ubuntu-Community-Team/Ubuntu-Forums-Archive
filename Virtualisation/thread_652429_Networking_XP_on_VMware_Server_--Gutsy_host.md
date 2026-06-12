---
title: "Networking XP on VMware Server --Gutsy host"
date: 2007-12-28
forum: Virtualisation
---

### Post by theZoid on 2007-12-28
I have XP Pro running in a Virtual Machine on Ubuntu 7.10.  The XP virtual machine can access the internet fine, but how can I access my home network and my Vista partition (same physical drive).  Accessing my network resources is more important....printing, ext HD, etc.

thanks much!  this is driving me crazy :D

---

### Post by fjgaude on 2007-12-30
You have to setup shares, Administration/Shared Folders in Gnome. From there when in Windows you go to Network using Windows Explorer or whatever program that has access to networks.

All this is done because of SAMBA capabilities in Ubuntu. Make sure in Services you have everything clicked to be active.

---

### Post by theZoid on 2007-12-30
I follow you, but in the XP Pro VM I can't see the network...I think it's on a different IP range...it's on the net set as NAT sharing the same IP?

---

### Post by fjgaude on 2007-12-30
While in the Windows VM, open Explorer, the file browser. Scroll down to near its bottom and see "Networks" or something like that. Click on it. From there click on Entire Network, then Microsoft Windows Network. Then you should see WORKGROUP, the group you setup in your Ubuntu Shares.

---

### Post by theZoid on 2007-12-30
Ok...thanks...let me try this again...

---

### Post by gruss on 2007-12-30
You could also change the networking to "bridged" in VMWare and let XP grab its own IP address, then you can treat it network wise just like another box.

---

### Post by theZoid on 2007-12-30
> **gruss said:**
> You could also change the networking to "bridged" in VMWare and let XP grab its own IP address, then you can treat it network wise just like another box.

Yes! that's what I was trying to do....but, it kicks me off the internet running as bridged...what am I doing wrong?

---

### Post by gruss on 2007-12-30
What kind of network are you trying to connect to?  I"m not sure if there is a difference between vmware on windows or linux settings wise, but I've been running ubunut inside VMWare with no issues switching between the two.  What it could be is you XP load doesnt have the appropriate "driver"?  If you open up device manager in XP does it show everything working correctly?  Is the network you're on running DHCP, if so go into the network connections and make sure all the settings on the connection your using are set to DHCP and AUTO and get rid of any residual DNS settings that may be haning around.

---

### Post by theZoid on 2007-12-30
thanks gruss....I'm going to check all that out

---

