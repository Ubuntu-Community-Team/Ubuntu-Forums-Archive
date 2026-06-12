---
title: "Apache user_dir throws 403 error"
date: 2011-09-23
forum: Server Platforms
---

### Post by ilSignorCarlo on 2011-09-23
Hi,
I'm trying to set up the public_html userdir on a new server.

Now if I try to access [http://myserver.com/~username](http://myserver.com/~username) it says I don't have permissions to access that directory.

Before posting here I've searched and read many other threads and tutorials.
So, I checked permissions of the directory and added the www-data group. Still it doesn't work.

What can I do?

---

### Post by Ryan Dwyer on 2011-09-23
What does the Apache error log say? (/var/log/apache/error.log)

---

### Post by ilSignorCarlo on 2011-09-24
> **Ryan Dwyer said:**
> What does the Apache error log say? (/var/log/apache/error.log)

It says:

[Sat Sep 24 10:36:43 2011] [error] [client 2.224.56.25] (13)Permission denied: access to /~username/index.html denied

---

### Post by Ryan Dwyer on 2011-09-24
What are the permissions on that file, as well as the user's directory itself?

ls -l /home/username
ls -l /home/username/index.html

---

### Post by ilSignorCarlo on 2011-09-24
> **Ryan Dwyer said:**
> What are the permissions on that file, as well as the user's directory itself?

ls -l /home/username
ls -l /home/username/index.html

The file is actually inside the public_html directory, which is the default apache userdir, so:
```


~$ ls -l /home/carlo/
total 4
drwxr-xr-x 2 www-data www-data 4096 2011-09-23 18:43 public_html

~$ ls -l /home/carlo/public_html/
total 4
-rwxr-xr-x 1 www-data www-data 10 2011-09-23 18:43 index.html

~$ ls -l /home/carlo/public_html/index.html 
-rwxr-xr-x 1 www-data www-data 10 2011-09-23 18:43 /home/carlo/public_html/index.html
```

---

### Post by Ryan Dwyer on 2011-09-24
I'm going to predict that your /home/carlo directory is owned by you and chmodded to 700. Run "ls -l /home" to confirm, then "sudo chmod 755 /home/carlo".

By default it's 755, so you must have changed those permissions at some point.

---

### Post by ilSignorCarlo on 2011-09-24
> **Ryan Dwyer said:**
> I'm going to predict that your /home/carlo directory is owned by you and chmodded to 700. Run "ls -l /home" to confirm, then "sudo chmod 755 /home/carlo".

By default it's 755, so you must have changed those permissions at some point.

ok, you're right. that was the problem. thanks : D
but what if I don't want to make the home readable to others?

---

### Post by Ryan Dwyer on 2011-09-24
Then put www-data in the carlo group and make the permissions 750.

---

### Post by ilSignorCarlo on 2011-09-25
> **Ryan Dwyer said:**
> Then put www-data in the carlo group and make the permissions 750.

no, this doesn't work.

I did this:
```

~$ sudo adduser www-data carlo
Adding user `www-data' to group `carlo' ...
Adding user www-data to group carlo
Done.
~$ sudo chmod 750 /home/carlo/
~$ ls -l /home/
total 12
drwxr-x--- 4 carlo       carlo       4096 2011-09-23 20:11 carlo

```

and I got the same error as before

---

### Post by Ryan Dwyer on 2011-09-25
Try restarting Apache and trying again.

---

### Post by ilSignorCarlo on 2011-09-25
> **Ryan Dwyer said:**
> Try restarting Apache and trying again.

ok, that was it : D
sorry and thanks.

---

