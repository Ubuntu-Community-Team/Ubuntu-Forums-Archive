---
title: "Bang! I can't run programmer in the background"
date: 2008-05-14
forum: Server Platforms
---

### Post by rollenc on 2008-05-14
I install Ubuntu in my server. 
I found I can't run command in the background.
There is my terminal output:

[INDENT]rollenc@ubuntu:~$ php tmp &
[1] 22639
rollenc@ubuntu:~$ 

[1]+  Stopped                 php tmp
rollenc@ubuntu:~$ bg
[1]+ php tmp &

[1]+  Stopped                 php tmp
rollenc@ubuntu:~$ bg
[1]+ php tmp &

[1]+  Stopped                 php tmp
rollenc@ubuntu:~$ fg
php tmp
49995000rollenc@ubuntu:~$[/INDENT]

I use '&' to run this program in the background, but it stopped, and bg is not my friend yet.

This server is a production server, I don't wanna an OS reinstall.

Thanks for any words.

---

### Post by dmizer on 2008-05-14
my understanding of your problem is limited, but you might be interested in learning about screen: [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

also, is there something in the logs indicating why php tmp is stopping?

---

### Post by rollenc on 2008-05-14
thanks for your post.

I checked out the /var/log/auth.log and /var/log/syslog, whice is updated after I excute the 'php tmp &', but nothing was found.
 
which log file I need to notice?

---

### Post by rollenc on 2008-05-15
I found this happened in my Ubuntu 8.04 desktop too.

---

### Post by dmizer on 2008-05-15
does it work at all, for a short time perhaps?

i really don't know exactly what you're trying to do, but maybe the syntax is just wrong?
```
php /tmp &
```

---

### Post by citium on 2009-03-11
[cant run php in background]

You can run php in the background with.

sh -cb 'php whatever.php &' > /dev/null

Php can also be run in the background with cron

Cheers,
lazycodo

---

