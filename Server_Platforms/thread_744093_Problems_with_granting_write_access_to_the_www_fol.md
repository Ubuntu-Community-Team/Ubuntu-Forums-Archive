---
title: "Problems with granting write access to the www folder"
date: 2008-04-03
forum: Server Platforms
---

### Post by deejross on 2008-04-03
I am trying to grant myself access to write to the /var/www folder so that I can upload files via SFTP(SSH). This is what I've done so far:

Added myself to the www-data group:
```
sudo usermod -a -G www-data ross
```

Changed the owner of the /var/www directory (recursively):
```
sudo chown -R www-data /var/www
```

Change the group of the /var/www directory (recursively):
```
sudo chgrp -R www-data /var/www
```

Change the permissions on the /var/www directory (recursively):
```
sudo chmod -R 0775 /var/www
```

Yet, even if I log into an SSH console, I get:
```
mkdir: cannot create directory `/var/www/test': Permission denied
```

Any ideas on how to make this work?

---

### Post by djgrandmarquis on 2008-04-03
What about doing it a different way?

I would just log into my SSH server as my normal username, then I would modify the www files using the sudo command. This is essentially the way I modify my www file locally, with the additional step of logging in via SSH first.

Try this maybe: log in as normal user, use SFTP to copy files to your home directory, move the files to www as root (using sudo).

---

### Post by deejross on 2008-04-03
Well, the idea is FTP into the www directory, but with SSH. On my Windows machine at work, I use WinSCP to log into the server via SSH. Besides, I'm going to be developing on this server and it wouldn't make much since to make a change, upload the file, then use putty to sudo and move the file every time I made a change.

---

### Post by cdenley on 2008-04-03
What you did should work after you create a new session. Check the output of the command "groups" to make sure you are currently in the www-data group. Your group memberships are only read when you log in.

This a not a good approach, though. You don't want to give www-data write access to /var/www, because then your web scripts will be able to edit anything in /var/www if you're not careful with your scripting, or if there is a vulneribility with apache or a module. What you should do, if you really need convenient access and don't mind the reduced security, is just make yourself the owner.
```

sudo chown -R 1000 /var/www

```

---

### Post by deejross on 2008-04-03
I restarted the session, but it's still not working. I also double checked /etc/group and I am in that group. Is there another way to accomplish this that's secure and convenient?

---

### Post by cdenley on 2008-04-03
Whenever a non-root user has write access to /var/www, you sacrifice a layer of security. Whenever root has remote access to your server, you sacrifice a layer of security. The best way to have remote write access to /var/www, as I said, would be to make yourself the owner.

Did you run the "groups" command to check that you are in that group? Post the output from these commands.
```

ls -ld /var/www
groups
whoami
mkdir /var/www/test

```

---

### Post by deejross on 2008-04-03
After trying those commands using Putty, it works. But when I went back to WinSCP, it still says permission denied. I just rebooted my Windows machine (Windows updates suck like that), so I know WinSCP created a new SSH session. I also double checked that I was using the same username/password between putty and WinSCP.

In WinSCP, I can create/delete in my home directory, but it still won't let me do anything in /var/www. Any ideas why this is?

---

### Post by cdenley on 2008-04-03
Not really, unless winscp is caching directory permissions.

---

