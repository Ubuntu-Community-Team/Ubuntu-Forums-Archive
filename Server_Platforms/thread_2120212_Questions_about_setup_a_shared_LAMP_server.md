---
title: "Questions about setup a shared LAMP server"
date: 2013-02-26
forum: Server Platforms
---

### Post by thego on 2013-02-26
Hello all,

I have a VPS running Ubuntu 12.04 Server that hosts 2 sites: example.com, test.com. One is mine, the other belongs to my friend.

Structure:

```

/home
      | example
                | public_html/
      | test 
                | public_html/

```

I setup suPHP for executing PHP scripts with the permissions of their owners. Everything was fine, but then I found out that the default permission of each user home directory is 755, all users can access to other users home directory and they can read the system fle too.

I can easily read config.php of test.com with script :

[PHP]<?php readfile('/home/test/public_html/config.php'); ?>[/PHP]

or

[PHP]<?php echo system('cat /home/test/public_html/config.php'); ?>[/PHP]

or system file 

[PHP]<?php echo system('cat /etc/apache2/sites-available/test.com'); ?>[/PHP]

[PHP]<?php echo system('cat /etc/apache2/httpd.conf'); ?>[/PHP]


My current solution is chmod the user home directory (/home/test/ , /home/example/) to 750.

The problem is user can also do the chmod 755 himself then the site is vulnerable again. Anyway, the system files /etc/apache ... has not been covered, they are still readable (I'm wondering if I should change its permissions or not).

I'm looking for another solution to solve this. Something like if user "test" chmod 777 or 755 all his files and folder, he is still protected from user "example". And both of them cannot access to system files.

Please help me !

---

