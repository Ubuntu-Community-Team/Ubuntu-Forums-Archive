---
title: "Cannot get ufw to function properly!"
date: 2011-01-01
forum: Security
---

### Post by zozza on 2011-01-01
Hello, 

I am trying to setup ufw and have the following situation. 

I start with ufw disabled.


sudo ufw enable
WARN: uid is 0 but '/' is owned by 1000
ERROR: problem running ufw-init

I now check with sudo ufw status:

WARN: uid is 0 but '/' is owned by 1000
Status: active

At this point I cannot use any internet features and have to do sudo ufw disable.

I check again using sudo ufw status and get:

WARN: uid is 0 but '/' is owned by 1000
Status: inactive

Now internet works.  How can I setup ufw to be on, be able to use the  internet, and not get these error messages (whether or not they are  related to having no connectivity when ufw is on). 

Thanks.

---

### Post by karthick87 on 2011-01-01
Have you checked your user id?Post the output of,

```
grep <yourusername> /etc/passwd
```

---

### Post by The Cog on 2011-01-01
This thread might help: [http://ubuntuforums.org/showthread.php?t=799487](http://ubuntuforums.org/showthread.php?t=799487)

Can you post the output of these two commands:
```
ls -ld /
ls -l /
```

---

### Post by zozza on 2011-01-02
Thanks for the assistance. 

My UID is 1000 as id confirms.

Also: from grep /etc/passwd

username:x:1000:1000:Username,,,:/home/username:/bin/bash

I see that / is owned by me (1000) not root (0):

ls -ld /

drwxr-xr-x 23 username username 4096 2010-12-30 18:13 /

ls -l / reveals all directories are owned by root except for media which is owned by username.

I did sudo chown root.root / and then ls -ld / reveals:

drwxr-xr-x 23 root root 4096 2010-12-30 18:13 /

Then I rebooted. 

I then ran sudo ufw enable and got:

ERROR: problem running ufw-init

sudo ufw status showed active but now I cannot get any connection like before.

So it looks as if the UID problem is solved - thanks guys - but not the ufw issue.

---

### Post by zozza on 2011-01-03
bump...

---

### Post by spynappels on 2011-01-03
Could it be that there is a problem with the init file and UFW defaults to blocking all INPUT and OUTPUT traffic?

Could you get a listing of all your firewall rules when UFW is active?

---

### Post by bodhi.zazen on 2011-01-03
> **zozza said:**
> bump...

You last post indicated it was working.

> **zozza said:**
> So it looks as if the UID problem is solved

So why the bump ?

My guess, from your other posts, is that you changed ownership and permission on your system files and this is difficult to repair and it is typically better to re-install.

---

