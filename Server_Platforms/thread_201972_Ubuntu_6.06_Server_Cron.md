---
title: "Ubuntu 6.06 Server Cron"
date: 2006-06-22
forum: Server Platforms
---

### Post by sparty2809 on 2006-06-22
I have installed the ubuntu server.  I try to run a cron job and nothing happens.

crontab -e
1 * * * * echo "Test" >> /tmp/test

---

### Post by jvl on 2006-06-22
Run specified command one minute after full hour.

What you probably meant is:
```
*/1 * * * * echo "Test" >> /tmp/test
```

You could check if your crond is running as well.

---

### Post by sparty2809 on 2006-06-22
I have it start at startup.  It just doesn't run.

---

### Post by lamego on 2006-06-22
Did you understood from the post from jvl that your line will only run that command at the minute 1 of each hour ?

---

### Post by sparty2809 on 2006-06-22
Yes, I understood that.  No matter what time I put, it won't run.

---

### Post by herald on 2006-06-23
once you've run the crontab -e can you see it with crontab -l?

---

### Post by jvl on 2006-06-23
If you've got mail subsystem running, the cron errors will be mailed to the crontab owner.

what does
```
ps -ef | grep -i cron
```
say? 

as said earlier, what's the output of 
```
crontab -l
``` ?

---

### Post by Endwin on 2006-06-23
One thing I have noticed is you have to have the ABSOLUTE path to any command, including system commands. 

So I think you want...

```
*/1 * * * * /bin/echo "Test" >> /tmp/test
```

Conversely for testing try it with...
```
* * * * * /bin/echo "Test" >> /tmp/test
```
Which should run whatever you are testing whenever cron runs.

Hope it helps!

---

### Post by sparty2809 on 2006-06-23
When I do
```
ps -ef | grep -i cron
```

I get

```

root  5920   1        0   June 22 ?     00:00:00 /usr/sbin/cron
user  6865   6535  9  06:58  tty1   00:00:00  grep -i cron

```

When I do
```

sudo -l

```

I get

```

*/1 * * * * /bin/echo "Test" >> /tmp/test

```

---

### Post by sparty2809 on 2006-06-23
Nevermind, I realized when I installed it, it didn't put the right time.  Changed it to the correct time, and it worked.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

