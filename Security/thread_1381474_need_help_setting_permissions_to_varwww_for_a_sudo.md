---
title: "need help setting permissions to /var/www for a sudo user"
date: 2010-01-14
forum: Security
---

### Post by husskii on 2010-01-14
Hi I've installed joomla on a ubuntu LAMP server but I did it through proxmox and I didn't really have control over the install or where I want the files / directories. 
I was actually quiet surprised it setup ubuntu with root and not a super user.

so my current setup is I have a / dir then bin, boot, root, home, var etc & then in the home dir I have my user which I created after the setup was done and I also had to add this user to nano /etc/sudoers my self.
I have created a configuration.php file with my sudoer user and added it to my /var/www/ dir and even tho I created it with my user who I made a sudoer, I still don't have rw permission to that file nor do I have any permissions to the /var dir.

I have tried a few chmod's i.e 775 but I couldn't get it to work and when I try access through ftp I still don't have any rights to that file. I even tried setting the permissions straight through ftp but because root cant login to my ftp I cant even do that.
(I use proftp because I kept messing up with pureftp and with proftp I cant get root to login to filezilla.)

what I want to eventually have is my user to be able to have read write permissions to the var folder as I need that folder to continue my setup off joomla.

so the layout is like this.
//var/www/configuration.php & //home/sudoer user

how can I set the permissions so that the sudoer user has the rwx permissions to that file, preferably the whole var dir.

I could really do with the help or advise and it would be greatly appreciated, Ive been on this one section for hours and have messed up each time, which has made me delete the whole OS and start all over again maybe 5 or 6 times now... 
(if not more) lol

Ive even tried following the file permissions in the ubuntu community help and still no good, I think I might be missing the (ls) bit but not too sure and also not too sure how to do that bit.

Thanks in advance 
husskii :)

---

### Post by cariboo on 2010-01-15
Instead of using sudo to read/write to /var/www, why not make your user a member of the group that owns the files in the directory. For instance if the directory your files are in is owned by www-data, add yourself to the www-data group eg:

```
sudo gpasswd -a <username> www-data
```

you should then be able to write files to the directory.

---

### Post by husskii on 2010-01-17
thanks cariboo907 that was my mistake, I had tried to make my user part of the root group and it didn't work.. I didn't realize I Dir had its own group, before I saw this post I had eventually just changed the wrx permissions on the folder and did what I had to do, then changed it back, but as im sure there will be more hiccups Ill add my user to the www-data group

Thanks:)

---

