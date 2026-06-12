---
title: "LAMP headache!"
date: 2006-08-13
forum: Server Platforms
---

### Post by drubulvr on 2006-08-13
So I have 6.06 installed.  Installed LAMP, all worked great!  Got a phptest page, using php5, apache2, lib$%##^%$^ whatever, the works!

So, not satisfied I thought...why not USE it as a server?  So I went to dyndns.org, got me ddclient, installed that... got my *.is-a-geek.com subdomain and VOILA!  it freaking worked.  I could see my index of/ from another computer on a browser!

Still not happy I wanted to then install Drupal.  It had my do some mysql commands and then everything broke.  Suddendly dyndns wouldn't update, even though it was on...

I reinstalled lamp, restarted sql, restarted everything.  I can see my localhost index.html page fine...but phpmyadmin, or anything else with php wont parse.

I'm so angry and frustrated.  I tried everything I found on google, from editing conf files, to libphp5.so and stuff.

Please, someone help me get my server going without a complete reinstall?

---

### Post by az on 2006-08-13
You do not need to edit any configuration files to get the LAMP stack working.  You do need to bump up the memory limit to run Drupal, though.


[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Since I don't know what you have edited, I don't know what to tell you to fix.

---

### Post by drubulvr on 2006-08-13
well, php parsing is the issue now.

how can I make sure php is set to parse in apache?

---

### Post by az on 2006-08-13
> **drubulvr said:**
> well, php parsing is the issue now.

how can I make sure php is set to parse in apache?

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031](https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031)

---

