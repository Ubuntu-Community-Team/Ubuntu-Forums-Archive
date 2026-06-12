---
title: "Trouble updating fresh install of server 12.04LTS"
date: 2013-08-11
forum: Server Platforms
---

### Post by russ2 on 2013-08-11
I just performed a fresh install of my server and wanted to run updates before I reconfigured the server and I found this error on all of the updates.

		 		
[LIST=1]Now updating apache2 ..
 
    Installing package(s) with command apt-get -y install apache2 ..
 ```

    Reading package lists...
    Building dependency tree...
    Reading state information...
    The following extra packages will be installed:
      apache2-mpm-prefork apache2.2-bin apache2.2-common libapache2-mod-php5
      php5-cli php5-common php5-mysql
    Suggested packages:
      apache2-doc apache2-suexec apache2-suexec-custom php-pear php5-suhosin
    The following packages will be upgraded:
      apache2 apache2-mpm-prefork apache2.2-bin apache2.2-common
      libapache2-mod-php5 php5-cli php5-common php5-mysql
    8 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
    Need to get 8262 kB of archives.
    After this operation, 3072 B of additional disk space will be used.
    Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main apache2 amd64 2.2.22-1ubuntu1.4
      Temporary failure resolving 'us.archive.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apache2 amd64 2.2.22-1ubuntu1.4
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apache2-mpm-prefork amd64 2.2.22-1ubuntu1.4
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apache2.2-common amd64 2.2.22-1ubuntu1.4
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apache2.2-bin amd64 2.2.22-1ubuntu1.4
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main php5-cli amd64 5.3.10-1ubuntu3.7
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main php5-mysql amd64 5.3.10-1ubuntu3.7
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libapache2-mod-php5 amd64 5.3.10-1ubuntu3.7
      Temporary failure resolving 'security.ubuntu.com'
    Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main php5-common amd64 5.3.10-1ubuntu3.7
      Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.22-1ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.22-1ubuntu1.4_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.22-1ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.22-1ubuntu1.4_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-bin_2.2.22-1ubuntu1.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-bin_2.2.22-1ubuntu1.4_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.3.10-1ubuntu3.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.3.10-1ubuntu3.7_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.10-1ubuntu3.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.3.10-1ubuntu3.7_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.3.10-1ubuntu3.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.3.10-1ubuntu3.7_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    Failed to fetch  [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.3.10-1ubuntu3.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.3.10-1ubuntu3.7_amd64.deb)   Temporary failure resolving 'security.ubuntu.com'
    E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 
    .. install failed!

```
[/LIST]

 		

I am not sure what is going wrong with this fresh install.  Are the update links down for maintenance or may there be a different issue.
The reason for the fresh install was because I saw these errors and wanted to install fresh and they are still there.

---

### Post by chadk5utc on 2013-08-11
From my previous experience this is likely to be a network issue. Can you ping google.com or yahoo? Check that you have properly configured /etc/network/interfaces   is it static or dhcp? do you have gateway set? nameservers?

[http://ubuntuforums.org/showthread.php?t=2079328](http://ubuntuforums.org/showthread.php?t=2079328)

---

### Post by russ2 on 2013-08-11
I think i figured out where I went wrong.  I set up a static ip address for the server and I just figured out that the gateway ip address is not what I put in. 

That was an easy fix.:P:P:P:P:P:P:P:P

---

### Post by kpothi on 2013-08-14
Thanks for sharing what went wrong. If the issue is really resolved, please consider marking this thread as [solved](http://ubuntuforums.org/showthread.php?t=2151638). So that, other volunteers do not check on this thread.

---

