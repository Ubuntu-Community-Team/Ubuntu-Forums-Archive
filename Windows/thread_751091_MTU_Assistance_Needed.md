---
title: "MTU Assistance Needed"
date: 2008-04-10
forum: Windows
---

### Post by Vince4Amy on 2008-04-10
Would this configuration be possible, sorry for the paint diagram, Network Notepad doesn't work on Vista 
[IMG]http://img246.imageshack.us/img246/2100/diagramyo4.jpg[/IMG]
As you can see from this diagram the Dynamode ADSL Router is going into the Main computer which is running Windows Vista Home Premium x64. I changed the MTU settings on this computer to 1492 and I can access any websites.The second ethernet connection is going from the Dynamode ADSL router to an ME 102 Access point, which is sending the Internet connection through wireless to another ME 102 which is an access point client
Now obviously I have to change the secondary computer MTU settings to 1492 and this machine runs Windows XP Home Edition sp2 so I can do this through DRTcp. There are two network cards in this machine and Windows XP has been configured to share the Internet connection from NIC 1 (Connected to the ME102) to NIC 2 (Which connects to customers computers when I repair them so I can check the Internet access and do updates.
My question is that now I accept the only way to do this with Orange is to change the MTU settings on every machine but is there any way I can set up a method on the secondary machine so I don't have to change the MTU settings on the customers machines as this could cause problems when they take them home?

---

