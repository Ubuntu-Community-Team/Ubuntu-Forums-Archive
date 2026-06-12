---
title: "Premissions in Ubuntu Server 11.10"
date: 2011-12-03
forum: Server Platforms
---

### Post by Booyaches on 2011-12-03
Hello! I am absolutely new to Ubuntu. 
Couple of days ago I set up a server on Ubuntu 11.10. I set up all the services (apache, MySQL, SSH, FTP) and everything works fine apart from the FTP. I can`t manipulate files from directories other than /home/MyUserName. 
I have just one user account one my system, the same that was created during the installation. I can copy, move and erase files from all the directories when I use SSH command terminal but when I use the same user to log in to FTP i can`t. How to change permissions for my user to be able to access and manipulate all the directories. I use ProFTPd.

---

### Post by Lars Noodén on 2011-12-03
I'd recommend [ditching FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and using SFTP instead.  It's already part of SSH, so it is already there and running.

As far as permissions go, you have to have write access to the directories in order to write.  Which ones are you thinking of in particular and will you be the only one with access?

---

### Post by Booyaches on 2011-12-03
> **Lars Noodén said:**
> I'd recommend [ditching FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and using SFTP instead.  It's already part of SSH, so it is already there and running.

As far as permissions go, you have to have write access to the directories in order to write.  Which ones are you thinking of in particular and will you be the only one with access?

Yes, I was also trying to access my files using SFTP but I get "permission denied" message when I try to delete something. 

On the begging I`d like to have write access to /var/www. Yes, for now, I will be the only user of this system.

---

### Post by Lars Noodén on 2011-12-03
The quick and dirty way to give just yourself access is to change ownership of /var/www.

```

sudo chown -R booyaches /var/www

```

If you plan to share access with others,  then you'll have to set group permissions instead.

---

### Post by Booyaches on 2011-12-03
Ok ,that worked right away! Thanks for help :-)

---

