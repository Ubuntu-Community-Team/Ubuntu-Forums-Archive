---
title: "Script to install MySQL Server distribution on Ubuntu Server"
date: 2012-03-01
forum: Server Platforms
---

### Post by VanJr on 2012-03-01
I have written a script that we use to install and upgrade MySQL distributions on our Ubuntu Servers. This script is known to work on Ubuntu 11.04 and 11.10. I'm pretty sure it will work on most modern Unbutu distros. We currently have MySQL 5.5.17 - 5.5.21 installed and running on our Ubuntu 11.xx (32 and 64 bit) servers. I have also included some information about changing the data directory (datadir) of MySQL to be something other than /var/lib/mysql.
[SIZE=3]
[/SIZE] [SIZE=3]**PLEASE READ THE FOLLOW**[/SIZE]

Please read and study the script first! Do not blindly execute it. There are configuration options you must set in the script (like the MySQL distro you want installed).

[SIZE=2]**Prerequisites**[/SIZE]

**1. Install Ubuntu's MySQL Distribution (VERY IMPORTANT!!)**
**If the server does not already have MySQL installed then you must install the Ubuntu MySQL distribution first!** This will properly configure the MySQL and Ubuntu environment. So, if MySQL is not already installed then do so now like this:
```
sudo apt-get install mysql-server
```Once the Ubuntu MySQL server distro is installed, then proceed with using the attached script.

[B]If MySQL is already installed and running then you may use the attached script.

2. Install ALIEN
[/B][alien]("http://manpages.ubuntu.com/manpages/oneiric/man1/alien.1p.html") must be installed prior to using the attached script[B]:
[/B]```
sudo apt-get install alien
```[B]

3. Install libaio
[/B]Usually **libaio** is installed when the Ubuntu MySQL distro is installed. It is required for MySQL. You can make sure it's installed by doing:
```
sudo apt-get install libaio1 libaio-dev
```[SIZE=3][B]

Changing the MySQL data directory[/B][/SIZE]
Reference: [http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html](http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html)
Ubuntu uses security software called AppArmor that specifies the areas of your filesystem applications are allowed to access. Unless you modify the AppArmor profile for MySQL, you&#8217;ll never be able to restart MySQL with a new *datadir *location. In the terminal, enter the command:
```
sudo vi /etc/apparmor.d/abstractions/mysql
```Copy the lines beginning with **/var/lib/mysql** and paste the lines below the originals. Optionally comment out the originals with hash marks (&#8220;#&#8221;). Now change **/var/lib/mysql** in the two new lines with your new **path/to/new/datadir**'. Save and close the file. Example *mysql* AppArmor file:
*HINT: The path/directory specified will also include all the sub-directories!*
```

/var/lib/mysql/mysql.sock rw,
/usr/share/mysql/charsets/ r,
/usr/share/mysql/charsets/*.xml r,
/d01/mysql/ rw,

```Restart the AppArmor profiles with the command:
```
sudo /etc/init.d/apparmor reload
```

---

### Post by puluceno on 2012-03-01
Thanks a lot! this helped me a lot!

---

### Post by zekapeta on 2012-03-03
you completely saved my life! :D

---

