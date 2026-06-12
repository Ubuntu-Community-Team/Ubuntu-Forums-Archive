---
title: "Problems in Virtual Box"
date: 2008-04-30
forum: Virtualisation
---

### Post by seiya5 on 2008-04-30
well ive been meesing with VB now, and i cant get the mouse to work.
for some reason it wont get on. 

You have clicked the mouse inside the Virtual Machine display or pressed the host key. THis will cause the virtual machine to capture the host mouse pointer (only if the mouse pointer integration is not cureently supported by the OS) and the keyboard, which will make them unavailableto other applications running on your host machine. 

now im sure this is a common message, but why cant i get the mouse moving inside VB?*maybe tutorial out, or im just plain dumb. itried the host hey, but tha message just keeps popping*

Also could someone please direct me to a link where i can find how to get windows inside virtual box to use wifi or lan internet connection. 

Thank you

---

### Post by TenPlus1 on 2008-04-30
goto [www.softpedia.com](www.softpedia.com) and click on the LINUX button at the down... Scroll down and you'll see Linux running Windows in 1-click... That's a good VirtualBox tutorial that tells all :)

---

### Post by seiya5 on 2008-04-30
wow great site!!
thanks :D

i found somthing with VB
but it tells me that i need interenet on it, so i can file share lol
how do i get interent?

---

### Post by niteshifter on 2008-05-01
Hi,

> Also could someone please direct me to a link where i can find how to get windows inside virtual box to use wifi or lan internet connection.

There is, I think some confusion "out there" with this topic. If you set / accept the default in VBox of Adapter 0 set as NAT then however the Host OS has a connection is what the Guest OS uses. See attached screenshot.

I'm running VBox 1.5.6, PUEL license. Host OS is Gutsy. With VBox using NAT, XP's internet access works if Gutsy is connected via wired LAN, Wireless, or even if I'm using my cell phone as a modem (PPP connection). It just works.

This approach makes sense if all one wants to do is use "client" - type windows software (IE, Outlook, etc.) - just let the Host OS provide the Guest OS a network connection.

OTOH, if what one is after is to have "server" - type Windows (other than simple shares) that is, running NT Server, Server 2003 (IIS, Exchange, etc.) then the simple NAT approach is not what you want. There's a whole section in the VBox manual one needs to study.

With regards to sharing: It's easy to setup, the Devices menu of the Guest OS frame will allow you set permanent or transient (this session only) shares. I hate to (truly I do) sound like one of those crotchety curmudgeon types that spout RTFM - but do take the time read the manual on Virtualbox, you'll be glad you did (it's at /usr/share/doc/virtualbox/UserManual.pdf after you install VBox).

With respect to mouse capture, you need to install the Guest Additions. The manual tells in detail how :) The ISO will be at /usr/share/virtualbox/VBoxGuestAdditions.iso after installing VBox.

---

### Post by seiya5 on 2008-05-01
thanks niteshifter for the info. But seems like i didnt have to go through hell and back to fix it lol I just needed to install  go to Devices -> Install Guest Additions (in the VirtualBox window) and it got internet on its own and mouse worked fine after that. 

but yes the share file part will be tricky for me. 
Ill check the manuala, you dont sound like that lol

THanks for the advice :D

---

