---
title: "Ubuntu 12.10 Apache server error 500"
date: 2013-01-18
forum: Server Platforms
---

### Post by fr1002 on 2013-01-18
Hello All,

I have recently set my laptop up with the newest version of Ubuntu 12.10. After doing so I started to set up Apache2 Php5 MySQL and PhpMyAdmin.

Now with that said I have done before in the past with no issues at all. So here is the problem.

The Apache server is working fine I can access it from 127 and localhost. Phpmyadmin is working correctly and I have tested the php info page to ensure that it is installed correctly.

I am getting this error after setting php.ini to have display_errors turned on.


**Fatal error**:  Call to a member function execute() on a non-object in **/var/www/test/models/config.php** on line **11**


I have searched the forum and many google searches to find a solution to this issue and this is what I have found and tried.

I have checked the error logs in apache2 and they are not displaying any errors when trying to run the pages.

I have made root the owner of /var/www/ where the pages are being hosted.[COLOR=Black]

Here is the line of code that is stated to be causing the fatal error.

$stmt->execute();

If you need any more info help me out let me know. As far as I can tell everything is setup correctly and i do not see where is the error is coming from.
[/COLOR]
Thanks,
Josh~

---

