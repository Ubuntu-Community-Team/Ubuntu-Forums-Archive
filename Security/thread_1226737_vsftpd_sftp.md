---
title: "vsftpd sftp"
date: 2009-07-29
forum: Security
---

### Post by inphektion on 2009-07-29
I use vsftpd in 2 of my production ftp servers and then in all our dev ones as well.  I have it setup with virtual users each chroot'd into their own folder with our corp account chroot'd up one level to be able to access all their folders.  
I want to enable sftp logins now.  I don't want to force every user to have to use sftp.  Can I somehow enable this on a per user basis (ie some ARE forced)? Or can I only make it optional whereas they can use sftp or ftp to their chosing.  

I can't force them to use sftp only right now or that would cut too many off.

---

### Post by cdenley on 2009-07-30
Do you mean sftp (SSH) or do you mean ftps (FTP over SSL)? You can allow FTP connections with or without SSL (encryption optional), but I don't think you can require encryption on a per-user basis. You wouldn't know what user is connecting until the encryption was already negotiated.

---

### Post by inphektion on 2009-07-30
yes i meant ftp over ssl.  good point about the per-user....

---

### Post by Lars Noodén on 2009-10-06
> **inphektion said:**
> yes i meant ftp over ssl. .

FTPS means FTP over SSL.

SFTP is something different and IMHO more appropriate. 

Why not leave the FTP as it is.  Then for those that need SFTP (as opposed to FTPS) you can set up OpenSSH server (which you have already presumably) to force a group of users into the sftp-subsystem.  The keyword for the sshd configuration would be 'ForceCommand'

---

