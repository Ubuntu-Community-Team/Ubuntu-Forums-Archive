---
title: "What is yuntu3?"
date: 2009-05-31
forum: Security
---

### Post by fuwkej on 2009-05-31
In my log, I keep seeing the following types of entries:

03:05:27 yuntu3: restart.
03:06:34 yuntu3: restart.

I googled yuntu3, and there was only one direct match for yuntu3, and it links to a site in Chinese, and google warns that "This site may harm your computer."

Is yuntu3 malicious? anyone?

---

### Post by whoop on 2009-05-31
never heard of it... 
is it a daemon running on your machine?
check in /etc/init.d

is it a process running? check top

---

### Post by fuwkej on 2009-05-31
Nope, doesn't appear to be running. It pops up from time to time, but I'm not sure why.

No daemon named yuntu3 in /etc/init.d and no process running by that name either.

---

### Post by whoop on 2009-05-31
> **laverabe said:**
> Nope, doesn't appear to be running. It pops up from time to time, but I'm not sure why.

No daemon named yuntu3 in /etc/init.d and no process running by that name either.

sudo find / -name yuntu3

---

### Post by fuwkej on 2009-05-31
no results

---

### Post by Agent ME on 2009-05-31
> **whoop said:**
> sudo find / -name yuntu3
Try 
```
sudo find / -iname "*yuntu*"
```
instead.

---

### Post by cariboo on 2009-06-01
Do you get a process id when you run:

```
ps ax | grep yuntu3
```

---

### Post by fuwkej on 2009-06-01
No results with the find function

There is a process running, here is the results:

```
$ ps ax | grep yuntu3
 9513 pts/0    R+     0:00 grep yuntu3
```

Thanks for helping

---

### Post by brian_p on 2009-06-02
> **laverabe said:**
> 

There is a process running, here is the results:

```
$ ps ax | grep yuntu3
 9513 pts/0    R+     0:00 grep yuntu3
```

That is an entry for the **grep process**.

My search for yuntu3 on Google gives eight hits. You are at the the top. The others appear to be of little interest. In which log did you find it mentioned? Is it still there? May we see the command you used to view it and **all** the information given?

---

### Post by fuwkej on 2009-06-03
A google search of "yuntu3" in quotes, prior to this thread, only showed the chinese link which google says is an attack site.

The entry appeared in conky, which reads /var/log/messages .

I opened the log file directly, and searched for yuntu and could not find any entries. I came across these:


```
May 31 03:05:27 desktop syslogd 1.5.0#5ubuntu3: restart.
May 31 03:06:34 desktop syslogd 1.5.0#5ubuntu3: restart.
```It looks like conky was cutting off the first part of those lines and adding a y.. i have no idea why. Thanks for the help, I just wish I would have checked that sooner.

---

