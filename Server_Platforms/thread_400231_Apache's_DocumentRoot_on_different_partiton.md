---
title: "Apache's DocumentRoot on different partiton"
date: 2007-04-03
forum: Server Platforms
---

### Post by VoidMain() on 2007-04-03
Hello

I installed Apache server and it works OK, if there is default DocumentRoot property (/usr/local/apache2/htdocs). But I need to change this path to different partition, so I set this property to "/media/sda7". Unfortunately it made that there's an error now:> Forbidden

You don't have permission to access / on this server.
I tried to change chmod on 777 for /media/sda7 but it didn't change anything. What can I do to keep all documents on different partition and to make Apache read them? Help me please.

---

### Post by uric on 2007-04-03
Hi, Im rather new to linux but I have my apache root on a different partition, and it works fine

this is my apache folder settings, 
```

drwxr-xr-x  2 root  root  4096 2007-04-02 00:54 www

```
I think you should keep it root for sercurity reasons.

in httpd.conf below the document root there is a directory that should be same as document root. have you done that?

here is a part from my httpd.conf

```


ServerName 192.168.1.222:51953

#
# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "/media/keep/www/"

#
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/media/keep/www/">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    Options Indexes FollowSymLinks

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    AllowOverride None

    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>


```

---

### Post by VoidMain() on 2007-04-03
What file system is your partition formated? I formated it FAT 32 to make it visible for Windows and Linux. But now I can't change permission to files on this partition. Chmod is 770 and I don't know how to change it to 755 or 775. Could you help me?

---

### Post by az on 2007-04-03
> **VoidMain() said:**
> What file system is your partition formated? I formated it FAT 32 to make it visible for Windows and Linux. But now I can't change permission to files on this partition. Chmod is 770 and I don't know how to change it to 755 or 775. Could you help me?

Fat32 does not support Unix permissions (or windows ones).  I would not advise you use this to serve web pages.

---

### Post by az on 2007-04-03
> **VoidMain() said:**
> Hello

I installed Apache server and it works OK, if there is default DocumentRoot property (/usr/local/apache2/htdocs).

How did you install Apache?  If you install apache using the package manager, it defaults to /var/www.  Did you install apache from source or from another software repository?

---

### Post by VoidMain() on 2007-04-03
[QUOTE=az]How did you install Apache? If you install apache using the package manager, it defaults to /var/www. Did you install apache from source or from another software repository?[/QUOTE]

I installed apache from source.

[QUOTE=az]Fat32 does not support Unix permissions (or windows ones). I would not advise you use this to serve web pages.[/QUOTE]
So... is there any possibility to make a partition visible and changeable both on Linux and on Windows? I wanted to do it to not copy documents from linux partition to windows partition every time I do any changes in files. I just wanted to have common partition for Apache server installed on both operating systems. (I have apache on windows also). Is it possible?

---

### Post by az on 2007-04-03
> **VoidMain() said:**
> I installed apache from source.


So... is there any possibility to make a partition visible and changeable both on Linux and on Windows? I wanted to do it to not copy documents from linux partition to windows partition every time I do any changes in files. I just wanted to have common partition for Apache server installed on both operating systems. (I have apache on windows also). Is it possible?

1.  There is no good reason to install apche from source.  Use the version in the repos and you benefit from security updates and proper configuration.

2.  You can get an ext3 driver for windows.  I forget what it's called, but it makes it so that windows can natively use ext3 filesystems.

---

### Post by huygens on 2007-04-03
The ext2 driver for windows can be found here: [http://www.fs-driver.org/](http://www.fs-driver.org/)
It is compatible with ext3 too, but won't use the journaling enhancements (when on Windows), [see their FAQ]("http://www.fs-driver.org/faq.html#acc_ext3").

---

### Post by huygens on 2007-04-03
> **VoidMain() said:**
> [...] I tried to change chmod on 777 for /media/sda7 but it didn't change anything. [...]

As you said, your partition is in FAT32. The permission are then set when it is mounted.
Apache is ran as user www-data (when installed from the repositories), so you would need to give the group ownership of your partition to user www-data. You need to find out the group ID (a number):```
grep www-data /etc/group
```After the second semi-colon (':') you will see the group ID (GID).
Now edit your fstab:
```
sudo nano /etc/fstab
```Find the line corresponding to your /media/sda7, you will see on the same line gid=nn where nn is a number. Simply replace this number by the GID for www-data you have found earlier.

Now if you reload your partition, Apache should be able to read your partition:
```
sudo umount /media/sda7
sudo mount /media/sda7
```and try to access your web site :-)

Anyway, I second the suggestion of az that you should not use FAT32. To say the least, I had countless problem with this file system because it does not make any difference if a name is upper or lower case. Then, I could not manage proper file permission neither!

---

