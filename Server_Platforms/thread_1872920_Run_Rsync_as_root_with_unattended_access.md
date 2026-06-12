---
title: "Run Rsync as root with unattended access"
date: 2011-10-31
forum: Server Platforms
---

### Post by arulnambi on 2011-10-31
Hi All,
I am trying to rsync a tomcat webapps folder from the primary server to secondary system using rsync through crontab (So I set up for unattended access by creating a ssh password and copying it to the primary system). I have setup rsync and its working fine, when I try to run rsync as a normal user and I don’t have to enter the password for the primary system. 
The problem I am having is I need to run it as a sudo user, since the file I am trying to copy belong to tomcat user, or else I get the message
“rsync: chgrp "file/path/file: Operation not permitted (1)”
.
Now if I run it as a sudo user I am being prompted for the password(I cannot enter password as I am automating it in crontab) for the remote system, unlike when I try to run it as normal user where I am not being prompted for password.
Rsync command I am using
“rsync -avz -e "ssh" [email]user@secondary.com[/email]:/backup_data/  /backup_data/”
Solutions I tired
1-	I moved the key to /root/.ssh/authorized_keys (I am not sure if it is the right directory
2-	I tried assigning the user whom I rsync with to the same group as tomcat user to whim the file belongs to
3-	I tries logging as sudo user and running the command again.
Every time I try I either get a Operation not permitted (1) message or I am being asked for the password for [email]user@secondary.com[/email]
Any help is appreciated.:D:D
Thanks in advance
with regards
Arul

---

### Post by lykwydchykyn on 2011-10-31
You need to generate an ssh key ~as root~ and copy it over to the remote machine, like so:

```

sudo ssh-keygen -t rsa
sudo ssh-copy-id -i /root/.ssh/id_rsa.pub user@secondary.com

```

That should take care of it.

---

### Post by SeijiSensei on 2011-11-01
A lot simpler solution is to run the command as root.  You can add the command to root's crontab by running "sudo crontab -e", or you can add it to the system-wide crontab /etc/crontab.  Note that for /etc/crontab the syntax is slightly different.  It includes the name of the user between the time fields and the script to be run like this:

```
1 1 * * * root rsync -avz /path/to/backup_data/* root@secondary.com:/backup_data/ 
```

That runs the rsync script as root at 1:01 am.

---

### Post by Lars Noodén on 2011-11-01
You could make the user that you are running rsync from a member of the group that the files belong to.  That should give the read access needed.

Alternately if you want to avoid connecting to ssh as root then you can [configure rsync and sudo](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo) to work together. It's a detailed process to get the right configuration into /etc/sudoers but not hard.

---

### Post by arulnambi on 2011-11-01
Hi All,
Thanks a lot for all your inputs, they were all very informative. But lykwydchykyn reply worked fine for me. > **lykwydchykyn said:**
> You need to generate an ssh key ~as root~ and copy it over to the remote machine, like so:

```

sudo ssh-keygen -t rsa
sudo ssh-copy-id -i /root/.ssh/id_rsa.pub user@secondary.com

```

That should take care of it.
Thanks a lot lykwydchykyn :KS :D
With regards
Arul

---

### Post by jwcalla on 2011-11-30
I've been pulling my hair out trying to get something like this to work.

> **SeijiSensei said:**
> A lot simpler solution is to run the command as root.  You can add the command to root's crontab by running "sudo crontab -e", or you can add it to the system-wide crontab /etc/crontab.  Note that for /etc/crontab the syntax is slightly different.  It includes the name of the user between the time fields and the script to be run like this:

```
1 1 * * * root rsync -avz /path/to/backup_data/* root@secondary.com:/backup_data/ 
```That runs the rsync script as root at 1:01 am.

Can you really do this?  How can you log into secondary.com as root user without supplying the root's password?  And isn't there no root password in Ubuntu?

---

### Post by lykwydchykyn on 2011-11-30
> **jwcalla said:**
> I've been pulling my hair out trying to get something like this to work.



Can you really do this?  How can you log into secondary.com as root user without supplying the root's password?  And isn't there no root password in Ubuntu?

You can log in without a password by using key-based authentication, which is what we've been discussing.

Of course, getting the key onto the remote system requires that you have a password set for root, and root enabled on ssh -- two things I would strongly recommend against doing on Ubuntu (or, for the latter, on any system).

You could enable these things temporarily while copying the key over, then disable them.  Or copy the key manually via another user account.

But frankly, for a backup situation there should be no need for using root, or at least not on both computers.  Simply create or designate a regular user for backup purposes, and make sure the backup destination is writeable by that user.

---

