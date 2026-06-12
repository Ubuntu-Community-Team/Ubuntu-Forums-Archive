---
title: "Clamav-freshclam asking for password"
date: 2007-11-19
forum: Server Platforms
---

### Post by mbuti on 2007-11-19
I'm trying to install clamav on a virtual machine (running on vmware fusion) with ubuntu server 7.10, but it hangs forever here:

Setting up clamav-freshclam (0.91.2-3ubuntu2) ...
 * Starting ClamAV virus database updater freshclam
Password: 
su: Authentication information cannot be recovered

I installed with no problems on a real machine with same configuration, but I don't think it's a problem of the virtual machine, what could that be?
Thanks a lot

---

### Post by mbuti on 2007-11-20
I actually found out that it's a problem about my ldap backend or pam configuration (I made some mess on this machine).

For example even running fetchail for every uses with the webmin module gives this
Password: su: Authentication information cannot be recovered

But ssh and smb account are working fine...

I don't know which logs or commands could help me :(

---

