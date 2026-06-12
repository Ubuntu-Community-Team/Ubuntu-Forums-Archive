---
title: "Need help on PXE boot and bare metal provisioning."
date: 2013-08-14
forum: The Cafe
---

### Post by thanh2 on 2013-08-14
Hello folks,
This is the scenario: You are the admin of a network which has a central server and client PCs. The clients have no operating systems installed. The server contains all OS images that the clients need.

[LIST]
[*]A client will load one of the OS images from the server via network to use. After the client shutdowns, the OS on the client is gone too, no installation needed. **(1)**
[*]The admin sits on the server to control the clients. For example:
[LIST]
[*]the server can choose what OS the client will boot into    **(2)**
[*]the server can make the client reboot to another OS       **(3)**
[*]the server can make the client wake up from its sleep     **(4)**
[/LIST]
[/LIST]

Here is what I have done so far:

Problem #1: This can be done by PXE boot which consists of DHCP, TFTP, NFS servers. Check out this link for the details [https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro) 

Problem #4: This can be done by “wake on lan” using the “magic packet”. Google it for details.

Problem #2, #3: These are the most important problems. I have tried Cobbler recently but I found out that Cobbler always make the client install the selected OS which is not our objective. I need some kind of tool that can help me solve all these problems harmoniously.

 
This is one part of my thesis and I really need help after a long time struggling. I hope there are specialists and experts around in this forum for I’m very confused now.
Best regards,
Thanh.

---

### Post by Sef on 2013-08-16
Homework, so locked.

---

