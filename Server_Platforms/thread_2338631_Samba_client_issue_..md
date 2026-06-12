---
title: "Samba client issue ."
date: 2016-09-30
forum: Server Platforms
---

### Post by gardenair on 2016-09-30
Hi,
      I am using samba in my Ubuntu box. I am facing problem in the client side .The issue is when i map the drive I save the samba  user name and its password in the windows diallog box.It take 5 minutes at least after saving the user credentials. Like it sleep.........[-(
It then open the share folder and work fine.I can see the map drive  in "My Computer".

The issue is when i restart the windows 7 PC it it show at the botton side of the taskbar  "Windows not connected the network drives" .In " My Computer" i see a red cross in the map drive. I double click on it and it take 2 to 3  minutes   "busy sign in windows" then it show me again windows dialog box to enter  samba user name and password .I give the user name and password  it again take 2 to 3 minutes then i can see the map drive.

Every time i do the same practice which consume lot of my time. In samba when i give the command it show me the user "Hall" with 3 different sessions.
How can I kill the user "Hall" sessions in samba ? Is it due to this problem ? 

Kindly see the attachment.

---

### Post by TheFu on 2016-09-30
Make the network settings (/etc/hosts files) on all systems know about the other systems so they can ping each other.  Basically, make all the systems have a static IP.

OR ....

you could setup avahi and try to access each of the systems using hostname.local nomenclature. I haven't used avahi and generally purge it from installs due to early issues. Those are almost certainly solved by now.

OR ... use DNS to have both systems able to "find" each other on the network.

BTW, copy/paste of text is much preferred over posting an image. Helps people using low bandwidth connections.

---

### Post by SeijiSensei on 2016-10-01
I have never been able to get Windows 7 to remember my credentials when connecting to my Samba server.  This seems to be a limitation in Windows.

---

### Post by Vegan on 2016-10-03
> **SeijiSensei said:**
> I have never been able to get Windows 7 to remember my credentials when connecting to my Samba server.  This seems to be a limitation in Windows.

windows 10 seems to work better that way

---

