---
title: "/var/www issues"
date: 2008-05-02
forum: Server Platforms
---

### Post by dewman0012 on 2008-05-02
My Ubuntu experience has been great thus far and I had our webpages displaying corrently. However, today I went to my /var/www folder to edit some files, it wouldn't let me open any of the directories. The even more weird thing is, they weren't even recognized as directories but showing up as "unknown". 

1) Why did the directories switch to unknown?

2) How do I fix this and make them directories again?


Thanks! 

P.S. We have GUI setup on this server

---

### Post by ghostknife on 2008-05-03
How did you browse to the files?

Via the GUI file browser?
Via the console?
Via FTP?
Via HTTP connection?

This is important.

Secondly, try to run a fsck on the filesystem.

---

### Post by dewman0012 on 2008-05-03
> **ghostknife said:**
> How did you browse to the files?

Via the GUI file browser?
Via the console?
Via FTP?
Via HTTP connection?

This is important.

Secondly, try to run a fsck on the filesystem.

I browse this by the GUI file browser. Previously when I used FTP, it would take me directly to the /var/www area, but now when I login it goes to the home of the user I login as with no way of getting to the /var/www area.

For the fsck, I am not sure which option to do, but this is what it says:

"The superblock could not be read or does not describe a correct ext2 filesystem."

---

### Post by ghostknife on 2008-05-04
It seems you got a corrupted filesystem.

Do the following and paste output:
```

sudo fsck -l
```

Then also:
```

mount
```

Then also:
```

cat /etc/fstab
```

---

### Post by dewman0012 on 2008-05-04
Results from sudo fsck -1:

```
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: invalid option -- 1
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

```

Results from mount:

```
/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=kermit)
```

Results from cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=5f9314ae-f36d-4b46-ad66-f624cff7cf64 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=6c7a788f-c785-42be-a70f-63a6d016c57d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by dewman0012 on 2008-05-05
Bump Bump Bump :)

---

### Post by dewman0012 on 2008-05-08
Anyone know how to help with this corrupt issues?

---

### Post by exaviorn on 2008-05-08
This might not be the answer,but are ownerships wrong?

---

### Post by dewman0012 on 2008-05-08
> **exaviorn said:**
> This might not be the answer,but are ownerships wrong?

