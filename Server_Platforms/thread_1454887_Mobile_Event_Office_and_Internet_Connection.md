---
title: "Mobile Event Office and Internet Connection"
date: 2010-04-15
forum: Server Platforms
---

### Post by spynappels on 2010-04-15
I have been asked to look at a few options for a mobile event ofice with a small LAN, shared storage, shared printers etc. I can do all that no problem using an Ubuntu server, but they have also asked is it possible to use a USB modem to give Internet access to specific users through the server.

So my question is is it possible to plug a USB modem into a spare USB port on the server, have it connect and then share this connection with other users on the network?

I would intend using the server as DHCP server, File and Print Share through Samba, maybe an IM server and then possibly as an Internet gateway.

Any how-tos on the Internet connection sharing bit?

---

### Post by volkswagner on 2010-04-15
This may have some useful info.

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

It is for setting up wireless router, but you should be able to substitute the wireless info to your wired card.

As long as your USB Modem is supported in Linux you should have lots of joy.

What is the modem model?  Is it cellular?

---

### Post by spynappels on 2010-04-16
Thanks for that, I should have said that the USB modem is actualy a 3G Wireless Broadband dongle. I presume this will make no difference though, as long as the specific dongle is Linux supported?

---

