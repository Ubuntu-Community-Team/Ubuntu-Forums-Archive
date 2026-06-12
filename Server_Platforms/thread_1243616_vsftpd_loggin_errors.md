---
title: "vsftpd loggin errors"
date: 2009-08-18
forum: Server Platforms
---

### Post by brown_ghost on 2009-08-18
I've been trying to setup vsftpd for a couple of weeks on and off and I still can't get it to work. 
I have a simple set up: vsftpd and samba, I have 2 cards plugged in one has static ip for clients to log in using TLS/SSL/FTPS and one is dhcp connected to my network (window xp boxes) can get to shared folder /srv/ftp and drop files that clients can get their files from. 
If I use ftpcommander to try to log in I get error "500 OPPS: vsftpd:both local and anonymous access disabled!", I'm able to log in using Winscp & Filezilla but can't seem to jail users to their home folder /srv/ftp, with any user I'm able to get out of home and can see and download any file anywhere within server (big security risk) but can't upload into any folder except home. What am I'm doing worg?
Here what I have enabled in /etc/vsftpd.conf
chroot_local_user=YES 
chroot_list_enable=NO 
anon_upload_enable=NO

---

### Post by hessiess on 2009-08-18
> **brown_ghost said:**
> I've been trying to setup vsftpd for a couple of weeks on and off and I still can't get it to work. 
I have a simple set up: vsftpd and samba, I have 2 cards plugged in one has static ip for clients to log in using TLS/SSL/FTPS and one is dhcp connected to my network (window xp boxes) can get to shared folder /srv/ftp and drop files that clients can get their files from. 
If I use ftpcommander to try to log in I get error "500 OPPS: vsftpd:both local and anonymous access disabled!", I'm able to log in using Winscp & Filezilla but can't seem to jail users to their home folder /srv/ftp, with any user I'm able to get out of home and can see and download any file anywhere within server (big security risk) but can't upload into any folder except home. What am I'm doing worg?
Here what I have enabled in /etc/vsftpd.conf
chroot_local_user=YES 
chroot_list_enable=NO 
anon_upload_enable=NO

Try using SFTP, The FTP protocol is a mess and dousen't work well with firewalls, FTPS is an even bigger mess.

---

