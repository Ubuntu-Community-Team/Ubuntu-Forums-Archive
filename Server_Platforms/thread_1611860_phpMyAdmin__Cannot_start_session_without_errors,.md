---
title: "phpMyAdmin  Cannot start session without errors,"
date: 2010-11-02
forum: Server Platforms
---

### Post by mjfroggy on 2010-11-02
Hello,

My LAMP ubuntu server apparently just upgraded the php to PHP Version 5.2.10-2ubuntu6.5

I know am unable to login to my phpmyadmin  when I do try to login I get the below error message
phpMyAdmin -
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

so I found the below url
[http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/](http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/)

When I type in
ls -l /var/lib/php


I get many rows that say
-rw------- 1 root www-data 16838 201011002 0:58 session_ ... (and a bunch of leters and numbers)

I typed in and tried to run the below code
sudo chown -R root:myusername /var/lib/php/session

replacing myusername with www-data
and I seem not to have a session folder it all seems to be located in php5  I also don't have a php folder its php5  so I altered the code to
sudo chown -R root:myusername /var/lib/php5
and then I dont seem to get any error message but still not able to login to myphpadmin 

Any suggestions??
Thanks

---

### Post by needtoknow60 on 2010-11-28
> **mjfroggy said:**
> Hello,

My LAMP ubuntu server apparently just upgraded the php to PHP Version 5.2.10-2ubuntu6.5

I know am unable to login to my phpmyadmin  when I do try to login I get the below error message
phpMyAdmin -
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

so I found the below url
[http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/](http://www.electrictoolbox.com/phpmyadmin-cannot-start-session-without-errors/)

When I type in
ls -l /var/lib/php


I get many rows that say
-rw------- 1 root www-data 16838 201011002 0:58 session_ ... (and a bunch of leters and numbers)

I typed in and tried to run the below code
sudo chown -R root:myusername /var/lib/php/session

replacing myusername with www-data
and I seem not to have a session folder it all seems to be located in php5  I also don't have a php folder its php5  so I altered the code to
sudo chown -R root:myusername /var/lib/php5
and then I dont seem to get any error message but still not able to login to myphpadmin 

Any suggestions??
Thanks
I had the same problem and created a session directory under php5.  This seemed to solve the problem.

---

### Post by new_tolinux on 2010-11-28
> **mjfroggy said:**
> Any suggestions??
Thanks
Share the errors, since they tell me a lot more than your story does until yet.

---

