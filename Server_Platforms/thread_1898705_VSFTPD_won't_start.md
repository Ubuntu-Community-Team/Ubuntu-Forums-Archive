---
title: "VSFTPD won't start"
date: 2011-12-22
forum: Server Platforms
---

### Post by Dragon Smaug on 2011-12-22
Hi all,

I have installed vsftpd.  I have configured it with the settings modified shown below.  Whenever I try to "sudo /etc/init.d/vsftpd start" or restart, it appears to do so successfully, saying

 * Starting FTP server: vsftpd
   ...done.

However when i check what processes are running vsftpd is no one of them.  What could my issue be?

Thanks.

-Dragon Smaug

listen=YES
anonymous_enable=NO
chroot_list_enable=YES
userlist_deny = NO
userlist_enable = YES
userlist_file = /etc/vsftpd.allowed_users
ssl_enable = YES
allow_anon_ssl = NO
force_local_data_ssl=YES
force_local_logins_ssl = YES
ssl_tlsv1 = YES
ssl_sslv2 = YES
ssl_sslv3 = YES
listen_port=990
force_dot_files=YES
max_per_ip = 2
max_clients = 5

---

### Post by Lars Noodén on 2011-12-22
You might want to check to see if you already have [sshd](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sshd.8.html) running.

If so, then you already have SFTP available and can uninstall [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  It is the FTP protocol itself which is insecure.  In contrast, SFTP is very secure.

If you're looking for SFTP clients, Nautilus, Dolphin, Konqueror and FileZilla all support SFTP out of the box.

---

### Post by Dragon Smaug on 2011-12-22
sshd is running and I am aware that SFTP is more secure that FTP.

What I want, however, is to give other users FTP or SFTP access in a chrooted/jailed directory.   I know that VSFTPD can do this, if I can get it working.

Research shows me that theoretically sshd can do this as well.

HOWEVER, I am on Ubuntu 8.04, so my version of OpenSSH is 4.7.  You need OpenSSH 4.9 or 5 or so to use it to make a chrooted SFTP.

How can I:
-get vsftpd to work alongside sshd?
-upgrade to a newer version of OpenSSH?
or
-another solution to creating a chrooted SFTP with sshd?

I have searched for solutions to these issues on the net with no luck.

Thanks.

-DS

EDIT: option 2, upgrading version of OpenSSH is the most attractive to me, it seems the cleanest

---

### Post by Lars Noodén on 2011-12-23
> **Dragon Smaug said:**
> ...
-upgrade to a newer version of OpenSSH?
...


I've not made OpenSSH from scratch myself.

But based on experience with other packages, it might be safest to make it into a package for APT before installing it.  That way APT can track versions or it can be uninstalled cleanly.  Since there is already a source package for OpenSSH in the repository for Ubuntu 8.04, that could be used as the base and the new code swapped in.  

Note there is a 'portable' version of OpenSSH for non-OpenBSD distros like Ubuntu.

Edit: tip: [http://www.unixwiz.net/techtips/openssh.html](http://www.unixwiz.net/techtips/openssh.html)

---

