---
title: "403 Forbidden error on Apache"
date: 2019-09-02
forum: Server Platforms
---

### Post by TechnoJunky on 2019-09-02
I have done this similarly in the past on my laptop. Instead of using the default /var/www/html directory, I redirect the webpages to a mounted file system on another drive. I do this by going into /etc/apache2/sites available and editing the 2 files there. On my laptop, I redirect it to a second hard drive and that works. The issue on this computer is that I'm redirecting it to a mounted Raid 5 hard drive configuration. If I point it anywhere on the primary drive, no issues. But when I point it to /mnt/md0, I get the forbidden error. File permissions are identical. Does anyone know what needs to be done to enable this on a Raid mounted system?

---

### Post by TheFu on 2019-09-02
Assuming the file system used is a Linux ....

RAID isn't the issue.  Check all the permissions for directories for the www-data userid from the root to the directories where the files are located.  If the www-data user can't at least read the files, it won't work.

Perhaps open a window and switch to the www-data user in a shell then check the access that way?  It could easily be validated where the issue lies.

---

### Post by TechnoJunky on 2019-09-02
The filesystem is ext4.  Root is the owner of all directories down to the file index.html.  File ownership is still root:root.  Index.html won't load if it's on the raid array, but will load if it's anywhere on the standalone drive.

The original directory, /var/www/html has root:root ownership all the way to the index.html file.  I kept that the same.  I tried changing it as you suggested, to www-data:root, but didn't make a difference.

---

### Post by Doug S on 2019-09-02
If you want to use a non-stanadard directory, and in addition to all the permissions stuff, you have to tell apache to allow it via the /etc/apache2/apache2.conf file.
Just copy the /var/www/html stantza stuff to whatever, example:

```
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

<Directory /media/newhd/test_web/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>
```

---

### Post by TechnoJunky on 2019-09-02
While I haven't had to do that for any other directory, I did try this as well, but doesn't help.

<Directory /mnt/md0/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

---

### Post by TheFu on 2019-09-02
Permissions are more than just the owner.  Less words, more command output like **ls -l **for every directory level starting from the location with the files that aren't working and moving up to /.

**tree -dp** /other-storage might make useful output.
```
$ tree -dp /var/www/
.
&#9500;&#9472;&#9472; [drwxr-xr-x]  2014-sa.example.com
&#9500;&#9472;&#9472; [drwxr-xr-x]  acme
&#9500;&#9472;&#9472; [drwxr-xr-x]  b.example.com
&#9474;** &#9492;&#9472;&#9472; [lrwxrwxrwx]  b -> /opt/projects/blog.example.com/output
&#9500;&#9472;&#9472; [drwxrwxr-x]  blog.example.com
&#9500;&#9472;&#9472; [drwxrwsr-x]  dc404.example.com
&#9474;** &#9492;&#9472;&#9472; [drwxrwsr-x]  img
&#9500;&#9472;&#9472; [drwxr-xr-x]  html

```
Web servers do produce logs. Have you checked those out to see the actual error?

Might be helpful if you posted the config file from sites-enabled/ too.

---

### Post by TechnoJunky on 2019-09-02
You were right.  It was a permission issue.  However, it was lower in the directory structure.  md0 had 0 for other, 770.  I changed it to 771 and now the webpage loads.  Thank you.

---

