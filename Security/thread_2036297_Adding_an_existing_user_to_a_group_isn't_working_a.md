---
title: "Adding an existing user to a group isn't working as advertized"
date: 2012-08-01
forum: Security
---

### Post by rtedbyers on 2012-08-01
I do not know if I was misinformed, but it does not have the exected result.
 
I was told that in order for a developer to have read/write access to /var/www the user had to be added to the www-data group.
 
I have already successfully enabled the user to log in using ssh. When I log in as that user using ssh, I can change to /var/www, and I can read the only file there (index.html). However, I can not edit it.
 
I added the user to www-data using the following:
 
usermod -a -G www-data theuser
 
When I do so, I can see in the group file that the user name has been added to the end of the www-data record. But nothing else seems to have changed. The user still can not edit anything in /var/www.
 
What did I miss?
 
Thanks
 
Ted

---

### Post by steeldriver on 2012-08-01
iirc the change won't take effect until the /etc/passwd file is re-read - typically that's when the user logs out and back in but I believe the user can now force a reload in the current login environment by executing 

```
newgrp -
```

---

### Post by Doug S on 2012-08-01
Has /var/www had the write permission for www-data added?
see: [https://help.ubuntu.com/12.04/serverguide/httpd.html#http-directory-permissions](https://help.ubuntu.com/12.04/serverguide/httpd.html#http-directory-permissions)
 
which basically says do this:```
sudo chgrp -R www-data /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;
```

---

### Post by rtedbyers on 2012-08-01
> **steeldriver said:**
> iirc the change won't take effect until the /etc/passwd file is re-read - typically that's when the user logs out and back in but I believe the user can now force a reload in the current login environment by executing 

```
newgrp -
```

Thank you for your reply.

Alas, that isn't the issue here as I had logged in and out as that user several times (that thought had occured to me), but doing so didn't change anything

Thanks again

Ted

---

### Post by rtedbyers on 2012-08-01
> **Doug S said:**
> Has /var/www had the write permission for www-data added?
see: [https://help.ubuntu.com/12.04/serverguide/httpd.html#http-directory-permissions](https://help.ubuntu.com/12.04/serverguide/httpd.html#http-directory-permissions)
 
which basically says do this:```
sudo chgrp -R www-data /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;
```

Thank you for your reply.  That was what I missed.

But, I suppose I need to apply the same three commands to /usr/lib/cgi-bin, right?

Thanks

Ted

---

### Post by Doug S on 2012-08-01
Not exactly, as in the cgi-bin directory you would want the files to be executable.

---

### Post by rtedbyers on 2012-08-01
> **Doug S said:**
> Not exactly, as in the cgi-bin directory you would want the files to be executable.
So that means ```
find /usr/lib/cgi-bin -type f -exec chmod g=rws "{}" \;
``` becomes  ```
find /usr/lib/cgi-bin -type f -exec chmod g=rwxs "{}" \;
```right?

Thanks

Ted

---

