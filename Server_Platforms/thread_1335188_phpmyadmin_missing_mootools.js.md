---
title: "phpmyadmin: missing mootools.js"
date: 2009-11-23
forum: Server Platforms
---

### Post by greenshirt11 on 2009-11-23
Kubuntu 9.10; phpmyadmin-4:3.2.2.1-1

[not sure whether this is the place to report bugs; so i put it as a question: do others see the same on their system?]

The following error (multiple lines though) is reported in "/var/log/apache2/error.log":

```
File does not exist: /usr/share/phpmyadmin/js/mootools.js, referer: http://localhost/phpmyadmin/main.php?token=e6c0a1559c61090b67ac29fd9590d9f0
```

Looking at the files installed by the phpmyadmin package, indeed the mootools.js is not among them.

I didn't test phpmyadmin completely but it seems to work anyway.

---

### Post by cdenley on 2009-11-23
I don't use phpmyadmin, but this might prevent that error.
```

sudo ln -s /usr/share/javascript/mootools/mootools.js /usr/share/phpmyadmin/js/mootools.js

```

---

### Post by greenshirt11 on 2009-11-23
yes that works, thanks but it is not the right solution in the end is it? 
Is this only happening on my system or is it a general 'problem'?
And where should it be reported then?

regards,
F

---

### Post by cdenley on 2009-11-23
I glances at the package, and it looks like it does not create the path /usr/share/phpmyadmin/js/mootools.js. Apparently, mootools was just [recently added]("https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/456319") to the repos to meet a dependency for phpmyadmin. I think there should be a link such as the one you created provided by the package, but there isn't. I think it is a bug, but can't verify since I don't use phpmyadmin. Perhaps you should file a bug report.

[https://bugs.launchpad.net/ubuntu/+source/phpmyadmin](https://bugs.launchpad.net/ubuntu/+source/phpmyadmin)

---

### Post by greenshirt11 on 2009-11-24
thanks for the link. Filed it as bug:

[https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/487241]("https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/487241")

---

