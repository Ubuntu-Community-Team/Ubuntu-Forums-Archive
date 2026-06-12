---
title: "File permissions for web server directory"
date: 2014-03-27
forum: Server Platforms
---

### Post by Help! on 2014-03-27
Hi All,

First time working on a server other than a shared hosting environment and I think something is not quite correct. 

I have a PHP application that needs to create pdf files in a directory under /var/www/website/pdfs  It works, but only if I set the file permissions to 777.  

The entire /var/www directory is owned by root and I have no idea of its group.  Should this not be working with a file permission of 775?

---

### Post by thnewguy on 2014-03-27
You probably want to change the owner of your website's directory from root to "www-date". Typically the web server runs as the www-data user and, if it needs to write files to your website's directories, you will want it to have write access.

You're right, running with permissions 777 on files and directories is bad. You should be able to get away with 755 with directories and 644 for files if they are owned by the www-data user.

---

### Post by Help! on 2014-03-27
Thanks, your mention of www-data gave me enough info to Google group permission for the /var/www directory.

So I ran:  ls -ld /var/www/
and got: drwxr-xr-x 6 root root 4096 Mar 27 18:12 /var/www/  So it is owned by root and in the root group.  That would explain why www-data can't use it...

So then I did this:
user@srv:~$ sudo usermod -a -G www-data user --------------------- Add the user user (I know bad user name idea) to the www-data group
user@srv:~$ sudo chown -R user:www-data /var/www --------------- Changed the owner to "user" so I can log in and manage files without problems
user@srv:~$ find /var/www -type f -exec chmod 0640 {} \; ---------- Find all files and change the permissions to 0640 (640)
user@srv:~$ sudo find /var/www -type d -exec chmod 2750 {} \; ---- Find all directories and change permissions to 2750 (750)

user@srv:~$  ls -ld /var/www/                                                     
drwxr-s--- 6 user www-data 4096 Mar 27 18:12 /var/www/ ----------- New owner and group


Then to make my directory with that will create the pdf files writable I set the permissions to 770 using Dream Weaver, and it works!

Please let me know if you see anything wrong with this config.

---

### Post by Lars Noodén on 2014-03-28
> **Help! said:**
> 
Please let me know if you see anything wrong with this config.

It would be safer to use a different group, other than that the method is fine.  The group www-data exists to provide privilege separation for the HTTP daemon and the unprivileged part runs under that user and group.  So giving write permissions to that group to any directory that the web server publishes provides great potential for trouble should something go wrong, and it violates a variant of the principle Write XOR eXecute (W^X).  In general, the web server should not be allowed to potentially write to the very same pages it is publishing.  

I would recommend making a new group, such as 'webmasters' or something like that, and using that and removing www-data from the web directories.

---

### Post by SeijiSensei on 2014-03-28
Note that if you follow Lars's suggestion, you'll need to add the www-data user to any "webmasters" group you create.

As a general rule, I try to keep any directories writable by www-data outside of the webroot, but that obviously won't work if you are writing an application to create publicly-visible PDFs.

---

### Post by SeijiSensei on 2014-03-28
duplicate deleted

---

### Post by Lars Noodén on 2014-03-28
@ SeijiSensei, thanks for catching that.  I saw /var/www and meant for the whole site, but giving www-data write access for a specific directory would work.  It's just that making web directories writable by the web server makes me quite nervous.  The ability to write should be limited to as small an area as possible.

---

