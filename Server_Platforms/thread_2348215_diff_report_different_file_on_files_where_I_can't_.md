---
title: "diff report different file on files where I can't see difference"
date: 2017-01-01
forum: Server Platforms
---

### Post by sed_faster on 2017-01-01
Hello folks,

I was run the software diff looking for the files different between different disks. The diff return a report with many situation where the file exist on two different disk but the report says "no such file or report"

I use this setup on software diff: 
```

sudo diff -ryq diskone disktwo

```

The file in question is this:
```

disk1
total 34
drwxrwxrwx 1 root root     0 May 30  2016 .
drwxrwxrwx 1 root root 32768 May 30  2016 ..
lrwxrwxrwx 1 root root    80 May 30  2016 gettext.inc -> ../../../php/php-gettext/gettext.inc
lrwxrwxrwx 1 root root    80 May 30  2016 gettext.php -> ../../../php/php-gettext/gettext.php
lrwxrwxrwx 1 root root    80 May 30  2016 streams.php -> ../../../php/php-gettext/streams.php


disk2
total 34
drwxrwxrwx 1 root root     0 May 30  2016 .
drwxrwxrwx 1 root root 32768 May 30  2016 ..
lrwxrwxrwx 1 root root    80 May 30  2016 gettext.inc -> ../../../php/php-gettext/gettext.inc
lrwxrwxrwx 1 root root    80 May 30  2016 gettext.php -> ../../../php/php-gettext/gettext.php
lrwxrwxrwx 1 root root    80 May 30  2016 streams.php -> ../../../php/php-gettext/streams.php

```

I ran this command on ubuntu server!
Whats happen?
thanks

---

