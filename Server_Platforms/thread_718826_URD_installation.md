---
title: "URD installation"
date: 2008-03-08
forum: Server Platforms
---

### Post by ariek on 2008-03-08
URD ([http://www.urdland.com/index.html](http://www.urdland.com/index.html)) is a great new web based usenet download manager. The installation is very easy, but not well documented. So here is my howto based on a fresh installation.

** Installation web server, database server, and script processor. **
 
```
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install apache2 php5 mysql-server php5-cli php5-mysql php-pear yydecode unrar par2 trickle cksfv subversion 
sudo pear install net_socket net_nntp 

```Restart Apache. 
 
```
/etc/init.d/apache2 restart
```**Configuration** 
 
Download the webcomponents and change permissions. 
 
```
cd /var/www/ 
```###EDIT###
##Like [GavinSpearhead]("http://ubuntuforums.org/member.php?u=283614") further on in this thread mentioned, using subversion is tricky, because of its development status.
```
 sudo svn co [https://urd.svn.sourceforge.net/svnroot/urd](https://urd.svn.sourceforge.net/svnroot/urd) urd 
```
**SO THIS IS SAFER!**
```
wget http://downloads.sourceforge.net/urd/urd-0.4.tar.gz?modtime=1204990738&big_mirror=0
sudo chown -R www-data:www-data urd/
sudo chmod -R 755 urd/
```
Now you can start the installation by entering the website address ([http://YOUR](http://YOUR) IP-ADDRESS OR HOSTNAME/urd/)

---

### Post by GavinSpearhead on 2008-03-13
> **ariek said:**
> URD ([URL]
# sudo apt-get update 
# sudo apt-get dist-upgrade 
# sudo apt-get install apache2 php5 mysql-server php5-cli php5-mysql php-pear yydecode unrar par2 trickle cksfv subversion 
# sudo pear install net_socket net_nntp 
)

Since version 0.4.0 PEAR is not needed any more. So the last step can be skipped and php-pear can be omitted from the list.

---

### Post by dmendels on 2008-03-23
Hi,

After a bit of fiddling, I can see my URD installation in Firefox, but get an error when doing so:

"[I]Fatal error:
Could not connect to database : ADONewConnection error: [-998: could not load the database driver for ''] in ADONewConnection(, )[/I]"

Also:

"[I]Warning: include(/var/www/urd/trunk/functions/../dbconfig.php) [function.include]: failed to open stream: No such file or directory in /var/www/urd/trunk/functions/functions.php on line 1327

Warning: include() [function.include]: Failed opening '/var/www/urd/trunk/functions/../dbconfig.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/urd/trunk/functions/functions.php on line 1327[/I]"

Please suggest how to fix this...

Thanks,

Dennis

---

### Post by GavinSpearhead on 2008-03-23
> **dmendels said:**
> Hi,

After a bit of fiddling, I can see my URD installation in Firefox, but get an error when doing so:


You are using the svn version of URD, which is not recommend unless you want to develop on URD. Try and install the tarball.

---

### Post by private_lock on 2008-05-18
Hello GavinSpearhead!

I followed your steps ...

[LIST]
[*]First I got an error, that "chfsv" was not found. So maybe I have to add another source ... but which one? See: [http://ubuntuforums.org/showthread.php?t=706543](http://ubuntuforums.org/showthread.php?t=706543)
[*]Second when I try to access [http://localhost/urd](http://localhost/urd) the local web-server is running, but not executing the php. I'm just offered to download the php file to disk :(
[*]In [http://sourceforge.net/forum/forum.php?thread_id=1962755&forum_id=728543](http://sourceforge.net/forum/forum.php?thread_id=1962755&forum_id=728543) I read, to first access [http://localhost/urd/install.php](http://localhost/urd/install.php), this seems to check for the available memory requiring the above package. So the memorytest fails :(
[/LIST]

Could you please clarify the instructions?

Thanks
private_lock

Edit:

I found [http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv) and installed it ... is that version too old??? So the install test still fails at:
PHP memory limit > 128 MB	Failed

---

### Post by ariek on 2008-05-18
Hi,

**cksfv** is not available in Hardy, so you need to install the deb manually from [http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv/](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv/).
Hopefully you have installed PHP, if so restart the Apache server:
```
/etc/init.d/apache restart
```

---

### Post by francky_51 on 2008-06-23
> **private_lock said:**
> Hello GavinSpearhead!

I followed your steps ...

[LIST]
[*]First I got an error, that "chfsv" was not found. So maybe I have to add another source ... but which one? See: [http://ubuntuforums.org/showthread.php?t=706543](http://ubuntuforums.org/showthread.php?t=706543)
[*]Second when I try to access [http://localhost/urd](http://localhost/urd) the local web-server is running, but not executing the php. I'm just offered to download the php file to disk :(
[*]In [http://sourceforge.net/forum/forum.php?thread_id=1962755&forum_id=728543](http://sourceforge.net/forum/forum.php?thread_id=1962755&forum_id=728543) I read, to first access [http://localhost/urd/install.php](http://localhost/urd/install.php), this seems to check for the available memory requiring the above package. So the memorytest fails :(
[/LIST]

Could you please clarify the instructions?

Thanks
private_lock

Edit:

I found [http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/cksfv) and installed it ... is that version too old??? So the install test still fails at:
PHP memory limit > 128 MB	Failed

You need to set memory_limit = 128M (or more)   
in both :
/etc/php5/apache2/php.ini and /etc/php5/cli/php.ini

---

### Post by GavinSpearhead on 2008-07-02
> **ariek said:**
> URD ([http://www.urdland.com/index.html](http://www.urdland.com/index.html)) is a great new web based usenet download manager. The installation is very easy, but not well documented. So here is my howto based on a fresh installation.


Note the correct URL is: [http://www.urdland.com/](http://www.urdland.com/)
[http://www.urdland.com/index.html](http://www.urdland.com/index.html) does no longer exist

---

### Post by GavinSpearhead on 2008-07-14
Cksfv is an optional tool. Installation without it should not fail. Unfortunately it was removed from Hardy. If your pachage does not install it in $path you can always set it later in the configuration.

The memory limit is needed, really. Strangely enough on some installations URD seems to need a lot more than 128 MB. Mostly 128 MB is enough.

---

