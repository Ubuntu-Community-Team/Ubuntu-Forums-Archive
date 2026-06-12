---
title: "Phpmyadmin isn't shown on localhost!"
date: 2007-01-08
forum: Server Platforms
---

### Post by Isoss on 2007-01-08
Hey

I have apache2, mysql5, php5 with phpmyadmin installed. I've been working on the server for a long time and everything is fine, but suddenly phpmyadmin stopped displaying in the index of the server when I type: [http://localhost](http://localhost) although the folder is still there in /var/www !!! when I type [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it gives me this error: 

> **Internal Server Error**

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 Server at localhost Port 80

Hope this is solvable! 

Thanks

---

### Post by Paul41 on 2007-01-09
Did you check to see if the permissions to the folder and/or files get changed somehow?

---

### Post by johnnymac on 2007-01-09
So....an ls -la should look something like this:

```

lrwxrwxrwx  1 root    root       21 2006-09-25 16:11 phpmyadmin -> /usr/share/phpmyadmin

```

Make sure the symlink is there and correct....

---

### Post by Isoss on 2007-01-10
OK, thanks guys .. I purged everything and reinstalled them. but I will surely try to apply this solution whenever it happenes again.

Thanks

---