This wouldn't be the issue here. The directories aren't even being recognized at all. This make the premission not able to be determined.... :(


I don't like what I am seeing thus far from Linux. All my other files are fine except the /var/www directory which is the main platform we need.

---

### Post by exaviorn on 2008-05-08
Sorry!,its just that was a problem with my server in the past proftpd had somehow got ownership of /var/www:lolflag:

---

### Post by ikt on 2008-05-08
> **dewman0012 said:**
> Anyone know how to help with this corrupt issues?


to continue trying to fsck(fix) the file system,

if you have a live cd I would recommend booting off of that, the idea is that you don't want to have your hard drive mounted when you're fixing (file system) errors.

After booting up to the live cd make sure your old drive isn't mounted and run fsck like you did before (not including the -L).

See if that fixes anything, else I'd probably just reinstall apache, and ofc I would also backup the hard drive, and on an off moment run a hard drive checker on it to make sure it's healthy.

---

### Post by dewman0012 on 2008-05-10
> **ikt said:**
> to continue trying to fsck(fix) the file system,

if you have a live cd I would recommend booting off of that, the idea is that you don't want to have your hard drive mounted when you're fixing (file system) errors.

After booting up to the live cd make sure your old drive isn't mounted and run fsck like you did before (not including the -L).

See if that fixes anything, else I'd probably just reinstall apache, and ofc I would also backup the hard drive, and on an off moment run a hard drive checker on it to make sure it's healthy.

Couple questions in regards to your suggestion:


Booting from the Ubuntu Server CD, how would I get to the command line? From what I remember, you are only prompt to the install screen.

How would I go about unmounting the old drive? After which, and I just fsck, how do I mount it back?


I am extremely new to this, so I appreciate the extra help!

---

### Post by songshu on 2008-05-10
if you boot from the server cd you would have to follow the questions for the installation for a while...then BEFORE the part to partitioning and formatting the disk, you could simply go to another console with ALT F2 or something..

---

### Post by cdtech on 2008-05-10
Are you using a linux workstation to log into the server via FTP? If you go to a terminal, log into the server "slogin yoursite.com". "cd" to the "/var/www" directory and "ls -Flb" the folder to see the permissions. Are you running a backup program? (which one?). Are you using any encryption on the partition?

```
-rw-r--r-- 1 ##### #####    785564 2008-05-09 22:46 wordpress
drwxr-xr-x 7 ##### #####      4096 2008-04-22 01:59 wp-admin/
-rwxr-xr-x 1 ##### #####     33489 2008-04-22 01:59 wp-app.php*
-rwxr-xr-x 1 ##### #####       129 2008-04-22 01:59 wp-atom.php*
-rwxr-xr-x 1 ##### #####       997 2008-04-22 01:59 wp-blog-header.php*
-rwxr-xr-x 1 ##### #####      2923 2008-04-22 01:59 wp-comments-post.php*
drwxr-xr-x 6 ##### #####      4096 2008-04-22 02:00 wp-content/
drwxr-xr-x 4 ##### #####      4096 2008-04-22 02:00 wp-includes/
-rwxr-xr-x 1 ##### #####      1525 2008-04-22 02:00 wp-links-opml.php*
```

---

### Post by dewman0012 on 2008-05-12
After following your directions cdtech, here is the results

```
drwxr-xr-x  2 xxxxxx   xxxxxx     4096 2008-04-18 16:08 apache2-default/
-rw-rw-r--  1 xxxxxx xxxxxx   5191 2008-04-24 12:54 DIFF_30354.patch
-rw-rw-r--  1 xxxxxx xxxxxx   1083 2008-04-21 23:45 patch_security.zip
-rw-rw-r--  1 xxxxxx xxxxxx 256161 2008-04-24 15:42 pospackage11192007.sql
-rw-rw-r--  1 xxxxxx xxxxxx   4970 2008-04-29 16:57 www_rmspos_net.cer
drwxr-xr-x 23   xxxxxx xxxxxx      4096 2008-04-17 17:58 xcart/
drwxr-xr-x 23 xxxxxx xxxxxx   4096 2008-04-24 09:06 xcart2/

```

I just access FTP via Windows which is rarely. Most of the time I use VNC to access our Linux server so I can work with the GUI.

We are not running any backup program

I do not know of any encryption being used. Everything is pretty much default from the original install.

---

### Post by dewman0012 on 2008-05-12
I obviously have no clue what any of that means. Can anyone give me any insight given all the codes I have posted in this thread?

---

### Post by cdtech on 2008-05-12
> **dewman0012 said:**
> I obviously have no clue what any of that means. Can anyone give me any insight given all the codes I have posted in this thread?

This shows that there are directories that exsist within the web folder on your server. The "d" is for directory the "rwxrwxrwx" means read, write, execute for owner (of the file/directory) group and the world (respectively).

The first set of XXXXXX that we blocked out (thanks for doing that, I forgot to mention) is the owner the second is the group.

> they weren't even recognized as directories but showing up as "unknown".

1) Why did the directories switch to unknown?

2) How do I fix this and make them directories again?

But I do see the directories. Its sounds like a browser issue or a VNC issue. You can probably cd into those directories from the command line.

I personaly use slogin for my Ubuntu box or putty for Windows to maintain my server but thats all command line. You must have a GUI installed on your server as well, I'm taking it.

---

### Post by dewman0012 on 2008-05-13
Ok, I was able to cd into the directories in the /var/www area. However, I find it weird I can do that, but the webpages still don't display. Would the unknown file types keep this from happening?

I do on occasion use Putty for minor issues with Linux. I am no where near good enough with the command line to use this full out on the server.

Yes, we do have a GUI installed on the server. 


