---
title: "Errors when installing LAMP"
date: 2014-02-05
forum: Server Platforms
---

### Post by Andrew_Greer on 2014-02-05
Hello, I have searched the web for a solution and haven't found one that has worked for me.

The error that I am getting is aptitude failed (100), which only happens when installing MySQL. 

Yes, I have tried sudo apt-get update. Yes, I have removed the /var/lib/mysql files. Any ideas?

---

### Post by fdrake on 2014-02-05
did you see this one :[http://ubuntuforums.org/showthread.php?t=1582441](http://ubuntuforums.org/showthread.php?t=1582441)

and also this [http://askubuntu.com/questions/185645/why-does-tasksel-give-an-aptitude-failed-error](http://askubuntu.com/questions/185645/why-does-tasksel-give-an-aptitude-failed-error)

---

### Post by Andrew_Greer on 2014-02-05
Yep, I already tried both of those.

---

### Post by Andrew_Greer on 2014-02-11
No luck.. Should I just reinstall completely?

---

### Post by steeldriver on 2014-02-11
Have you tried installing via apt-get instead of tasksel?

```
sudo apt-get install mysql-server
```

---

