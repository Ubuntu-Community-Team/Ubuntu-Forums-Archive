---
title: "SFTPD Permissions Denied"
date: 2013-05-07
forum: Server Platforms
---

### Post by shaquille110 on 2013-05-07
Hi there.

I have connected to my server (Which is a AWS EC2) via SFTPD and I am able to upload and download folders in the user directory /home/user1 but I can't read, write or modify /var/www/ 
How would I be able to make the user "user1" able to modify, read, write, and remove in the /var/www/* directory?

---

### Post by darkod on 2013-05-07
You have two options, depending what do you prefer.
1. if these are files for a website, you can make a folder in your home like /home/user/domain.com and keep the files there. In the apache configuration for that website you will have to modify the Document Root so that it points to the correct folder.
2. Give your user permissions to write to /var/www but be careful since the www-data user should still be able to use that folder. I'm not sure you can simply make /var/www owned by you, and whether that will make issues for apache.

In any case, you need something like SSH access or terminal access, to view these options and do what you need. If /var/www is owned by the www-data group and has RW permissions, you can also add your user to the www-data group which could be the easiest solution.

---

### Post by darkod on 2013-05-07
What you can also do is upload files in your Home folder, and then use sudo to copy if your user has sudo rights. Something like:
```
sudo cp /home/user/filename /var/www/destinationfolder/
```

That should copy it since with sudo you can copy anywhere.

---

