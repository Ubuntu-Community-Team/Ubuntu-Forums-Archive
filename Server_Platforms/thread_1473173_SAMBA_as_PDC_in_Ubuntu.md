---
title: "SAMBA as PDC in Ubuntu"
date: 2010-05-04
forum: Server Platforms
---

### Post by wrp on 2010-05-04
I am unable to join a W2K or XP machine to a Samba PDC. I have tried to make this work on both 8.04 LTS and 10.04 LTS without success. Everything else works but I cannot add machine accounts "on the fly" using the "add machine script" as provided in the server guide. 

I have been able to make it work by enabling the root user but not as a user with admin privileges and sudo in the script. Despite multiple attempts including a new 10.04 install and following the instructions (in the 9.10 server guide) to the letter.

There are a number of posts on this and other forums relating to this problem with NONE actually acknowledging a successful resolution! 

Does anyone out there have a samba PDC actually running on Ubuntu and able to add machines on the fly without enabling the root account (i.e using SUDO in the script and a user from the admin group) ??

If so I will post details of my most recent setup and plead for help.

---

### Post by wrp on 2010-05-08
Problem solved. The problem is that rights need to be explicitly provided to the domain admins group to allow the add machine script (and other admin functions) to work. 

This is achieved by running
net rpc rights grant "YOURDOMAIN\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege

I can now add a machine to the domain. 

Also don't forget that in 10.04 you restart Samba by running 
sudo restart smbd

and if necessary
sudo restart nmbd

NOT sudo /etc/init.d/samba restart

---

