---
title: "Phpmyadmin: &quot;cannot load mcrypt extension&quot; on Hardy"
date: 2008-04-29
forum: Server Platforms
---

### Post by tubezninja on 2008-04-29
Hi folks,

I was wondering if anyone else on Hardy was experiencing an issue where they get the following error message when logged into phpMyAdmin:

"Cannot load mcrypt extension.  Please check your PHP configuration."

Doing some searching, I [found this thread from January]("http://ubuntuforums.org/showthread.php?t=653434").  However, the solution doesn't appear to be so simple for me.  When I try a "sudo apt-get install php5-mcrypt, " I get:

"php5-mcrypt is already the newest version"

Indicating it's already there.

I'm having the same issue in both 32-bit and 64-bit distros of 8.04 server with the LAMP package.

FWIW, mcrypt isn't mentioned anywhere in my php.ini.  Should I add it?  And what line should I use?

If anyone has a smilar problem or can shed some insight into how to get this to work, I'd be really greatful. :)

---

### Post by uboss on 2008-05-10
I´m having the same problem and can´t seem to find the solution.

---

### Post by tubezninja on 2008-05-10
I solved the problem in my setup:

```
sudo apt-get purge php5-mcrypt phpmyadmin
sudo apt-get install php5-mcrypt phpmyadmin
```

For whatever reason, purging both packages and then reinstalling them solved the issue for me.  *shrug*

---

### Post by shafi on 2008-05-11
Dear all, i have face to a problme, I have installed php5 and apache server on my laptop but i am not able to test my installed php, means the localhost works, but when i want to run test.php it just print the content of the test.php as follow:
 
    [http://localhost/test.php](http://localhost/test.php)

< ?php phpinfo(); ?> 

I have used the following link for installing php5 and apache2:

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

i dont konw how to solve this problem

whe i restart my apache server i get the following error:
```

** sudo /etc/init.d/apache2 restart**
 * Restarting web server apache2                                                [Sun May 11 16:22:23 2008] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Sun May 11 16:22:33 2008] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]



```
if any one could help me please ??

---

### Post by shafi on 2008-05-11
I forgot to say: I am using ubuntu hardy!

---

### Post by ddemerre on 2008-12-29
L.S.,
hi Shafi,
This problem of yours has hardly anything to do with the - original - subject of the thread (about the mcrypt in php).
Allow me to reply with a quick possible solution:
[list][*] The error-messages of your apache are actually warnings about the fact that your apache installation is not completely configured.  For solutions and extra explanation: check out [http://ubuntuforums.org/showthread.php?t=296155](http://ubuntuforums.org/showthread.php?t=296155)
[*] your problem with test.php that returns the actual contents of test.php instead of the result of execution, this indicates that OR your php is not installed on this apache, or not activated, or not linked to .php files, or your directory has restrictions to executing .php's...
[list][*] check whether apache-php module is installed (check output of):
$ dpkg -l |grep -e '.*apache.*php[0-9]*'
[*] check on presence of files /etc/apache2/mods-available/php*
[*] check on enableing: /etc/apache2/mods-enabled/php*
  here links should be present to ../mods-available/php*
[/list][/list]

---

