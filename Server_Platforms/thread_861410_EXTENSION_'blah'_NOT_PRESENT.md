---
title: "EXTENSION 'blah' NOT PRESENT"
date: 2008-07-16
forum: Server Platforms
---

### Post by wjrhee77 on 2008-07-16
Hello all.

I have a php script that I run everynight and give me this error :

Extension '/usr/local/scripts/lockmyadmin.php' not present.

This is what lockmyadmin.php script looks alike :

[PHP]#!/usr/bin/php -q

<?php

shell_exec("chmod 770 /var/www/afc/webdocs/afc_admin/phpmyadmin");

?>
[/PHP]

When I run this php script from shell prompt, 
```
root@new:/# php /usr/local/scripts/lockmyadmin.php
```, it works fine.

But only when I run it as cron job, it give me error of "EXTENSION '/usr/local/scripts/lockmyadmin.php' NOT PRESENT."

I am running Ubuntu 7.10 Gutsy.

Thanks & HELP!

---

### Post by cdenley on 2008-07-16
> **wjrhee77 said:**
> Hello all.

I have a php script that I run everynight and give me this error :

Extension '/usr/local/scripts/lockmyadmin.php' not present.

This is what lockmyadmin.php script looks alike :

[PHP]#!/usr/bin/php -q

<?php

shell_exec("chmod 770 /var/www/afc/webdocs/afc_admin/phpmyadmin");

?>
[/PHP]

When I run this php script from shell prompt, 
```
root@new:/# php /usr/local/scripts/lockmyadmin.php
```, it works fine.

But only when I run it as cron job, it give me error of "EXTENSION '/usr/local/scripts/lockmyadmin.php' NOT PRESENT."

I am running Ubuntu 7.10 Gutsy.

Thanks & HELP!

Post this output of these commands
```

ls -l /usr/local/scripts/lockmyadmin.php
/usr/local/scripts/lockmyadmin.php

```

Or does your cron entry look like "php /usr/local/scripts/lockmyadmin.php"? If so, change it to "/usr/bin/php /usr/local/scripts/lockmyadmin.php".

---

### Post by wjrhee77 on 2008-07-16
No, cron look like this : 
```
# 5:15 PM close phpmyadmin directory from public
37 11 * * *     root    /usr/local/scripts/lockmyadmin.php >> /tmp/backup/crond.log 2>&1

```

The output of ls -l is : 
```
root@new:/# ls -l /usr/local/scripts/lockmyadmin.php

-rwxrwxr-x 1 root root 123 2008-07-16 11:36 /usr/local/scripts/lockmyadmin.php

```

The output of /usr/local/scripts/lockmyadmin.php :
```
root@new:/# /usr/local/scripts/lockmyadmin.php
Extension '/usr/local/scripts/lockmyadmin.php' not present.

```

Thank you.

I changed the cron job to :

37 11 * * *     root    **php** /usr/local/scripts/lockmyadmin.php >> /tmp/backup/crond.log 2>&1

and works great.

---

### Post by MeccaOz on 2010-03-17
I just had the same problem and thought i'd post my fix.
Im using debian 5.0 but that shouldnt matter.
My problem it seemed was due to the line endings. I had downloaded these files to a windows box and edited them so the pages were using DOS endings not Unix endings and creating the error. Simply I used Ultredit and its convertor to go DOS->Unix line endings, and now she works :)

Hope this helps

---

### Post by bibby on 2010-10-14
I found this thread because I encountered the same message as in the title, although unlike the poster, the script did not run right as root.

Like the commenter above me, though,  dos2unix fixed the issue

---

