---
title: "samba as a pdc"
date: 2010-12-19
forum: Server Platforms
---

### Post by edthetoad on 2010-12-19
I am attempting to use Samba as a pdc for my house but whenever I try to join the domain with my windows 7 computer it tells me that it cannot find the domain.  I have the computers on the same wireless network.  Also I have connected them with a small ethernet switch.  The computers are able to ping eachother but I cannot get onto the domain.  I have tried multiple versions of samba but I have no clue how to use the smb.conf for samba4.  What should I do?

---

### Post by windependence on 2010-12-19
This is most likely a Windoze 7 problem, NOT SAMBA. 
 
 
 
 
Control Panel - Administrative Tools - Local Security Policy 

Local Policies - Security Options 


Network security: LAN Manager authentication level 
Send LM & NTLM responses 

Minimum session security for NTLM SSP 
Disable Require 128-bit encryption 

See if that works.
 
-Tim

---

### Post by windependence on 2010-12-19
Also, [http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)
 
-Tim

---

