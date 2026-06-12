---
title: "How to get root access when sftp'ing to Ubuntu Server"
date: 2008-07-10
forum: Server Platforms
---

### Post by antilog on 2008-07-10
I am trying to move files to an Ubuntu Server using SFTP and my only user account on the server.  It always fails, and I don't feel like 777'ing everything, so I am wondering how to get sudo / root access when SFTP'ing.  I am using Filezilla.

Any ideas?

---

### Post by Fire_Chief on 2008-07-10
Is there a particular reason you are using SFTP? You may want to try with a simpler option like SCP.

---

### Post by Traumadog on 2008-07-10
> **antilog said:**
> I am trying to move files to an Ubuntu Server using SFTP and my only user account on the server.  It always fails, and I don't feel like 777'ing everything, so I am wondering how to get sudo / root access when SFTP'ing.  I am using Filezilla.

Any ideas?

Are you trying to copy files into folders that are owned by "root" and have "root" as the only group member?  If so, that may be why the copy procedure fails.  

I don't think "Filezilla" has a method to use "sudo" when transferring files.  However, one solution might be to become a group member of the directories that you want to copy files to and then make sure the group has write access to those directories.

Others, of course, may have better ideas.

Hope this helps! :)

Traumadog.

---

### Post by antilog on 2008-07-10
I am using SFTP because that's what Filezilla uses when using port 22, and I have openssh server running.  

I could chmod, but I was trying to get away from that.  I really wish Ubuntu didn't "block" the root account....

Thanks

---

### Post by cdenley on 2008-07-10
> **antilog said:**
> 
I really wish Ubuntu didn't "block" the root account....


It's very easy to enable root. If you don't know how, then you probably don't understand why it is a bad idea. It is against the forum rules for me to post the command to do this.

---

### Post by antilog on 2008-07-10
> **cdenley said:**
> It's very easy to enable root. If you don't know how, then you probably don't understand why it is a bad idea. It is against the forum rules for me to post the command to do this.

Yes it is easy, thanks for your uberness.  The main point is that I can't do what I want to do without using a root account.  Unless you know how to do what I want to do....

---

### Post by antilog on 2008-07-10
> **Traumadog said:**
> Are you trying to copy files into folders that are owned by "root" and have "root" as the only group member?  If so, that may be why the copy procedure fails.  

I don't think "Filezilla" has a method to use "sudo" when transferring files.  However, one solution might be to become a group member of the directories that you want to copy files to and then make sure the group has write access to those directories.

Others, of course, may have better ideas.

Hope this helps! :)

Traumadog.

Would it be safe to grant my user account access to all of /var/www? Would that be a

```
chown -R (myusername) /var/www
```

?

Since I am running Ubuntu Server, there is obviously no GUI, and some download links require a browser ex: [http://themes.wordpress.net/download.php?theme=nnnn](http://themes.wordpress.net/download.php?theme=nnnn)

I am just trying to streamline processes.

Thanks for helping me learn.

(running multiple websites in a virtual machine running ubuntu server 8.04.1, LAMP, VirtualHosts)

---

### Post by doogy2004 on 2008-07-10
I have removed this post to comply with the Ubuntu Forums policy for root tutorials.  Located here: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Thank you to the user who pointed this out to me, I am sorry if my actions have miss represented the Ubuntu Forums or the Ubuntu Community at large.

---

### Post by Traumadog on 2008-07-11
> **antilog said:**
> Would it be safe to grant my user account access to all of /var/www? Would that be a

```
chown -R (myusername) /var/www
```

?

Hello antilog,

I would suggest changing group ownership as follows:

```
chgrp -R (groupname) /var/www/(rest of path)
```

Then allow root (or whoever) to remain as the owner of the file.  Then you should change the permissions for the directories and/or files that you need to change or copy to so that group members have write access. (770 for directories and 660 for files.) 

Please note: the code you suggest in your message would change the user ownership of the files and directories and not the group ownership.  Either method, however, would give you write access to the files and directories in question. Change of user ownership would prevent you from having to update the permissions for each of the files and directories, but might cause other problems down the road.

Hope this helps,:)

Traumadog.

---

### Post by hyper_ch on 2008-07-11
instead of using root you could setup another user, set his UID and GID to the root one... you should be able to then login with that newly created user.

---

### Post by DezSP on 2008-07-11
While you're fishing around with permissions and whatnot, make sure you don't accidentally prevent the Apache user (usually www-data) from reading /var/www. I'd suggest chgrp as posted above, for example:

groupadd webwrite
usermod -aG webwrite yourusername
chgrp -R webwrite /var/www/(etc.)
chmod -R g+w /var/www/(etc.)

Using root for SFTP is a silly idea.

---

### Post by drhiii on 2008-07-11
Excellent and simple clarification of adding groups and permissions.

I am using ssh/scp to access a server.  Have tried this and still no joy.  I've also tried to add umask 002 and umask 007 to the ssh config file and restarted, reading this would overcome the problem.  Umask also set in /etc/profile.  

I am missing something because group permissions are not working the way I am used to executing them in prior *nix installs.  

Is there something additional when trying to use ssch/scp and group permissions?

tia


> **DezSP said:**
> While you're fishing around with permissions and whatnot, make sure you don't accidentally prevent the Apache user (usually www-data) from reading /var/www. I'd suggest chgrp as posted above, for example:

groupadd webwrite
usermod -aG webwrite yourusername
chgrp -R webwrite /var/www/(etc.)
chmod -R g+w /var/www/(etc.)

Using root for SFTP is a silly idea.

---

