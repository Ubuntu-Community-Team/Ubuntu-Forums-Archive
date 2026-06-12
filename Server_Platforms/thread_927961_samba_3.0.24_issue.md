---
title: "samba 3.0.24 issue?"
date: 2008-09-23
forum: Server Platforms
---

### Post by asbaeza on 2008-09-23
I have installed a samba (multipurpose as a matter of fact) server using 6.06 LTS ubuntu server release. All went ok till I upgraded (recently) to 7.04 Now I have a stange beheavour of the Windows network. When PCs are up, some of them can not see the other Windows machines, just the samba server. Some others can see everything, but, once entering the samba server and authenticate user for open some folder (not all folders are password protected), they lose network visibility. Other Winboxes are still available, but only looking for them using its IP. When samba server is restarted, visibility comes back, till someone gets into some folder in the samba server, and the cycle repeats. 

I made some changes and got it work fine, but just after undefine samba server as logon server. Is there any known issue about it? After all, the network is working well now, and logon server is not requiered since some time ago, but I do not understand the problem.

Any idea?

---

### Post by bab1 on 2008-09-24
This sure sounds like an authentication problem.  I would confirm how your users are authenticated in the system.  Do you handle it in a centrally located manner or via the smbpasswd system.  If you are using Windows AD or Winbind or some such, then I would make sure that the smb.conf file reflects that and that the other configuration files are correct.  If you are using the Samba users password file, I would make sure that all the users are in it.

---

