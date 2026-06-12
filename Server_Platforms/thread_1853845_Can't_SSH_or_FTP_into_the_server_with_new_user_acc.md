---
title: "Can't SSH or FTP into the server with new user accounts!"
date: 2011-10-03
forum: Server Platforms
---

### Post by EApubudu on 2011-10-03
I have a mediatemple web server configured with Nginx.... At first, i created one user account and used that user to log into to the server through SSH... it worked perfectly and still i can use that user account to login to the server...

But, when i create a new user account now, that account can't connect to the server! When i try to connect with SSH, after i give the user name and password... the connection gets closed automatically!

When i try to FTP into the site through Filezill (using that user account)... it says :

Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing

Can you please tell me how to fix this problem? Its very urgent!

---

### Post by cj13579 on 2011-10-03
I would check to make sure that these new users are in the SSH and FTP groups. Check in /etc/groups

---

### Post by Lars Noodén on 2011-10-03
First, I'd uninstall FTP.  You already have [SFTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) since you have SSH.

Second, I'd look in [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) and see if somehow AllowUsers, AllowGroups, DenyGroups, or DenyUsers was set.  If you can log in from the console, you should be able to log in via SSH or SFTP.

---

### Post by [S|G] on 2011-10-03
Hi!

It doesn't seem to be a problem on your user configuration. As you mentioned the error message is "connection timeout", which is connectivity-related. You're probably hitting a firewall along the way and it is not allowing you to connect to ports 21 and 22.

You can check that by trying to telnet to those ports:

ssh yourhost 21   # <-- for FTP
ssh yourhost 22   # <-- for SSH

EDIT: Just saw that the timeout happened AFTER you connected and tried to list the directory's contents. You might need to activate passive connection for FTP or check your communication to port 20 if you're using active connection (in this case the client's port 20 must be reachable).

---

