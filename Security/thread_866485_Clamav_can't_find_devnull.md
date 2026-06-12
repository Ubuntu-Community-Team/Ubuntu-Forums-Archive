---
title: "Clamav can't find /dev/null"
date: 2008-07-21
forum: Security
---

### Post by fowie on 2008-07-21
Clamav has stopped working.  When I try
```

sudo /etc/init.d/clamav-daemon

```
I get:
```

 * Starting ClamAV daemon clamd                                                                                  Can't open /dev/null
ERROR: daemonize() failed

```
help?

---

### Post by ad_267 on 2008-07-21
Why do you say it can't find /dev/null?

---

### Post by fowie on 2008-07-24
See the message:
```

 * Starting ClamAV daemon 
clamd
Can't open /dev/null
ERROR: daemonize() failed

```

---

### Post by ad_267 on 2008-07-25
Oh sorry, didn't scroll across to see that.

Can you post the output of "ls -l /dev/null"

---

### Post by Nicovdd on 2010-01-05
Hi,

I'm having the same problem.

ls -l /dev/null gives 

crw-rw---- 1 root root 1, 3 Dec  9 15:52 /dev/null

Where to from here?

---

### Post by ad_267 on 2010-01-05
/dev/null should be readable and writeable for all users. I'm not sure how it would have changed. Try running this:
```
sudo chmod a+w /dev/null
sudo chmod a+r /dev/null
```

---

