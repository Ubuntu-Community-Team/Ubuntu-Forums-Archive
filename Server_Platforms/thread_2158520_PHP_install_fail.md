---
title: "PHP install fail"
date: 2013-06-29
forum: Server Platforms
---

### Post by NuxNik on 2013-06-29
Hello,

Wanting to set up a Raspberry PI (running a  Debian Wheezy Distro), )as a web server. I decided to do my learning on a Lubuntu 13.04 box first. in part because this box is much faster.

I installed Lighttpd, mySQL, and PHP5 in that order (althogh mySQL seems to have already been on.
I used the following pages as guides
  ---http://elinux.org/RPi_webserver
  ---https://help.ubuntu.com/community/lighttpd
  ---http://www.penguintutor.com/linux/light-webserver
  ---https://www.linux.com/learn/docs/ldp/285394-installing-lighttpd-with-php5-on-ubuntu-910

All the pages end with create a small  test.php file in folder /var/www,  making a phpinfo() call.
And ALL of these pages assume that this will work when you try to run it on your designated serve
NONE go the next step and work on the premise that this does not work

I'm getting an 40 - Forbidden  error when I try 
     localhost/test.php or [serverhostname]/test.php
Even a Perl "hello World" file, test.pl gives the same error

Apparently the /var/www directory belongs to "root" and it won't let anyone else have access.

---

### Post by CharlesA on 2013-06-29
Check your permissions.

/var/www/ should have defaulted to root:root with rwx-rwx-r-x permissions.

---

### Post by sandyd on 2013-06-30
> **NuxNik said:**
> Hello,

Wanting to set up a Raspberry PI (running a  Debian Wheezy Distro), )as a web server. I decided to do my learning on a Lubuntu 13.04 box first. in part because this box is much faster.

I installed Lighttpd, mySQL, and PHP5 in that order (althogh mySQL seems to have already been on.
I used the following pages as guides
  ---http://elinux.org/RPi_webserver
  ---https://help.ubuntu.com/community/lighttpd
  ---http://www.penguintutor.com/linux/light-webserver
  ---https://www.linux.com/learn/docs/ldp/285394-installing-lighttpd-with-php5-on-ubuntu-910

All the pages end with create a small  test.php file in folder /var/www,  making a phpinfo() call.
And ALL of these pages assume that this will work when you try to run it on your designated serve
NONE go the next step and work on the premise that this does not work

I'm getting an 40 - Forbidden  error when I try 
     localhost/test.php or [serverhostname]/test.php
Even a Perl "hello World" file, test.pl gives the same error

Apparently the /var/www directory belongs to "root" and it won't let anyone else have access.
lighttpd (I think?) runs with the user www-data:www-data.

try something like
```

sudo chown -R www-data:www-data /var/www
```

If you want the settings to stick (i.e. even if you create files using another user there), do something like
```

sudo chmod -R 2770 /var/www
```
After running the chown command above to make the group 'sticky' (All files created under /var/www will always be owned by www-data). Its kind of handy, as when you create files there using the root account, the files are owned by root user and root group. The above forces the files to be owned by the root user and the "www-data" group.

---

### Post by NuxNik on 2013-07-07
Thank you

Sorry for the delayed response. But I was distracted by 2 National holidays in the past week.

---

### Post by NuxNik on 2013-07-10
> **sandyd said:**
> lighttpd (I think?) runs with the user www-data:www-data.

try something like
```

sudo chown -R www-data:www-data /var/www
```

If you want the settings to stick (i.e. even if you create files using another user there), do something like
```

sudo chmod -R 2770 /var/www
```
After running the chown command above to make the group 'sticky' (All files created under /var/www will always be owned by www-data). Its kind of handy, as when you create files there using the root account, the files are owned by root user and root group. The above forces the files to be owned by the root user and the "www-data" group.

------------------------------------

Thanks.
I've been distracted and this has fallen to nearly bottom of the todo pile

Hopefully, I can try this out ASAP..

Will adivse of results obtained.

---

### Post by NuxNik on 2013-07-12
Tried it
I worked.
Log into to my notes for future reference   :-)

---

