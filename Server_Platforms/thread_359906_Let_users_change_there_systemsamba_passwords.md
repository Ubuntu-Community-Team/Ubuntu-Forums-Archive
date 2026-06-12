---
title: "Let users change there system/samba passwords?"
date: 2007-02-12
forum: Server Platforms
---

### Post by random_mike on 2007-02-12
Hi

I have a ubuntu-server 6.10 with samba and rsync via ssh running. I've chrooted the ssh login for users who use rsync, so they can't login just rsync. I've installed webmin and it's up and running. 

What I would like to do next is to let users have the ability to change there passwords. Both system and samba. Is there a good way/program to do this?

Thanks

---

### Post by random_mike on 2007-02-13
Update.

I updated webmin. I found a module in webmin "usermin" witch let's users log in and change stuff. In webmin you can configure usermin. In usermin my users can change there system password, but not there own sambapassword. 
I tryed to add a custom command in webmin that users can run in usermin.

echo -n -e "$oldpass\n$newpass\n$newpass2" | smbpasswd -s

smbpasswd "-s" This  option  causes  smbpasswd  to  be  silent  (i.e. not issue prompts) and to read its old and new passwords from standard in&#8208;put,  rather  than  from  /dev/tty...
$oldpass $newpass etc are inparameters that you can specify in webmin when you build your custom command.

And this gives me this output.
machine x.x.x.x rejected the password change: Error was : Password restriction.
Failed to change password for JonDoe

Skipped the above, users can change there system password now.
I set the samba password to sync system password in /etc/samba/smb.conf so when users change there system password in usermin samba password will be set to the same.

smb.conf
  unix password sync = yes

---

