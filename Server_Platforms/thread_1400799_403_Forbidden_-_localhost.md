---
title: "403 Forbidden - localhost"
date: 2010-02-07
forum: Server Platforms
---

### Post by dv310p3r on 2010-02-07
I've got Ubuntu 8.04 Server setup and apache up and running and serving my pages. But I have to chmod 777 any of them to be able to see them through my browser on a different computer from within my network. 

I want to be able to just see the webpages without having to chmod 777 all of the files and folders recursively first. 

the var/www folder is shared and I access it through my Windows box to do all my editing and updates to the sites.

Any ideas?

---

### Post by mushwars on 2010-02-07
```
sudo chown -R www /var/www
sudo chmod -R 0644 /var/www
cd /var/www
sudo find . -type d -exec chmod 0755 {} \;

```If you have a forum/blog/any other software in php that you didnt code you want to be careful not to change its permissions.

---

### Post by dv310p3r on 2010-02-07
Thanks for the quick reply, it's much appreciated. Would it be too much to ask for an explanation of what's going on in your code?

Thanks a million.

---

### Post by dv310p3r on 2010-02-07
[code]sudo chmod -R 0644[code]

This didn't work for me, it says missing operand after 0644

---

### Post by mushwars on 2010-02-07
oops I am sorry you need to put /var/www after that.

Basically this code will fix the ownership issues as well as the permissions issues of all the files in your htdocs.

fixed code above.

the find command will change all directories into 755 permissions while leaving the files 644

---

### Post by dv310p3r on 2010-02-07
Thanks a million, it worked like a charm!!!!

Thanks again.

---

### Post by mushwars on 2010-02-07
If you could mark this thread as solved. :)

I am glad I could help, you might need to run those commands again in the future.

---

### Post by amac777 on 2010-02-07
To avoid having to manually make all the files readable by apache each time you make changes, you may want to set the /var/www directory so all files in that directory will belong to www-data group, so apache can read them.
```

sudo chgrp www-data /var/www
sudo chmod g+s /var/www
```

After that, all new files you create in /var/www should have the group of www-data automatically and therefor apache should be able to read them.

---

### Post by dv310p3r on 2010-02-08
After doing a few things on the server, suddenly I'm back to why I started this topic. I can't make any changes to the /var/www files through my windows box. I'm not sure what happened.

---

### Post by dv310p3r on 2010-02-08
Actually forget it. I've fixed it by changing the owner of the whole directory to my user.

---

### Post by mushwars on 2010-02-09
> **dv310p3r said:**
> Actually forget it. I've fixed it by changing the owner of the whole directory to my user.
Good luck writing to a file with a php script. (You can add [s]apache[/s] www to a group called website along with your regular user then chmod g+w)

---

### Post by dv310p3r on 2010-02-10
> **mushwars said:**
> Good luck writing to a file with a php script. (You can add [s]apache[/s] www to a group called website along with your regular user then chmod g+w)

That the kind of information I like to know. Can you explain why that will happen, and if you wouldn't mind could you be a tad more specific as to how to rectify or prevent that from happening. I am not too familiar with the command line so, the more specific the better. 

Thanks a Million!

---

