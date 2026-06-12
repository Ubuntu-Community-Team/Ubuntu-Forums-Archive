---
title: "FTP and appache question"
date: 2008-04-29
forum: Server Platforms
---

### Post by mam00th on 2008-04-29
Hi, I just have some questions concerning proftpd. I recently (yesterday hehe) installed a LAMP server with openssh on my sisters' old hp. For file transfer purpose, I decided to instal proftpd as well but here the thing.

I wondered, would there be a more efficient way to tansfer file to /var/www then ftping them to /home/user/ and then moving them using ssh?

Also what permission should my files in /var/www have? right now they are at 644 but if I intend to put PHP shouldn't I set it at 755?

Thanks in advance!

---

### Post by barnex on 2008-04-29
For this purpose you could for instance make a symbolic link to your home folder in the www directory: ```
ln -s /home/user /var/www
```.

---

### Post by cdtech on 2008-04-29
I run a home LAMP server with a FQDN (somewhere.com) and I configure my site off of my laptop computer befor I submit changes to my server. When the time comes to update my site I use Rsync to sync my laptop with my server.

On a command line from my laptop I use:
```
rsync -e "ssh -ax" -avz --delete --stats /var/www/mysite/ webadmin@mysite.com:/var/www/mysite
```

Using the rsync method only updates the changed files.

Then of course I have to copy the database to the server as well:
from my laptop
```
mysqldump -u user -p database > database.new
```

Then copy my database to the server:
```
scp database.new user@mysite.com:/var/www/mysite
```

Hope this helps ya...

---

### Post by mam00th on 2008-04-29
All right. But for learning purpose, could you explain me what a symbolic does?

---

### Post by mam00th on 2008-04-29
Also what permission should my files in /var/www have?

---

### Post by cdtech on 2008-04-29
> **mam00th said:**
> Also what permission should my files in /var/www have?

I use 775 so the group has access to change files as well. If your the only owner or group of the /var/www directory then 755 is more secure.

> In Linux and Unix, everything is a file. Directories are files, files are files and devices are files. Devices are usually referred to as a node; however, they are still files. All of the files on a system have permissions that allow or prevent others from viewing, modifying or executing. If the file is of type Directory then it restricts different actions than files and device nodes.

From: [[COLOR="DarkRed"]FilePermissions Ubuntu Documentation[/COLOR]]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by dark_religion on 2009-11-13
> Also what permission should my files in /var/www have? right now they are at 644 but if I intend to put PHP shouldn't I set it at 755?

Your script should work. If it doesn't work with 644 then try setting more rights. Less rights directory or fire have more secure it is.)

---

