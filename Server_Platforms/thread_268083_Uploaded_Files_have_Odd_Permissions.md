---
title: "Uploaded Files have Odd Permissions"
date: 2006-09-29
forum: Server Platforms
---

### Post by languagemaven on 2006-09-29
Greetings,

I am developing a website for an organization that I work at. I have experience working with an established web server when developing websites, but where I am working now, it fell on my shoulders to set up a web server before I did the web development. I had never done this before. So far, I have everything working just great, except one thing.

When I upload files to the home directory for a user (I use the home directory of that user as the www file folder that Apache serves up) the directories I upoad have permissions set at 700 and all the files I upload have permissions set at 644. This of course messes things up when it comes to the website (Drupal-powered) and I have to manually change most everything to 755.

Can anyone help me?

Thanks.

---

### Post by jpkotta on 2006-10-01
You could just make a script to change permissions and run it after uploading.

```
find /home/www -type d -exec chmod 700 '{}' \;
find /home/www -type f -exec chmod 755 '{}' \;
```

Also, your default permissions are set with the 'umask' command.  umask takes 4 octal digits, and the permission on new files and dirs is ```
(default & ~umask)
```, where default is 777 for dirs and 666 for files, umask is the umask setting, & is bitwise AND, and ~ is bitwise NOT.  My umask is ```
umask 0077
```, thus my files are created with 600 and dirs with 700.

---

