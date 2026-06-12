---
title: "Unable to uploads files via sftp (FileZilla)"
date: 2016-03-05
forum: Server Platforms
---

### Post by Miyoko on 2016-03-05
Hi, i have looked at the google examples but they didn't seem to work so i wanted to make a post to see if i did something wrong or missed something.

> Problem, unable to upload or edit on sftp via filezilla and ssl key

I'm connecting via my second user since for security you should disable root login.


I have added the second user "supersecretuser" to the root / sudo group.
The var/www/html is owned by www-data


supersecretuser@supersecretserver:~$ ls -la /var/www
drwxr-xr-x 3 supersecretuser root 4096 Nov 12 20:12 .
drwxr-xr-x 13 root root 4096 Mar 5 14:55 ..
drwxr-xr-x 18 supersecretuser www-data 4096 Mar 6 00:10 html


I have added supersecretuser to www-data with 


sudo chown supersecretuser /var/www/html/*


I also tried 


sudo chmod 755 /var/www/html/*


Restarted server, still get the error


Command:	put "my computer\site_logo.png" "site_logo.png"
Error:	/var/www/html/styles/prosilver/theme/images/site_logo.png: open for write: permission denied
Error:	File transfer failed


I'm new to linux so if i forgot something please help.
I would prefer to not use something like this;


Quick-n-dirty solution would be to give 777 permissions - or rwx to all user/group/other. Not exactly *best practices*, but it'll help you test. Then you can dial back the permissions until you get them right.


Or is that what i should do?

I also tried 

> The command would be "useradd -G www-data supersecretuser" . That should let the user write into the directory. If not You might also need to run "chown -r www-data:www-data /var/www" 

But that gave me

> supersecretuser@supersecretserver:~$ sudo useradd -G www-data supersecretuser[sudo] password for supersecretuser:
useradd: user 'supersecretuser' already exists
supersecretuser@supersecretserver:~$ chown -r www-data:www-data /var/www
chown: invalid option -- 'r'
Try 'chown --help' for more information.
supersecretuser@supersecretserver:~$ sudo chown -r www-data:www-data /var/www
chown: invalid option -- 'r'
Try 'chown --help' for more information.

---

### Post by Miyoko on 2016-03-05
I solved it by reverting to a fresh install and use
- Maybe it helps someone in the future

```
sudo chown yourusername:www-data -R /var/www/html 
```
```
sudo usermod -aG www-data yourusername 
```

---

### Post by Bucky Ball on 2016-03-05
Good news. It will help more if you mark the thread as solved. See the first link in my signature at the bottom of this post and good luck.

---

