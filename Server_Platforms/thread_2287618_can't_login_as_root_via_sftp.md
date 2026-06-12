---
title: "can't login as root via sftp"
date: 2015-07-21
forum: Server Platforms
---

### Post by Drone4four on 2015-07-21
I can't login as root via sftp in my ftp clients (Konqueror, FileZilla).  I can login as a regular user via sftp just fine.  I can also login to root via a regular user from a shell.  

I tried googling 'sftp cannot login as root' and found a number of users sharing similar experiences , but nothing seems to help. 

I tried uncommenting my 'PasswordAuthentication' line in my /etc/ssh/sshd_config file .  I then restarted ssh. No dice.  I then commented that line back out and restarted ssh again.

I tried commenting out 'Subsystem sftp /usr/lib/openssh/sftp-server' in that same config file, restarted ssh.  No dice.  I then change that setting back.

What else could I try?  

Its worth noting that I did uninstall the ftpd package recently, while in the process I restored all my ssh configuration files back to their originals.

---

### Post by TheFu on 2015-07-21
Doubt you will like this answer.

Don't connect as root. Use file permissions to do what you need, not root.  Are you using keys?
Of course, you could create another account, not named "root" with the same uid and use that. Not a good idea, but it will work.

Ubuntu is designed to not use any root logins and it is against the [forum policy]("http://ubuntuforums.org/showthread.php?t=1486138") to help side-step that. Of course, you can do whatever you like. The main settings are in /etc/ssh/sshd_config and that manpage is very complete.

I've never tried to do this, so I don't **know** the exact answer, but I do use a root-equiv backup account with ssh-keys all-the-time (nightly).

---

### Post by Drone4four on 2015-07-23
The reason for the unconventional security practice on my part is because I am using a DigitalOcean droplet.  Ubuntu's configuration on a freshly created droplet by default comes with a root user.  Would you recommend that I eliminate the root user and reconfigure the security scheme to match the way Ubuntu is supposed to be run, w/o a super user?

The reason why I have been trying to get access as root via sftp is because my /var/www/domainname/ which houses apache's public_folder is set for root access only.  It hit me like a ton of bricks two nights ago when I was lying in bed trying to fall asleep that if I recursively reset the permissions of my public folder as root so that regular users can edit and make changes, then I could go about working in said directory as a regular user.  With directories set to 0644 and and files set to 0755, then I wouldn't need to log in as root to do work.  This makes sense to me now.

What I am trying to resolve now is why in my top level public folder directory, these commands do nothing:

```

# find * -type d -print0 | xargs -0 chmod 0755
# find * -type f -print0 | xargs -0 chmod 0644
# exit

```

I have been troubleshooting apache public folder permissions [elsewhere on this forum]("http://ubuntuforums.org/showthread.php?t=2268991&p=13326447").

---

### Post by TheFu on 2015-07-23
> **Drone4four said:**
> The reason for the unconventional security practice on my part is because I am using a DigitalOcean droplet.  Ubuntu's configuration on a freshly created droplet by default comes with a root user.  Would you recommend that I eliminate the root user and reconfigure the security scheme to match the way Ubuntu is supposed to be run, w/o a super user?

The reason why I have been trying to get access as root via sftp is because my /var/www/domainname/ which houses apache's public_folder is set for root access only. 

You cannot delete root, but you don't need to use it after you create a normal userid with sudo privileged. Make a new userid, add it to the sudoers group, verify you can sudo with it and move on.   Make the root account have a 200 character passphrase and never use it again.  sudo is your friend.  Ok - so there are times to use root - like when a fresh system was just installed and you need to spend 20 min setting up 50 things.  After that, sudo should be used so there is a record of every command used.

I and BAB1 replied with the solution to the apache issue in another thread. There isn't any way around understanding the file and directory permissions for a multi-user OS.

---

### Post by bab1 on 2015-07-24
> **Drone4four said:**
> The reason for the unconventional security practice on my part is because I am using a DigitalOcean droplet.  Ubuntu's configuration on a freshly created droplet by default comes with a root user.  Would you recommend that I eliminate the root user and reconfigure the security scheme to match the way Ubuntu is supposed to be run, w/o a super user?

The reason why I have been trying to get access as root via sftp is because my /var/www/domainname/ which houses apache's public_folder is set for root access only.  It hit me like a ton of bricks two nights ago when I was lying in bed trying to fall asleep that if I recursively reset the permissions of my public folder as root so that regular users can edit and make changes, then I could go about working in said directory as a regular user.  With directories set to 0644 and and files set to 0755, then I wouldn't need to log in as root to do work.  This makes sense to me now.

What I am trying to resolve now is why in my top level public folder directory, these commands do nothing:

```

# find * -type d -print0 | xargs -0 chmod 0755
# find * -type f -print0 | xargs -0 chmod 0644
# exit

```

I have been troubleshooting apache public folder permissions [elsewhere on this forum]("http://ubuntuforums.org/showthread.php?t=2268991&p=13326447").
To add to @TheFu's comments;  There is nothing magical about root having ownership or root's permissions to various folders.  Ownership is really just a notation of who the creator was while the permissions are set by the current umask.  One of the little items that seems to trip new users is that fact that the root user umask is different from that of a mortal (human) user on current Ubuntu versions.  Root is 755/644 (dir/file) while the mortal user is 775/664.  The thought is when root creates a directory or file it most likely needs tighter permissions.  In any event this is just the default.  You as the systems administrator have to decide who has access to the file and what that access is.  

File security is all about who has access and what happens if that user account is compromised.  If I have a user that has rw access to all of the files in the DocRoot and that user is compromised, then the web page is compromised.  On the other hand if the compromised user has read only (r) permissions then we have no problem with the files in the DocRoot.  

Since the Apache user (www-data) can be easily compromised I only allow www-data to have read permissions to that directory.  This is easily provided by world read only permissions (others=r) and eXecute permissions on all folders in the path to the DocRoot so the "others group" can descend to the DocRoot directory.  All the other permissions on the actual DocRoot have to do with who you want to have write permission as everyone has read permissions anyway.  I personally leave the ownership of the DocRoot directory as root.  It doesn't matter to me.  The group ownership is what I control access with.  I created a group named www-content and made that group the "group owner" of the DocRoot.  So the ownership looks like this:: ** root:www-content:others**.  Now everyone has read permissions and only root and those in www-content have write permission.  I never add www-data to the www-content group.  As I said before I do not want www-data to have write permissions.
At this point when anyone in the www-content group wants to create, modify or delete a file or sub directory they can.  When a new directory or file is created the owner is always **user:user:others** unless you set the sgid bit at the DocRoot.  In that case the new file or directory is created with the group www-content as group owner.  This is the inheritance you need to have all www-content group users have consistent access to the web pages in the DocRoot or it's subdirectories.  I always use DocRoot subdirectories with different user groups so I can have all the virtual hosts at the same DocRoot.  Something like this```

/DocRoot/
| --    Vhost1  (root:www-vhost1:others)
|
| --    Vhost2  (root:www-vhost2:others)
|
| --    Vhost3  (root:www-vhost3:others)

```...as a matter of fact the DocRoot doesn't have to be anywhere near that rest of the Apache2 file system.  I keep my DocRoot at /srv/www/.  This makes my virtual hosts look like this```

/srv/www/
| --    Vhost1
|
| --    Vhost2
|
| --    Vhost3
```... All of this is basically what @TheFu has indicated in your other thread anyway.

---

### Post by Drone4four on 2015-07-24
Thanks for ur insight and suggestions, bab1 and TheFu.  I unfortunately won't be able to follow up until next week.  I will get to it eventually tho.

---

