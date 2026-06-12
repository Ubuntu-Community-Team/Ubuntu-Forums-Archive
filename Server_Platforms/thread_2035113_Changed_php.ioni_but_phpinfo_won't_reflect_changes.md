---
title: "Changed php.ioni but phpinfo won't reflect changes"
date: 2012-07-29
forum: Server Platforms
---

### Post by Maheriano on 2012-07-29
I just installed Ubuntu server and I'm trying to upload a 50 MiB file into phpmyadmin. I changed both:
- upload_max_filesize
- post_max_size
to 80M but each time I load phpinfo it still says it's at 2M. How can I get this to change? I've restarted the Apache service and even rebooted the server itself, nothing works. The 2 files I changed are:
- /etc/php5/apache2/php.ini
- /etc/php5/cli/php.ini

Both files had both variables changed to 80M and apache2 was restarted and the server was rebooted. Loading phpinfo still shows it sitting at 2M. I don't get it, please help!

EDIT - I forgot to mention, when I load phpinfo I get this:
Loaded Configuration File	/etc/php5/apache2/php.ini

---

### Post by Maheriano on 2012-07-29
For some reason the first line in my php.ini file was> \[php] which was causing a syntax error and none of the following values were being loaded. I had to change it to > [php] and then it worked.

---

