---
title: "XDMCP setup"
date: 2009-02-22
forum: Server Platforms
---

### Post by Dowdy90 on 2009-02-22
hi i am trying to set up a XDMCP so worstation can access a server. As it stands my workstation can not see server.

On the server i have set a static ip. The workstation can access the server using telnet so the server is hosting on the network.

How do i configure the XDMCP so my workstation can see the server

---

### Post by RealPSL on 2009-02-22
Since you are trying to connect with XDMCP we will assume that you have a GUI installed on your server. Assuming that GUI is GNome you can select System -> Administration -> Login Window. On the Remote tab choose either Same as Local/Plain with face browser. In the lower right hand corner choose XDMCP to change any additional settings you like. Click Close twice to complete the task.

With that said you are significantly more secure using SSH so assess your needs carefully before using XDMCP.

---