I guess the bottom line is, how can I go about fixing this issue? Obviously the files are still intact if I can access them via Putty, but VNC and the webpages are still weird.

---

### Post by cdtech on 2008-05-13
I would be looking into the configuration files for the apache web server. See if they point to the correct directory.

(/etc/apache2/sites-available/default) or whatever your using as your default. Be sure your document root directory has no trailing slash and the directory part does.

Somehow something got updated and re-configed a file somewhere, I'm guessing.

Are you using standard HTML pages or PHP?

---

### Post by dewman0012 on 2008-05-13
> **cdtech said:**
> I would be looking into the configuration files for the apache web server. See if they point to the correct directory.

(/etc/apache2/sites-available/default) or whatever your using as your default. Be sure your document root directory has no trailing slash and the directory part does.

Somehow something got updated and re-configed a file somewhere, I'm guessing.

Are you using standard HTML pages or PHP?

Mix of PHP and HTML. Nothing should have changed in the Apache configuration. I honestly went to the /var/www area and everything was seen as unknown in our GUI. 

Anyways, I have checked all the configuration settings via WebMin and everything is fine. Any other ideas?

---

### Post by mam00th on 2008-05-13
> **dewman0012 said:**
> Results from sudo fsck -1:


Isn't it sudo fsck -**l**

---

### Post by dewman0012 on 2008-05-14
That's what I used, not sure why I put 1 in my post!

---

### Post by cdtech on 2008-05-14
> My Ubuntu experience has been great thus far and I had our webpages displaying corrently. However, today I went to my /var/www folder to edit some files, it wouldn't let me open any of the directories. The even more weird thing is, they weren't even recognized as directories but showing up as "unknown".

You don't have anything wrong with your web pages, you can probably still access the site I'm sure. You have a problem with the program your viewing your site directory with. That's what you need to be looking into.

---

### Post by dewman0012 on 2008-05-15
> **cdtech said:**
> You don't have anything wrong with your web pages, you can probably still access the site I'm sure. You have a problem with the program your viewing your site directory with. That's what you need to be looking into.


I can't view the pages at all. I was able to view it online up until this happened. See for yourself:

[www.pospackage.com](www.pospackage.com)

Prior to the files issues, this displayed fine. Any ideas? There have been ZERO changes to Apache

---

### Post by cdtech on 2008-05-16
Sorry dewman0012, I've been out of town. That is really weird, I also get forbidden access on your site.

I would start by checking the log file, on a command line type: tail /var/log/apache2/error.log

PS.
I just noticed that you have root "/" as your documentroot directory. 

> You don't have permission to access / on this server.

You need to check your /etc/apache2/sites-available/default and look at your configuration.

 DocumentRoot /var/www/apache2-default
        <Directory />
                Options FollowSymLinks IncludesNoExec
                AllowOverride None
        </Directory>
        <Directory /var/www/apache2-default/>

This looks to be the problem.

---

### Post by dewman0012 on 2008-05-19
I checked the log, and it is all recent (May 18) but there is a common error:

13)Permission denied: /var/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

Not sure why this would be changed has I never touched the premissions on the .htaccess files. I suppose in this case, what is the correct chmod for these?


As for the Apache configuration, I use a httpd.conf file instead of the default setup. Regardless, I haven't changed this. What do you mean exactly by the "/" I have in there?

On a side note, how would I got about editing the httpd.conf files through terminal? I understand the vi command, but I have NO idea how to edit and save.

---

### Post by windependence on 2008-05-19
> **dewman0012 said:**
> I checked the log, and it is all recent (May 18) but there is a common error:

13)Permission denied: /var/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

Not sure why this would be changed has I never touched the premissions on the .htaccess files. I suppose in this case, what is the correct chmod for these?


As for the Apache configuration, I use a httpd.conf file instead of the default setup. Regardless, I haven't changed this. What do you mean exactly by the "/" I have in there?

On a side note, how would I got about editing the httpd.conf files through terminal? I understand the vi command, but I have NO idea how to edit and save.

