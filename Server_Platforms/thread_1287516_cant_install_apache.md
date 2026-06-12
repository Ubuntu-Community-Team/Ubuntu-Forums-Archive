---
title: "cant install apache"
date: 2009-10-10
forum: Server Platforms
---

### Post by kpholmes on 2009-10-10
im having trouble installing apache. its driving me insane.




[majorelle-blue /var] aptitude install apache2 apache2-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  apache2-mpm-prefork libapache2-mod-php5 
The following partially installed packages will be configured:
  apache2 php5 phpmyadmin 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2.2-common but it is not installable
  apache2-mpm-prefork: Depends: apache2.2-common (= 2.2.9-10+lenny4) but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
apache2.2-common [2.2.9-10+lenny4 (stable, stable)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  apache2.2-common{a} 
The following partially installed packages will be configured:
  apache2 apache2-mpm-prefork libapache2-mod-php5 php5 phpmyadmin 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/814kB of archives. After unpacking 3518kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 36411 files and directories currently installed.)
Unpacking apache2.2-common (from .../apache2.2-common_2.2.9-10+lenny4_amd64.deb) ...
**dpkg: error processing** /var/cache/apt/archives/apache2.2-common_2.2.9-10+lenny4_amd64.deb (--unpack):
 trying to overwrite `/var/www', which is also in package munin
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2.2-common_2.2.9-10+lenny4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
[B]dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common[/B] (= 2.2.9-10+lenny4); however:
  Package apache2.2-common is not installed.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (>= 2.2.9-10+lenny4) | apache2-mpm-prefork (>= 2.2.9-10+lenny4) | apache2-mpm-event (>= 2.2.9-10+lenny4); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not installed.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.6.dfsg.1-1+lenny3) | libapache2-mod-php5filter (>= 5.2.6.dfsg.1-1+lenny3) | php5-cgi (>= 5.2.6.dfsg.1-1+lenny3); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on libapache2-mod-php5 | libapache-mod-php5 | php5-cgi | php5 | libapache2-mod-php4 | libapache-mod-php4 | php4 | php4-cgi; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache-mod-php5 is not installed.
  Package php5-cgi is not installed.
  Package php5 is not configured yet.
  Package libapache2-mod-php4 is not installed.
  Package libapache-mod-php4 is not installed.
  Package php4 is not installed.
  Package php4-cgi is not installed.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2-mpm-prefork
 apache2
 libapache2-mod-php5
 php5
 phpmyadmin
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

right in the area i highlighted is a bunch of errors.
i dont understand what its trying to tell me

---

### Post by GuyCorngood on 2009-10-10
The important bit is right here:

```
Unpacking apache2.2-common (from .../apache2.2-common_2.2.9-10+lenny4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.9-10+lenny4_amd64.deb (--unpack):
**trying to overwrite `/var/www', which is also in package munin**

```

Both apache2.2-common and munin claim ownership of the /var/www directory. This is a bug in the munin package, so run 'ubuntu-bug munin' and follow the directions.

---

### Post by DC^ on 2009-10-10
Do you have done an clear install of the OS and than you have tried to install Apache ?

---

### Post by kpholmes on 2009-10-10
its a dedicated server and im using ssh to manage it, so i cant physically see it, or do a clean install, i think  its somewhere if france. 

i was on the debian forums and someone else mentioned munin, should i try to re-install it?

thanks for the help with this debian box, 
even though were on the ubuntu forums, its much appreciated
:P:P


is it possible and safe to remove munin?
would i want to do something like that?

or

would it be better to edit the munin.conf file and take it off the /var/www/ directory ?

---

### Post by GuyCorngood on 2009-10-10
If you don't use munin, you should try uninstalling it. Changing the configuration wouldn't help, it's an issue with the package itself.

---

### Post by kpholmes on 2009-10-11
> **GuyCorngood said:**
> If you don't use munin, you should try uninstalling it. Changing the configuration wouldn't help, it's an issue with the package itself.

i tried and got this

[majorelle-blue ~] apt-get --purge munin
E: Invalid operation munin
[majorelle-blue ~] dpkg --purge munin
(Reading database ... 36418 files and directories currently installed.)
Removing munin ...
Purging configuration files for munin ...
The generated web site or accumulated data won't be removed.
Processing triggers for man-db ...
[majorelle-blue ~] dpkg --purge munin-node
(Reading database ... 36374 files and directories currently installed.)
Removing munin-node ...
Stopping Munin-Node: done.
Purging configuration files for munin-node ...
dpkg - warning: while removing munin-node, directory `/var/lib/munin' not empty so not removed.
Processing triggers for man-db ...
[majorelle-blue ~] 


what am i doing wrong?

---

### Post by GuyCorngood on 2009-10-11
> **kpholmes said:**
> i tried and got this

<snip>

what am i doing wrong?

Nothing, as far as I can see. In the first command you used the wrong syntax for apt-get (it should be apt-get --purge **remove** munin), but you then successfully used dpkg to uninstall munin and munin-node. Run 'dpkg -s munin munin-node' if you'd like to check.

You should be able to install Apache now.

---

### Post by kpholmes on 2009-10-11
> **GuyCorngood said:**
> Nothing, as far as I can see. In the first command you used the wrong syntax for apt-get (it should be apt-get --purge **remove** munin), but you then successfully used dpkg to uninstall munin and munin-node. Run 'dpkg -s munin munin-node' if you'd like to check.

You should be able to install Apache now.

sweet! ya you were right.

thanks!

---

