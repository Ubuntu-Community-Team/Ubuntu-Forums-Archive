---
title: "proftpd can not login problem and work around"
date: 2006-11-01
forum: Server Platforms
---

### Post by lkz on 2006-11-01
I'm running Edgy Eft and I am experiencing a problem with proftpd I found a workaround for myself, however I would like to avoid the issue all together.

The problem is that the first time I try to login to the ftp after boot, I get "Password Incorrect". 

The solution I found was to click "Deactivate" and then "Activate" in gproftpd (the configuration tool) and now I am able to login. 

It seems the user authentication is not running correctly from the beginning.

Does any one have any suggestions?

---

### Post by DannyG on 2006-11-01
Did you try and Login with root, when you got password incorrent?

---

### Post by lkz on 2006-11-01
> **DannyG said:**
> Did you try and Login with root, when you got password incorrent?

I'm not sure I understand what you mean and how this helps, are you asking if I tried to login to the Ubuntu as root?

I dugg a little deeper and found this in /var/log/secure (proftpd log)

```

Nov 01 10:27:18 zen proftpd[5471] localhost.localdomain (::ffff:192.168.0.1[::ffff:192.168.0.1]): PAM(test): Authentication failure.
Nov 01 10:27:18 zen proftpd[5471] localhost.localdomain (::ffff:192.168.0.1[::ffff:192.168.0.1]): USER test (Login failed): Incorrect password.

```

After the Deactive/Active fix :

```

Nov 01 10:43:50 zen proftpd[4812] localhost.localdomain (::ffff:192.168.0.1[::ffff:192.168.0.1]): ANON test: Login successful.

```

It seems that PAM is not running correctly from startup, I've searched around the net and I was unable to find any solution to this.

---

### Post by Legnet on 2006-11-15
I did have the same problem as describe in this post.
What I did find out was that gproftpd did use /etc/proftpd.conf when proftpd use /etc/proftpd/proftpd.conf

I have so far not figure out how to tell gproftpd to use the same conf file, but when I copy the conf info from gproftpd to the /etc/proftpd/proftpd.conf login worked as it should after restart.

---

