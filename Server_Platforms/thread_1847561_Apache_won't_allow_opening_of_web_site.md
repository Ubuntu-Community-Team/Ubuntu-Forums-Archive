---
title: "Apache won't allow opening of web site"
date: 2011-09-21
forum: Server Platforms
---

### Post by Ghost_Mazal on 2011-09-21
Morning guys ,

I have a 32bit Ubuntu 10.10 server. Fresh install and LAMP selected.

My problem is with the web site. When I hit just the server I get the "it works !" page.
However when I try and hit my webpage that is in a folder within /var/www then I just get the error "You do not have permissions to view this page" from another pc's web browser.

The folder is a sub folder like so /var/www/it and inside is all my pages.

Currently that folder and it's contents belongs to the one and only user on the system.

I tried changing permissions to the folder and it's contents to 775 so that other can read and execute. But that did nothing.

Can someone help me please ?

---

### Post by Drenriza on 2011-09-21
Try and read this article,
[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)
Since i am pretty sure you need to make your site available.

Also i have experienced that my files and directories need to be in the www-data owner and www-data group
```
sudo chown www-data:www-data /files 
```

---

### Post by Dangertux on 2011-09-21
Also might want to change up the permissions

```

sudo chmod -R 750 /var/www/yoursite

```

---

### Post by Drenriza on 2011-09-21
should he be able to at least see his site, as long as the read bit is set? 
Which is set by standard by read and write permissions?

---

### Post by Ghost_Mazal on 2011-09-21
Oh man I am such an IDIOT !!!!!!!!!!!! ](*,)

I found the problem , I was standing in the wrong folder the whole time. I was in the folder containing the backup.](*,)
It has exactly the same naming.

Sorry for wasting your time guys. I feel really stupid now.

---

### Post by Drenriza on 2011-09-21
:d

---

### Post by Dangertux on 2011-09-21
To answer the read bit question yes. However, depending on where the files came from (sometimes uploading them from a Windows box causes problems) the permissions will get mucked up.

---

