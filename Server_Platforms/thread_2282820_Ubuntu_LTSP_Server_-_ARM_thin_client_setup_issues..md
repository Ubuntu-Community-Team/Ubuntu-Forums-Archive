---
title: "Ubuntu LTSP Server - ARM thin client setup issues."
date: 2015-06-17
forum: Server Platforms
---

### Post by krish2487 on 2015-06-17
Hello, Let me give a brief introduction before I get to the actual problem.
We are a ubuntu shop with the exception of our SAP ERP server which runs on windows 2012 R2 and Terminal Server running windows server 2008 R2.
All in all about 40 clients.

We are very happy with the setup. However, in an effort to go green with power consumption we are trying to migrate to a thin client setup. 
We wanted to scrap out existing PCs and get proper thin clients that can be fit to the monitors. 

I have successfully setup a test LTSP server (ubuntu 14.04) and client using virtualbox on my laptop. It boots and I am able to login to the server from the client.
The network is setup correctly on VirtualBox (bridged mode) and no DHCP server issues etc. So far so good.

We are trying to evaluate a thin client from QHMPL - Model QHM6056 for booting into the LTSP server.
This is where I hit a brick wall. The thin client runs windows embedded and I cant get it to PXE boot. I am not that good with windows, having given up on windows a decade back.
The thin client itself is a generic rebranded ARM thinclient based on CLG7700.

Has anyone else faced a similar situation? I will be extremely grateful to anyone who can help me with this.

What I am looking for is help with either 
1. network booting a thin client
2. Setup the thin client to access a ltsp server post booting into the embedded windows.

Thanks in advance.

---

