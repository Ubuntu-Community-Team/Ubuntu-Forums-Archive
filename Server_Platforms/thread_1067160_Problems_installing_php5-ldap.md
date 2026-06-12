---
title: "Problems installing php5-ldap"
date: 2009-02-11
forum: Server Platforms
---

### Post by Bockbertil on 2009-02-11
Hi, I'm running Ubuntu 8.04 on a server and I've run into some sort of problem that I can't figure out. Until recently my server was running Ubuntu 6.06 drapper, but I decided that I was time to upgrade it to 8.04 instead. I haven't been reading the change logs, but I do suspect that there might be quite a few security updates (amongst other things) in the 8.04. Thus this seemed to be a good idea. However after upgrading I can't run php from the command line. I'm using it in crontab so thats why I need this, case you was wondering. 

When I try to run "php" form the terminal it states that PHP couldn't load because 2 dynamic libraries are missing. One being php5-ldap and the other being sybase_ct. 

Complete error message when trying to start PHP:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/ldap.so' - /usr/lib/php5/20060613+lfs/ldap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sybase_ct.so' - /usr/lib/php5/20060613+lfs/sybase_ct.so: cannot open shared object file: No such file or directory in Unknown on line 0

So what the above basically says is that ldap & sybase_ct aren't installed, yet php tries to load them. So I could simply comment out the extensions in my php.ini file, but I kinda need these them. So I tried to installed php5-ldap using the following command and then i received the error below.

sudo apt-get install php5-ldap

Some packages could not be installed ...
...
The following packages have unmet dependencies:
  php5-ldap: Depends: php5-common (= 5.2.4-2ubuntu5) but 5.2.5-0.dotdeb.2 is to be installed
E: Broken packages

Running sudo apt-get install php5-common doesn't help though. It claims I have the latest available version installed. I can't find much about this at all, and I'm not sure what errors to relate to in this situation. Any help is appreciated, and thanks for your interest :)

---

### Post by Bockbertil on 2009-02-11
Found the answers to my question in this thread [http://ubuntuforums.org/showthread.php?t=321156]("http://ubuntuforums.org/showthread.php?t=321156"). Turns out I had the latest version php5-common, the latest and unapproved version. I've downgrade my php5-common to 5.2.4-2ubuntu5 and now it's working again :D. If anyone else has a similar issue, make sure your repository list is pointing to *restricted*, not *multiuniverse*. As I understand it multiuniverse holds unapproved updates?

php5-ldap: Depends: php5-common (= 5.2.4-2ubuntu5) but 5.2.5-0.dotdeb.2 **is to be installed**
It should have said "is installed". would have been a lot clearer :/

---

