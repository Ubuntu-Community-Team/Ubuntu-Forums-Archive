---
title: "Ubuntu 10.04, Samba 3.63 &amp; LDAP errors in logs"
date: 2012-04-19
forum: Server Platforms
---

### Post by dinsdalepirhana on 2012-04-19
Hi  I have recently upgraded our 9.04 Ubuntu server running Samba 3.4.2 & LDAP 2.4.21 backend to Ubuntu 10.04 & Samba 3.6.3.  

Since the upgrade, I have the following errors in our logs every time  a Windows 7 client logs in: 
**2012/04/19 11:41:33,  0] rpc_server/srv_netlog_nt.c:603(_netr_ServerAuthenticate3)   _netr_ServerAuthenticate3: netlogon_creds_server_check failed. Rejecting auth request from client PCNAME machine account PCNAME$**

The user is able to login fine and everything appears to be working. However I would like to resolve this message as it looks terrible in the logs.   Applied all windows 7 reg fixes, have disabled password change requirement on the win7 pcs.  I would appreciate any help I can get I have googled this for a couple of weeks now and cannot find a resolution. 

 Thank you 
Candy M

---

