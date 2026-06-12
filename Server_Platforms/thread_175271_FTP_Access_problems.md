---
title: "FTP Access problems"
date: 2006-05-13
forum: Server Platforms
---

### Post by jazee on 2006-05-13
I am just wanting to know if any of you guys have been having problems with the D-Link DGL-4300 router with servers behind it. I just got it today and for some reson my ftp server acts up when connecting to the server from a diffrent machine even local to the network. The apache server seems to be going just fine as well as the VNC, SSH, & webmin.

The problem is that when I try and connect to the server via external or internal IP the connection seems slow. It takes forever just to connect and give a log-in then it takes even longer just to do a simple ls on the PWD. 

Any ideas on how to fix this problem. Thanks

---

### Post by Socratez on 2006-05-13
Stupid I know but check to be sure your server is not using PASSV and if it is then make the appropreate adjustments ... I could be way out in left field but I had a similar problem with my old server behind any sort of Gateway/Router Device D-Link or otherwise ... 


Soc

---

