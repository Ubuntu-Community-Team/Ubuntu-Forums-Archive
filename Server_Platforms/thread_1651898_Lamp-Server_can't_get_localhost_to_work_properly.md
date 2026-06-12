---
title: "Lamp-Server: can't get localhost to work properly"
date: 2010-12-23
forum: Server Platforms
---

### Post by kukac67 on 2010-12-23
Hello everybody, I'm new to this forum!
To the problem...

I have Ubuntu 10.10 and i installed the lamp-server by typing:
```

sudo apt-get install lamp-server^

```everything seemed to work fine.
I created /home/user/public_html/
i did some stupid things to the apache2 files (/etc/apache2/) to try to change the location of localhost.
then i went to: [http://localhost/](http://localhost/)
it said:
403 forbidden
You don't have permission to access / on this server.
Apache/2.2.16 (Ubuntu) Server at localhost Port 80

I need help so this will work...
Yes there is something under /home/user/public_html/
it is index.html, and phpinfo.php

then i checked back again later and the folder (/etc/apache2/) is completely GONE! :o
what do I do?!?!!!?!?!?

---

### Post by slooow on 2010-12-23
How about
```
sudo apt-get purge lamp-server
```
and then reinstall it how you already did.
Not sure though if it works, since lamp-server is a meta-package.

---

### Post by kukac67 on 2010-12-23
i'll try tommorow and let you know what happens

i'm sorta sleepy...

---

### Post by kukac67 on 2010-12-24
ok,

so I tried:

```

sudo apt-get purge lamp-server^

```this is what I got:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libwrap0' for task 'lamp-server'
Note, selecting 'mysql-server-core-5.1' for task 'lamp-server'
Note, selecting 'mysql-client-core-5.1' for task 'lamp-server'
Note, selecting 'libmysqlclient16' for task 'lamp-server'
Note, selecting 'libdbi-perl' for task 'lamp-server'
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'apache2-mpm-prefork' for task 'lamp-server'
Note, selecting 'apache2.2-common' for task 'lamp-server'
Note, selecting 'apache2.2-bin' for task 'lamp-server'
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'libapr1' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'libaprutil1-dbd-sqlite3' for task 'lamp-server'
Note, selecting 'libaprutil1-ldap' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'libapache2-mod-php5' for task 'lamp-server'
Note, selecting 'php5-common' for task 'lamp-server'
Note, selecting 'php5-cli' for task 'lamp-server'
Note, selecting 'libdbd-mysql-perl' for task 'lamp-server'
Note, selecting 'libplrpc-perl' for task 'lamp-server'
Note, selecting 'libhtml-template-perl' for task 'lamp-server'
Note, selecting 'mysql-common' for task 'lamp-server'
Note, selecting 'libnet-daemon-perl' for task 'lamp-server'
Note, selecting 'tcpd' for task 'lamp-server'
Note, selecting 'mysql-client-5.1' for task 'lamp-server'
Note, selecting 'mysql-server-5.1' for task 'lamp-server'
Note, selecting 'php5-mysql' for task 'lamp-server'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2-mpm-prefork : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
 apache2.2-common : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
                    Depends: apache2-utils but it is not going to be installed
                    Recommends: ssl-cert but it is not going to be installed
E: Broken packages

```some ubuntu geek could help me...

/etc/apache2/   still doesn't exist...

i have no idea what to do...

---

### Post by Loan_Refi on 2010-12-24
to uninstall and purge lamp-server do this;

sudo apt-get remove --purge lamp-server

Your last command was missing "remove --purge"

---

### Post by kukac67 on 2010-12-24
ok,

So i tried:
```

sudo apt-get remove --purge lamp-server^

```

but again the same thing happened:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libwrap0' for task 'lamp-server'
Note, selecting 'mysql-server-core-5.1' for task 'lamp-server'
Note, selecting 'mysql-client-core-5.1' for task 'lamp-server'
Note, selecting 'libmysqlclient16' for task 'lamp-server'
Note, selecting 'libdbi-perl' for task 'lamp-server'
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'apache2-mpm-prefork' for task 'lamp-server'
Note, selecting 'apache2.2-common' for task 'lamp-server'
Note, selecting 'apache2.2-bin' for task 'lamp-server'
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'libapr1' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'libaprutil1-dbd-sqlite3' for task 'lamp-server'
Note, selecting 'libaprutil1-ldap' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'libapache2-mod-php5' for task 'lamp-server'
Note, selecting 'php5-common' for task 'lamp-server'
Note, selecting 'php5-cli' for task 'lamp-server'
Note, selecting 'libdbd-mysql-perl' for task 'lamp-server'
Note, selecting 'libplrpc-perl' for task 'lamp-server'
Note, selecting 'libhtml-template-perl' for task 'lamp-server'
Note, selecting 'mysql-common' for task 'lamp-server'
Note, selecting 'libnet-daemon-perl' for task 'lamp-server'
Note, selecting 'tcpd' for task 'lamp-server'
Note, selecting 'mysql-client-5.1' for task 'lamp-server'
Note, selecting 'mysql-server-5.1' for task 'lamp-server'
Note, selecting 'php5-mysql' for task 'lamp-server'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2-mpm-prefork : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
 apache2.2-common : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.1) but it is not going to be installed
                    Depends: apache2-utils but it is not going to be installed
                    Recommends: ssl-cert but it is not going to be installed
E: Broken packages

```

still don't know what to do...

---

### Post by Rusty au Lait on 2010-12-24
Not to add confusion to the situation. /etc/apache2 is gone completely? Before you purged it? Where did it go? Did you accidentally rename it? Anyway, can you reinstall lamp successfully? What is the "^" at the end of your command line?

---

### Post by kukac67 on 2010-12-24
yes, /etc/apache2/ is completely gone

not renamed or anything...

i don't know where it went

i can't reinstall lamp-server succesfully...

adding the "^" at the end was the only way i could install it in the first place (before it got jacked up)

---

### Post by felixoh on 2010-12-24
Hi,

why don't you get the latest version of apachefriends xampp?
Download it from [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html), extract it and just start it.

---

### Post by Vegan on 2010-12-24
If you want to use a LAMP stack, go download the server edition and use that.

Then you can install a desktop over that once you have the web appliances up.

You can also manage a server with a browser so a desktop is optional.

---

### Post by kukac67 on 2010-12-25
thanks everyone for the help but I'm probably gonna switch back to windows anyway because i have a wierd feeling about ubuntu

you see, when i first got involved in linux (ubuntu) i was excited because i heard all of these awesome things about it being user-friendly and unable to get viruses and it it so easy to learn to operate.

well...

i know all of these are true, but i never took the time to get to know linux and ubuntu, and windows is so familiar...

thanks anyway guys
ur awesome

i'm gonna mark this resolved or solved or whatever because if i did what you guys said my problem would probably be solved

bye

---

### Post by aceofspades686 on 2010-12-25
Its worth pointing out that installing a properly working apache2/mysql/php server is tricky regardless of the operating system.  On the offchance that you want to give it another try, I recommend this tutorial from howto forge:

[http://howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2](http://howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2)

---

### Post by CharlesA on 2010-12-25
Hiya,

I actually installed the LAMP stack on my Ubuntu Desktop box, by using:
```
sudo tasksel
```

Then selecting LAMP server.

It's worked fine outside of apache complaining when it was restarted due to the way Ubuntu Desktop sets up the /etc/hosts file.

---

### Post by kundancool on 2011-01-21
at last step do this or you will get 403 error   I think you didn't tried this    chmod -R 777 /var/www    This will solve yours as it solved mine

---

### Post by kundancool on 2011-01-21
I think you didn't tried this   chmod -R 777 /var/www   This will solve yours as it solved mine

---

### Post by CharlesA on 2011-01-21
> **kundancool said:**
> I think you didn't tried this   chmod -R 777 /var/www   This will solve yours as it solved mine

It is not a good idea to do that. You do not need 777 permissions on everything - that gives everyone read, write and execute permission.

At most you'd need 755 for directories and 644 for files.

---

### Post by boblogic on 2011-01-27
PROBLEM:
403 Forbidden
You don't have permission to access /server-info on this server.

SOLUTION:
Add "localhost.localdomain ${HOSTNAME}" to /etc/apache2/mods-available/info.conf
like so :
==>
<Location /server-info>
    SetHandler server-info
    Order deny,allow
    Deny from all
    Allow from localhost ip6-localhost [COLOR=Blue]localhost.localdomain ${HOSTNAME}[/COLOR]
#    Allow from .example.com
</Location>
<==

Then do (example): 
==>
root@Aries2:/etc/apache2# a2dismod info
Module info disabled.
Run '/etc/init.d/apache2 restart' to activate new configuration!
root@Aries2:/etc/apache2# a2enmod info
Enabling module info.
Run '/etc/init.d/apache2 restart' to activate new configuration!
root@Aries2:/etc/apache2# service apache2 restart
 * Restarting web server apache2
 ... waiting                                [ OK ]
root@Aries2:/etc/apache2# 
<==

for some reason, "localhost" needs to be "localhost.localdomain" on my Ubuntu (10.04).
I put in  "${HOSTNAME}" so that "http://Aries2/server-info will also work.
Don't mess with the file permissions.

And don't give up on Linux. It's worth the time in the long run.
Windows 8 will probably be cloud based and really out of your control.
Start learning Linux now !

---

