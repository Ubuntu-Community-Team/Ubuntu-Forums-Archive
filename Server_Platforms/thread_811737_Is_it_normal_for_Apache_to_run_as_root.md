---
title: "Is it normal for Apache to run as root?"
date: 2008-05-29
forum: Server Platforms
---

### Post by madu on 2008-05-29
Hi,

This is the first time I'm running Apache (or any web server for that matter) and am just worried about a few things...

First is that I dont see a new user created (in Users and Groups) for running apache.. is that normal?
and then, I see apache running as root;
> madu@Dell:~$ ps aux | grep apache
**root      9458  0.0  0.1  10468  2628 ?        Ss   May29   0:00 /usr/sbin/apache2 -k start**
www-data  9459  0.0  0.0  10240  1792 ?        S    May29   0:00 /usr/sbin/apache2 -k start
www-data  9463  0.0  0.1 231804  2912 ?        Sl   May29   0:00 /usr/sbin/apache2 -k start
www-data  9466  0.0  0.1 231804  2412 ?        Sl   May29   0:00 /usr/sbin/apache2 -k start
madu     11407  0.0  0.0   3008   772 pts/2    S+   00:20   0:00 grep apache


Is that OK?
Isn't the process supposed to kill itself?

Thank you.

---

### Post by cmnorton on 2008-05-29
Yes.

And there's a lot of folklore as to why. I just cannot remember it right now.

---

### Post by spiderbatdad on 2008-05-29
Apache is root owned but running in userspace.
[http://www.faqs.org/docs/securing/chap29sec254.html](http://www.faqs.org/docs/securing/chap29sec254.html)
There are other guides, as well, and it probably takes reading several.
Also see debootstrapping if interested.
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

---

### Post by Joeb454 on 2008-05-29
I've never had any issues with my apache configuration on my server :)

---

### Post by madu on 2008-05-29
Thank you heaps for the replies mates.
So everything is fine then I guess.

Cheers!

---

