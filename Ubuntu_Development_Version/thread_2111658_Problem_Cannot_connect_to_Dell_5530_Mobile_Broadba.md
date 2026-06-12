---
title: "Problem: Cannot connect to Dell 5530 Mobile Broadband (AT&amp;T)"
date: 2013-02-02
forum: Ubuntu Development Version
---

### Post by baddison1 on 2013-02-02
Hello, I just performed a clean install of 13.04 and I am unable to connect using my internal Dell 5530 Mobile Broadband card. I am quite new to Ubuntu, but with the help of this community, I am learning every day. :p
 
Network Manager recognizes the connection, and takes me thru the setup. I am using the AT&T Laptopconnect (Data cards) settings. The apn is correct: "broadband" and the number to dial is also correct. However, when I attempt to make a connection, it tries and then returns "Network Disconnected - You are now offline"
 
Has anyone successfully used their onboard mobile broadband card with UBUNTU 13.04? Can you tell me where I need to go to configure the card's commands? Or perhaps can I get a "sniffer" on this to see exactly where the failure is occurring? 
 
Any help, advice, ideas, and suggestions are welcome. And thank you all in advance!:D

---

### Post by grahammechanical on 2013-02-02
The design of Network Manager has changed slightly between 12.04 and 13.04 to make it easier for new users to set up a network connection. But the method that network manager uses to make that connection is still the same as it has been for more than two years.

Is this an issue with 13.04? Do you know if this hardware works in 12.04? Are you sure that the encryption method is correct? Is the wireless key or passphrase correct.

First try the normal trouble shooting tests before putting the problem down to a bug in 13.04

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Regards.

---

### Post by baddison1 on 2013-02-02
> **grahammechanical said:**
> The design of Network Manager has changed slightly between 12.04 and 13.04 to make it easier for new users to set up a network connection. But the method that network manager uses to make that connection is still the same as it has been for more than two years.

Is this an issue with 13.04? Do you know if this hardware works in 12.04? Are you sure that the encryption method is correct? Is the wireless key or passphrase correct.

First try the normal trouble shooting tests before putting the problem down to a bug in 13.04

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Regards.

I performed all the normal troubleshooting tests, and all the outputs show an active module with the proper drivers installed. Ubuntu recognized the card as well.

How can I verify the "encryption method".  And with the AT&T broadband APN, there is no username and no password required

This card did the same exact thing for me in 12.04...Network Manager sees the card, the drivers are all there, but I cannot connect. I found this article ([http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page) ) that shows my specific device is supposed to be supported, but that Kernel number is very old (2.6.31)

Can you tell me what I can run to see the modem's output as it tries to connect?? Perhaps I can find out why the connection is not successful.

I am such a newbie at this....but I am learning fast!! I need desperately to get this mobile broadband card up and running.  Perhaps I need to create my own script, or perhaps I need to use something other than the standard Network Manager to correctly make the PPP connections??   #confusedtodeath

---

### Post by baddison1 on 2013-02-03
How do I set up a launchpad troubleshooting incident?

---

### Post by mörgæs on 2013-02-04
For those following here's the new bug report:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1114575](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1114575)

and some older ones:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/540003](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/540003)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/299274](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/299274)

---

### Post by baddison1 on 2013-02-07
Totally solved!!! Up and running...needed to physically connect the antennae to the modem on the hardware itself. Go figure!!
 
 


[https://bugzilla.gnome.org/show_bug.cgi?id=693309](https://bugzilla.gnome.org/show_bug.cgi?id=693309)

---

