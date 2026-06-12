---
title: "Restart Apache and Kill All Sub Processes"
date: 2010-08-10
forum: Server Platforms
---

### Post by joshpennington on 2010-08-10
I am trying to restart Apache on my server but it does not seem to kill all the processes that Apache is currently running.

The command I am using is

sudo /etc/init.d/apache2 restart

Is there something else I should be doing that will kill all the child processes too?

Thanks

Josh Pennington

---

### Post by Ryan Dwyer on 2010-08-10
Really? Works for me.

```

ryan@ryan-pc:~$ ps -e | grep apache
 1196 ?        00:00:04 apache2
 6372 ?        00:00:00 apache2
 6373 ?        00:00:00 apache2
 6374 ?        00:00:00 apache2
 6375 ?        00:00:00 apache2
 6376 ?        00:00:00 apache2
 6378 ?        00:00:00 apache2
 6508 ?        00:00:00 apache2
 6838 ?        00:00:00 apache2
ryan@ryan-pc:~$ sudo /etc/init.d/apache2 restart
[sudo] password for ryan: 
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
ryan@ryan-pc:~$ ps -e | grep apache
 9239 ?        00:00:00 apache2
 9242 ?        00:00:00 apache2
 9243 ?        00:00:00 apache2
 9244 ?        00:00:00 apache2
 9245 ?        00:00:00 apache2
 9246 ?        00:00:00 apache2
ryan@ryan-pc:~$ 

```

They all have new process IDs.

---

### Post by joshpennington on 2010-08-10
Yes you are correct.

The reason I assumed they were not killing the processes was because each Apache process was taking up about the same amount of memory as they were before Apache was closed.

Do you know if this is normal?

---

### Post by Vegan on 2010-08-10
depending on the load there can be a few instanced of apache running

they come and go as needed

---

### Post by Ryan Dwyer on 2010-08-10
By default Apache starts 5 workers and creates more if needed. Each one servces 100 or so requests before being killed and replaced, so they tend to keep similar memory usage.

---

### Post by joshpennington on 2010-08-10
Ok this makes a lot more sense to me now.

Thanks all!

Josh Pennington

---

