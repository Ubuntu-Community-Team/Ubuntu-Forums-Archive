---
title: "cannot increase open files limit on Ubuntu 9.10 (goes down but not up)"
date: 2010-03-24
forum: Server Platforms
---

### Post by DigitalRonin on 2010-03-24
This is happening on Ubuntu 9.10 server

I'm trying to increase the number of open files allowed for a user. This is for an nginx webserver where the current limit of 1024 is not enough.

According to the posts I've found so far, I should be able to put lines into /etc/security/limits.conf like this;

```

* soft nofile 4096
* hard nofile 4096

```

...to increase the number of open files allowed for all users.

But, that's not working for me, and I think the problem is not related to that file.

For all users, the default limit is 1024, regardless of what is in /etc/security/limits.conf (I have been rebooting after changing that file)

```

$ ulimit -n
1024

```

Now, despite the entries in /etc/security/limits.conf I can't increase that;

```

$ ulimit -n 2048
-bash: ulimit: open files: cannot modify limit: Operation not permitted

```

The weird part is that I can change the limit *downwards*, but can't change it upwards - even to go back to a number which is below the original limit;

```

$ ulimit -n 800
$ ulimit -n
800

$ ulimit -n 900
-bash: ulimit: open files: cannot modify limit: Operation not permitted

```

As root, I can change that limit to whatever I want, up or down. It doesn't even seem to care about the supposedly system-wide limit in /proc/sys/fs/file-max

```

# cat /proc/sys/fs/file-max
188897

# ulimit -n 188898
# ulimit -n 
188898

```

So far, I haven't found any way to increase the open files limit for a non-root user, and I really don't want to be running my webserver as root.

Does anyone have any ideas?

David

---

### Post by Kieron on 2010-05-01
I'm facing the same problem and like you I've tried every fix I've found on google to no avail. Have you found a fix yet?
Kieron

---

### Post by Kieron on 2010-05-01
I figured it out bro.

You need to add this line to /etc/pam.d/common-session after doing the limits.conf

session required pam_limits.so

working fine for me now! :D

---

