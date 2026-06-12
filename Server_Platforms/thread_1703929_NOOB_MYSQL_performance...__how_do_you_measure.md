---
title: "NOOB: MYSQL performance...  how do you measure?"
date: 2011-03-09
forum: Server Platforms
---

### Post by aharown07 on 2011-03-09
Recently set up a webserver at Linode.
I've been reading alot about tuning the mysql, but other than hitting web pages and seeing how fast they load, how do I tell how well my tuning is working?

What numbers really tell you that and where do I see them?

---

### Post by wongo888 on 2011-03-09
You might try this tuning script for starts

[http://www.day32.com/MySQL/](http://www.day32.com/MySQL/)

You need to install 'bc':

```
$ sudo apt-get install bc
```

Then download and run it:

```
$ wget http://www.day32.com/MySQL/tuning-primer.sh
$ chmod 755 tuning-primer.sh
$ ./tuning-primer.sh
```

---

### Post by aharown07 on 2011-03-10
Thanks for that. I've already got that script though and have been using it.
What I don't know is what to look at to see what sort of performance result my tuning is producing.

Is avg. queries per second a good metric? Right now, it's all I know to look at.

---

