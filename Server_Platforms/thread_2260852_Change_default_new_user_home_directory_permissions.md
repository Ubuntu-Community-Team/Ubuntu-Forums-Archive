---
title: "Change default new user home directory permissions"
date: 2015-01-14
forum: Server Platforms
---

### Post by Marc-NJ on 2015-01-14
I've been using Ubuntu server for a while now (on 12.04), but still have some large gaps in my knowledge.  I also use Webmin for a lot of stuff since having a GUI is always easier than command line (at least for me), but also use command line when necessary.  

It's my understanding that whenever a new user is created, their /home/<username> directory is pretty much left open for the world to view.  I did read that there are chmod and chown changes you can make to each of these /home/<username> directories and sub-dirs to change this, but is there any way to just change the default so that each new user's home directory isn't accessible by anyone except them and potentially admin's?  

Thanks so much!

---

### Post by sisco311 on 2015-01-14
Never used Webmin but according to  [http://doxfer.webmin.com/Webmin/UsersAndGroups](http://doxfer.webmin.com/Webmin/UsersAndGroups) you can change the default permissions under *System -> Module Config -> Permissions on new home directories.*

If you use the adduser  command, then you have to edit the DIR_MODE option in /etc/adduser.conf

---

### Post by SeijiSensei on 2015-01-14
You can change the default directory mode for new users created with the adduser command by changing the DIR_MODE parameter in /etc/adduser.conf.  The Ubuntu default is 0755, which grants read and list privileges to all users.  To limit read and list access to the user and members of the user's group use 0750.  To allow only the user herself, use 0700.  

I don't know if webmin invokes adduser, but I'm going to guess that it does.  Otherwise just create new users with "sudo adduser username" and follow the prompts.

---

