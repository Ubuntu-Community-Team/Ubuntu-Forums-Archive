---
title: "too much permissions on LAMP filesystem"
date: 2007-06-26
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-06-26
I have a directory IMAGES with all the images uploaded by users of websites running on my LAMP server

Filesystem:

-IMAGES (drwxr-xr-x myuser mygroup)
      |_______HUGE  ([COLOR="Red"]drwxrwxrwx[/COLOR] myuser mygroup)
      |                 |_____BEAUTY ([COLOR="Red"]drwxrwxrwx[/COLOR] myuser mygroup)
      |                 |_____BEAST
      |                 |_____UGLY
      |_______NORMAL
      |                  |_____BEAUTY
      |                  |_____BEAST
      |                  |_____UGLY
      |_______SMALL
                            |_____BEAUTY
                            |_____BEAST
                            |_____UGLY

I think to have too much permissions as you can see in red
web-users should be able to upload images through cgi-script
images must be viewed on the web
images uploaded have www-data as user and group and rw-r--r-- which seems to be fine
Would it be better to change myuser mygroup with www-data?
Can somebody share with me some wisdom?

---

### Post by kidders on 2007-06-27
Hi there,

> **erasmo.da.rotterdam said:**
> Can somebody share with me some wisdom?The general "best policy" advice is to set file access permissions to the minimum possible that can work, so that nothing that doesn't *need* access can get access. With very few exceptions, if you find yourself doing a "chmod 777", you're *definitely* making a mistake.

In your situation, assuming all interaction with your images is done via your web server, I'd prefer to see files "chown www-data:root" and "chmod 660", or something similar. (Directories obviously need an additional execute bit.)

Is that any help?

---

