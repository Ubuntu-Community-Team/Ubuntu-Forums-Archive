---
title: "User account"
date: 2006-06-08
forum: Server Platforms
---

### Post by Dylan103 on 2006-06-08
I just recently installed Ubuntu Dapper.
And I made a new user account, and deleted the default OEM account.
But now in the System -> Administration, I don't see all the things, like Users and Groups.
I also cant do anything in terminal like
sudo nautilus /var/www to access it with admin privilages.
Any help to regain this stuff?

---

### Post by nanotube on 2006-06-08
[QUOTE=Dylan103]I just recently installed Ubuntu Dapper.
And I made a new user account, and deleted the default OEM account.
But now in the System -> Administration, I don't see all the things, like Users and Groups.
I also cant do anything in terminal like
sudo nautilus /var/www to access it with admin privilages.
Any help to regain this stuff?[/QUOTE]
you need to add your new user to the group "admin", and group "adm"

to do this, reboot in recovery mode, you will get a root terminal
then edit the file /etc/group (command "nano /etc/group") and add your new user to the admin group, and adm group. 

also, if your new user is not in these groups, add him:
dialout, cdrom, floppy, audio, dip, video, plugdev, lpadmin, scanner
that will make sure all that other stuff works.

have fun.

why did you delete the stock user, anyway? :)

---