You may want to turn off checking .htaccess files in your httpd.conf file. Use nano, it's for us pussies who don't like vi (me included) ;-)

-Tim

---

### Post by cdtech on 2008-05-19
Your config is pointing to the root directory "/". that's what this say's

> Forbidden

You don't have permission to access / on this server.

---

### Post by cdtech on 2008-05-19
> On a side note, how would I got about editing the httpd.conf files through terminal? I understand the vi command, but I have NO idea how to edit and save.

I use "pico"

Open a terminal:
sudo pico /etc/apache2/httpd.conf

After you edit, just press ctrl x to exit, it will ask if you want to save, press y then press return to save as same name.

---

### Post by windependence on 2008-05-19
> **cdtech said:**
> I use "pico"

Open a terminal:
sudo pico /etc/apache2/httpd.conf

After you edit, just press ctrl x to exit, it will ask if you want to save, press y then press return to save as same name.

Yep, nano and pico have virtually the same controls, both nice lightweight editors.

-Tim

---

### Post by cdtech on 2008-05-19
lovem' easy and fast, no mess..... :)

---

### Post by dewman0012 on 2008-05-19
First off, the pico thing is awesome, wayyyyyy better than the VI editor.

For you to see what my httpd.conf is, I will paste it to show you I don't see a problem here.

```
ServerRoot "/etc/apache2"
PidFile /var/run/apache2.pid
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data
AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

DefaultType text/plain

HostnameLookups Off

ErrorLog /var/log/apache2/error.log

LogLevel warn

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Prod

ServerSignature Off

Include /etc/apache2/conf.d/

DocumentRoot /var/www/xcart2
<VirtualHost *>
DocumentRoot /var/www/xcart2
ServerName pospackage.com
<Directory "/var/www/xcart">
allow from all
Options +Indexes
</Directory>
AccessFileName .htaccess
</VirtualHost>
```



As for the .htaccess, this is essential for me to have in order to use mod_rewrite properly. We have rules in there that are needed. Other than that, there is nothing in there that should be blocking people out.

---

### Post by cdtech on 2008-05-19
Have you tried to access the site using the localhost:
[http://127.0.0.1/](http://127.0.0.1/)

sounds like a permission issue, try:

sudo chmod -R a=rx /var/www

---

### Post by dewman0012 on 2008-05-19
> **cdtech said:**
> Have you tried to access the site using the localhost:
[http://127.0.0.1/](http://127.0.0.1/)

sounds like a permission issue, try:

sudo chmod -R a=rx /var/www

I tried to access the site with localhost, and I got the same error message you did "Forbidden".



After running the permission command you listed, it basically unlocked all the files. Now it lets me work with them inside the GUI. This obviously brings me to some questions:

1) Why did this happen?
2) All my folder permissions are now messed up from what they were previous, what are the chances of this happening again?

---

### Post by lunatinker on 2008-05-20
why folder permissions messed up? I have no idea. 
But i've noticed that some cms/blog/shop-cart .."installers.." finals steps are to attempt chmod from php. 
I like to get new releases or "new to me" apps
working first offline in a dev box and then geting to know 
which files need write access from the app itself.
on upload the mysql database and zipped folder of files.

Quote from someone else:
"....[COLOR="DimGray"]What was the source of the zip file? A Windows box? Windows permissions in a zip file may not translate well to Linux. Other than manually changing permissions after the fact, I don't know if there's a way to tell the unzipping utility to set permissions to a certain pattern[/COLOR]..."

quote from last post on this page: 
[http://www.lunarforums.com/lunarpages_cpanel_help/file_manager_extract_zip_file-t46496.0.html](http://www.lunarforums.com/lunarpages_cpanel_help/file_manager_extract_zip_file-t46496.0.html)

---

### Post by dewman0012 on 2008-05-21
So basically with moving some files from the Windows server over might have caused this issue? I can't think what would have done this though because it was running so well then suddenly went crazy. 

At any rate, I appreciate all the help provided here. Special shout out to Cdtech for helping so much!

---

