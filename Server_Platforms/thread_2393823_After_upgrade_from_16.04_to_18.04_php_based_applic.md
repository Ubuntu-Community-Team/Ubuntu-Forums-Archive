---
title: "After upgrade from 16.04 to 18.04 php based applications do not work"
date: 2018-06-08
forum: Server Platforms
---

### Post by deepakdeshp on 2018-06-08
Hello,
I upgraded the virtual machine from Ubuntu 16.04 to 18.04. I followed this process [https://websiteforstudents.com/upgrade-ubuntu-16-04-lts-to-ubuntu-18-04-lts-beta-server/](https://websiteforstudents.com/upgrade-ubuntu-16-04-lts-to-ubuntu-18-04-lts-beta-server/)
After the upgrade when I run any php application, only the php code is displayed in the browser instead of the application running in the browser.

Please help

---

### Post by LHammonds on 2018-06-08
You jumped the gun on doing the upgrade.  For a greater chance of success you should always wait for the first point release before doing the in-place upgrade.  e.g. 18.04.1 LTS

However, the in-place upgrade only ensures that the operating system will be upgraded successfully.  Any installed apps / libraries beyond the base OS will be hit-or-miss.

Ubuntu 16.04 used PHP 7.0 but 18.04 uses PHP 7.2 so all the various modules will be named differently.

At this point, you should probably uninstall Apache/PHP and re-install using the correct names/versions.

For example:

```
apt -y install apache2 php7.2 libapache2-mod-php7.2
```

That will get Apache and PHP installed so that PHP pages will process correctly.

You may need to install additional libraries depending on your app's needs...like these as an example:

```
apt -y install php7.2-curl php7.2-xml php7.2-gd php7.2-mysql php7.2-zip php7.2-intl
```

I don't know about how others upgrade their servers but I "never" do an in-place upgrade.  I always install a new server, migrate the settings/data over from the old server and make 100% sure everything will work 1st.  Then I move the IP to the new server and let it become the new server.  Or if I only had the one physical box, I'd make sure everything was running on another machine (like on my PC inside a virtual server), then blow out the old server and install from scratch using the tested/verified procedure I did for the test box.  Then migrate the data over from the backup location.

LHammonds

---

### Post by deepakdeshp on 2018-06-08
Hello LHammonds ,
Thank you for your immediate reply. The plan to chalk out server upgrades is perfect and I do agree to it. I also visited and bookmarked hammondslegacy.com , an excellent site.

I uninstalled and installed back php and apache2 using the commands in your post but there is no joy. I am afraid I may be stuck with a broken server.

---

### Post by SeijiSensei on 2018-06-08
Make sure you have the libapache2-mod-php package installed.  On 18.04 you also need libapache2-mod-php7.2.

The quickest and easiest way to get a complete Apache+PHP installation, with MySQL thrown in on the side, is to run

```

sudo apt update
sudo apt install lamp-server^

```

The tilde "^" must be included.

---

### Post by deepakdeshp on 2018-06-09
> **SeijiSensei said:**
> Make sure you have the libapache2-mod-php package installed.  On 18.04 you also need libapache2-mod-php7.2.

The quickest and easiest way to get a complete Apache+PHP installation, with MySQL thrown in on the side, is to run

```

sudo apt update
sudo apt install lamp-server^

```

The tilde "^" must be included.
I have many applications installed on the server and each has a mysql password along with mysql data. I am not sure if I install mysql afresh , all my database will be intact.
The problem is with apache and php hence I would like to try solving it at that level.

---

### Post by deepakdeshp on 2018-06-09
I tried out many suggestions on the web and I have been able to run php scripts in the document root /var/www/html But I am not able to run the php script in any subfolders of the document root.

Any help is appreciated.

---

### Post by mastablasta on 2018-06-11
> **deepakdeshp said:**
> I have many applications installed on the server and each has a mysql password along with mysql data. I am not sure if I install mysql afresh , all my database will be intact.


well you have backups made anyway, so why does it matter?

---

### Post by LHammonds on 2018-06-11
> **deepakdeshp said:**
> I tried out many suggestions on the web and I have been able to run php scripts in the document root /var/www/html But I am not able to run the php script in any subfolders of the document root.

Any help is appreciated.
Well, it sounds like Apache+PHP is working if you can get a single PHP file to run instead of reveal its code.  So at this point, you need to trouble-shoot file permissions (is owner set to www-data) and review the .conf files in /etc/apache2/sites-available

After you look-over those, take a look at the error logs to see what specifically is failing beyond simple file permission/ownership settings and site configuration issues.

Try not to look at the server and get overwhelmed at all the things that do not work and focus on making very-specific things work...such as just getting PHP working.  Make a phpinfo.php file and get it to work and look at the modules that are loaded.  Then make a small php file that makes a simple call to a database just to ensure that PHP can connect and talk to the database.  Keep working on the basic building blocks and as you solve specific problems, it may clear up many more issues down the line.

LHammonds

---

### Post by SeijiSensei on 2018-06-11
> **deepakdeshp said:**
> I have many applications installed on the server and each has a mysql password along with mysql data. I am not sure if I install mysql afresh , all my database will be intact.

You can "dump" the entire contents of MySQL and its databases to text using the "mysqldump" command and its "--all-databases" switch.  You can then restore the entire database from that file in case disaster strikes.  See [https://stackoverflow.com/questions/9497869/export-and-import-all-mysql-databases-at-one-time](https://stackoverflow.com/questions/9497869/export-and-import-all-mysql-databases-at-one-time).  I run a script on my server that uses this method to back up all my databases and store the result on a remote machine.

---

### Post by geoffrey-p on 2018-06-19
I ran into the same problem. The solution is to a2enmod (enable module) for PHP 7.2. The old "enable module for PHP 7.0" won't do anything for you.

Essentially, the problem is that the PHP 7.2 module is not enabled for Apache and PHP 7.0 isn't present to serve the content any longer.

---

### Post by bk6662 on 2018-08-18
Thanks all for your recommendations - but especially Geoffrey for a quick fix to both the OP and my issue!!  I completely agree with LHammond and other's cautions, and that it's much better to restart from scratch.  But in my case I don't have that sort of time.  I backed up the working 16.04 VM, and then performed the in-place upgrade.  I'm happy to report that Geoff's suggestion to run 'a2enmod php7.2' was all it took to fix the issue.  It prevented many hours of troubleshooting and reconfiguration.  Maybe I was just lucky (and I do understand that bad things happen all the time), but so far I've been pretty successful using Ubuntu's in-place upgrade

---

### Post by LHammonds on 2018-08-19
> **bk6662 said:**
> Maybe I was just lucky (and I do understand that bad things happen all the time), but so far I've been pretty successful using Ubuntu's in-place upgradeYes, people can and have successfully done the in-place upgrades.   The overall success depends a lot on the applications that are installed and how they are configured.

I do not run across these types of issues because I don't do the in-place upgrades, but knowing about the a2enmod trick will be helpful to know if others experience this upgrade issue.

LHammonds

---

### Post by RobotOfBarr on 2018-09-09
I too have recently upgraded from 16.04 LTS to 18.04 LTS, and had a similar problem to the OP. I reinstalled Apache and PHP7.2, and all modules I need except one. PHP7.2-GD refuses to co-operate. Synaptic goes through the motions of installing it without a complaint, when it's done it, it thinks it's done it (it reports the version and installed files etc), but from the terminal[FONT=courier new]  a2enmod gd  [FONT=arial]reports[/FONT]ERROR: Module gd does not exist!  [/FONT]and it indeed doesn't transform the images.

I'm not a Linux expert and I don't have the detailed knowledge to know where to look. GD does NOT appear in the directory /etc/apache2/mods-enabled

---

### Post by LHammonds on 2018-09-10
Create a phpinfo.php file in the root of your website.
```
vi /var/www/html/phpinfo.php
```

Add the following inside the file:
```
<?php
phpinfo();
?>
```
Then open a browser on your PC and load that page.  e.g. [http://192.168.1.20/phpinfo.php](http://192.168.1.20/phpinfo.php)

Once the page loads, it displays your server's settings and modules loaded.  Search for "GD Support" and you will likely see that it is there and enabled.

You are not going to see a "gd" file in /etc/apache2/mods-available.

You can see if the module is installed on the command-line by typing this:

```
apt search php7.2-gd
```

Which should show "[Installed]" if it is installed.  Example:

```
# apt search php7.2-gd
Sorting... Done
Full Text Search... Done
php7.2-gd/bionic-updates,bionic-security,now 7.2.7-0ubuntu0.18.04.2 amd64 [installed]
  GD module for PHP
```

Be sure to remember to delete the file once done looking at it:
```
rm /var/www/html/phpinfo.php
```

LHammonds

---

### Post by RobotOfBarr on 2018-09-10
Thank you for responding. I indeed have it installed according to apt & phpinfo (but it isn't in "Loaded Modules" where I was looking :( .  BTW, there's no problem with phpinfo - this is on my laptop.)

So now the problem moves to why the production server (PHP7.0) is working and PHP7.2 isn't. I have rechecked the notes for migrating 7.0 -> 7.1 -> 7.2 and can see no mention of the functions in mod-gd. I obviously need to check the dependencies again.

[Edit]
Problem solved. It was a case of Digitus Erroneous, which I'd not noticed, and I was thrown by the module not appearing where I expected. Many thanks for the steer.

---

### Post by kilusu on 2018-10-24
> **geoffrey-p said:**
> I ran into the same problem. The solution is to a2enmod (enable module) for PHP 7.2. The old "enable module for PHP 7.0" won't do anything for you.

Essentially, the problem is that the PHP 7.2 module is not enabled for Apache and PHP 7.0 isn't present to serve the content any longer.

Enabling Php7.2 solved my problem. Thank you.

---

### Post by djbrother on 2019-02-23
Thank you! This works!
I had installed LAMP and it wasn't parsing the php.
However, after running both commands, it now parses the phpinfo().

---

### Post by Viktor_Ferenczi on 2019-03-03
Apache module is named differently, thus not enabled after upgrade.

a2enmod php7.2
systemctl restart apache2

---

