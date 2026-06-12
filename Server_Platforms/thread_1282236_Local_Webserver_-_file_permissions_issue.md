---
title: "Local Webserver - file permissions issue"
date: 2009-10-04
forum: Server Platforms
---

### Post by Stoneface on 2009-10-04
I have created a new folder on my local Ubuntu server to do some testing. 
the output of ls -ls was
```
drwx------ 27 www-data me     4096 2009-10-04 12:25 peter

```
when I tried to enter the directory by entering sudo /var/www/peter/ I got a "Permission denied". I could only enter the folder as root.
So I did a ```
sudo chmod 755 /var/www/peter
```
Now I can enter the folder. 755 gave the folder:```
drwxr-xr-x 27 www-data me  27 4096 2009-10-04 12:25 peter
``` So all the permissions are now clearly stated. But, now when I enter the folder peter I see that file permissions are all messed up (incomplete). Here a few:
```

-rwx------  1 www-data me 3359 2009-10-04 12:25 AC_RunActiveContent.js
-rwx------  1 www-data me   5752 2009-10-04 12:25 add_series.php
drwx------  5 www-data me    4096 2009-10-04 12:25 admin

```
Why is that anyways? And is there a way to quickly give all folders 755 and files 644?

---

### Post by Lars Noodén on 2009-10-04
> **Stoneface said:**
>  And is there a way to quickly give all folders 755 and files 644?

Do you mean 664, instead, so that your group has rw permissions?

```

 sudo find /var/www type -d -exec chmod 775 {} \;
 sudo find /var/www type -f -exec chmod 664 {} \;

```

---

### Post by Stoneface on 2009-10-04
I found the following information @ [http://www.linuxquestions.org/questions/linux-general-1/chmod-all-files-644-and-files-755-542059/](http://www.linuxquestions.org/questions/linux-general-1/chmod-all-files-644-and-files-755-542059/)
To chmod all files 644 and all folders 755 in a folder you can enter the following command from a terminal
```

sudo find /var/www/ -type f -exec chmod 0664 {} \;
sudo find /var/www/ -type d -exec chmod 0755 {} \;

```

And after Lars' comment I made some further adjustments.

@ Lars Noodén Thanks for the post. I just posted this and saw yours! 664 for files is a better solution. Thanks!

---

