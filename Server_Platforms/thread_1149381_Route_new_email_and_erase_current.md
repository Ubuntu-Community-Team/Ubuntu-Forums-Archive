---
title: "Route new email and erase current"
date: 2009-05-05
forum: Server Platforms
---

### Post by m3bik on 2009-05-05
I have a crontab that accesses a php script on my server. The cronjob emails the root account after every job. How can I route mail to root to /dev/null? I've found a few tutorials on forwarding to /dev/null but I can't seem to get them to work on my server...

Thanks.

---

### Post by m3bik on 2009-05-05
Sorry, it's not addressed to root@server it's addressed to user@server but it's the user I use as root...

---

### Post by m3bik on 2009-05-05
Still no luck...

---

### Post by m3bik on 2009-05-05
I've tried editing the alias file, /etc/aliases and added:

> user: /dev/null

Restarted the server. The user account still gets mail...

---

### Post by m3bik on 2009-05-05
I've tried creating a symlink from /var/mail/user to /dev/null and that still doesn't work! The server renames the symlink to something crazy and creates /var/mail/user again.

---

### Post by Dr Small on 2009-05-05
To redirect stdout to /dev/null, you append this to the end of your crontab command:
```
> /dev/null
```

To send both stdout and stderr to /dev/null, you would use this:
```
> /dev/null &> /dev/null
```

Dr Small

---

### Post by m3bik on 2009-05-05
I've added that, and I still get an email...

---

### Post by Dr Small on 2009-05-05
> **m3bik said:**
> You come in and make it soo easy.... Thanks!!
So, did that solve your problem? :)

---

### Post by m3bik on 2009-05-05
> **Dr Small said:**
> So, did that solve your problem? :)

No, that response was premature... My bad. I still get emails sent to the user account after every cronjob...

---

### Post by m3bik on 2009-05-06
I've started a new topic as my plan to fix this has changed...

See - [http://ubuntuforums.org/showthread.php?p=7223188](http://ubuntuforums.org/showthread.php?p=7223188)

---

