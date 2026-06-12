---
title: "Why is php not in my /bin directory??"
date: 2009-01-24
forum: Server Platforms
---

### Post by kpm on 2009-01-24
Hi, I am working on configuring a Linode LAMP webserver using Ubuntu 8.10.  Php pages are running, but I'm having a problem using the drush module for a Drupal install and I think it has to do with PHP not appearing in the system path.  When I run the command "which php" there is no value returned.  If I search using "whereis php" no value is returned... However, if I search for php5 three directories are returned, but no bin directory:

/etc/php5
/usr/lib/php5
/usr/share/php5

I'm confused as to where the php executable is, and how to add it to the system path.  Also, I'm wondering why php is not appearing in the /bin/ directory, since all the info I have read on this so far instructs that php should be in the /bin/ directory.

---

### Post by Dr Small on 2009-01-24
If the Php files are working, there should be a php executable somewhere. I just ran the commands on my server and they are there:
```
drsmall@mycroft:~$ which php5
/usr/bin/php5
drsmall@mycroft:~$ whereis php5
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/X11R6/bin/php5 /usr/bin/X11/php5 /usr/share/php5 /usr/share/man/man1/php5.1.gz

```

---

### Post by kpm on 2009-01-25
> **Dr Small said:**
> If the Php files are working, there should be a php executable somewhere. I just ran the commands on my server and they are there:
```
drsmall@mycroft:~$ which php5
/usr/bin/php5
drsmall@mycroft:~$ whereis php5
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/X11R6/bin/php5 /usr/bin/X11/php5 /usr/share/php5 /usr/share/man/man1/php5.1.gz

```

Thanks for the help, on your system, is /usr/bin/php5 a symbolic link?  I'm wondering if I am just missing a link file or a complete directory somehow... My PHP pages are working fine, but trying to execute a .php file from the command line results in "/usr/bin/env: php: No such file or directory" and I'm wondering if my php installation is bad...

---

### Post by kpm on 2009-01-27
> **kpm said:**
> Thanks for the help, on your system, is /usr/bin/php5 a symbolic link?  I'm wondering if I am just missing a link file or a complete directory somehow... My PHP pages are working fine, but trying to execute a .php file from the command line results in "/usr/bin/env: php: No such file or directory" and I'm wondering if my php installation is bad...

Ahh, I had not installed php-cli... now all is well

---

### Post by anagallardo on 2009-03-05
I have the same problem, I'm working with Ubuntu 8.10 server + LAMP server + Symfony. I can probe symfony -T  in sandbox.

¿how do you resolve it? 

Thank you very much.

---

### Post by anagallardo on 2009-03-06
> **anagallardo said:**
> I have the same problem, I'm working with Ubuntu 8.10 server + LAMP server + Symfony. I can probe symfony -T  in sandbox.

¿how do you resolve it? 

Thank you very much.

Sorry, I really want to say **I can't probe symfony -T  in sandbox**

I got the next error

$ ./symfony -T
/usr/bin/env: php: No existe el fichero ó directorio


I install php5 (apt-get install php5)

$ dpkg -l | grep php
ii  libapache2-mod-php5                  5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php5                                 5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php5-common                          5.2.6-2ubuntu4.1                        Common files for packages built from the php
ii  php5-mysql                           5.2.6-2ubuntu4.1                        MySQL module for php5

but the problem persist:
$ sudo whereis php5
php5: /etc/php5 /usr/lib/php5 /usr/share/php5
$ sudo which php5


Thank you in advance.

---

### Post by anagallardo on 2009-03-09
I don't know what was the problem, but I resolve it doing:

[B]$ sudo apt-get update
$ sudo apt-get remove --purge php5
$ sudo apt-get install php5 php5-cli php5-cgi php5-dev
[/B]
[B]$ sudo which php5
/usr/bin/php5

/var/www/sf_sandbox$ ./symfony -T
[/B]available pake tasks:
  clear-cache                > clear cached information
  clear-controllers          > clear controllers
  disable                    > disables an application in a given environment
  downgrade                  > downgrade to a previous symfony release
  enable                     > enables an application in a given environment
  fix-perms                  > fix directories permissions
  freeze                     > freeze symfony libraries
  init-app                   > initialize a new symfony application
  init-batch                 > initialize a new symfony batch script
  init-controller            > initialize a new symfony controller script
  init-module                > initialize a new symfony module
  init-project               > initialize a new symfony project
  log-purge                  > purges an applications log files
  log-rotate                 > rotates an applications log files
  plugin-install             > install a new plugin
  plugin-list                > list installed plugins
  plugin-uninstall           > uninstall a plugin
  plugin-upgrade             > upgrade a plugin
  propel-build-all           > generate propel model and sql and initialize database
  propel-build-all-load      > generate propel model and sql and initialize database, and load data
  propel-build-db            > create database for current model
  propel-build-model         > create classes for current model
  propel-build-schema        > create a schema from existing database
  propel-build-sql           > create sql for current model
  propel-convert-xml-schema  > create schema.yml from schema.xml
  propel-convert-yml-schema  > create schema.xml from schema.yml
  propel-dump-data           > dump data to fixtures directory
  propel-generate-crud       > generate a new propel CRUD module
  propel-init-admin          > initialize a new propel admin module
  propel-init-crud           > initialize a new propel CRUD module
  propel-insert-sql          > insert sql for current model
  propel-load-data           > load data from fixtures directory
  sync                       > synchronise project with another machine
  test-all                   > launch all tests
  test-functional            > launch functional tests for an application
  test-unit                  > launch unit tests
  unfreeze                   > unfreeze symfony libraries
  upgrade                    > upgrade to a new symfony release

task aliases:
  app                        = pake init-app
  batch                      = pake init-batch
  cc                         = pake clear-cache
  controller                 = pake init-controller
  module                     = pake init-module
  new                        = pake init-project


:D

Now I can start working with Symfony.

---

### Post by 1jackjack on 2009-11-29
> **anagallardo said:**
> I don't know what was the problem

The problem was that you didn't have php5-cli installed. This is the command line interpreter for PHP (allows you to test PHP scrips from the shell).

Hope this saves someone some time...

---

