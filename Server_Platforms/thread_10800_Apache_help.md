---
title: "Apache help"
date: 2005-01-11
forum: Server Platforms
---

### Post by acejones on 2005-01-11
I'm an Ubuntu n00b, and trying to run apache.  I've got Apache, MySql, and PHP all installed (per the Ubuntu guide...which is marvelous, btw).  My question:  I previously had PHP and MySql running on a spare Win 2k3 server.  Before wiping 2k3 for Ubuntu, I made a backup of the Inetpub folder.  Can I copy the contents of this folder to the necessary dir in Ubuntu?

---

### Post by flade on 2005-01-11
Correct me if I'm wrong but you can. Just put files to /etc/www/ 
This is just for files. Databases have to be backed up in another way.




Fladé

---

### Post by Johan on 2005-01-11
[QUOTE=flade]Correct me if I'm wrong but you can. Just put files to /etc/www/ 
This is just for files. Databases have to be backed up in another way.




Fladé[/QUOTE]
 Actually, I think you should put the files in /var/www/.

---

### Post by wulf on 2005-01-11
You can put them anywhere but /var/www is the default. If you want to change the location of the webroot, the configuration files are in /etc/apache2 (see the sites-available subdirectory) if you're using apache2... probably /etc/apache if you're using apache1.3.

Wulf

---

### Post by acejones on 2005-01-12
[QUOTE=wulf]You can put them anywhere but /var/www is the default. If you want to change the location of the webroot, the configuration files are in /etc/apache2 (see the sites-available subdirectory) if you're using apache2... probably /etc/apache if you're using apache1.3.

Wulf[/QUOTE]
 cool.  i'll try that.  thanks.

---

### Post by acejones on 2005-01-13
ok, i can't copy the contents from the cd, b/c when I insert the cd, nothing happens.  i tried mounting it, but i get errors that the cd-rom drive is not listed in the fstab.  i also tried copying from a network drive by using 
cp //west/wntinf/admin/Inetpub /var/www , but i got
cannot copy: no such file or directory.

here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

help!

---

### Post by Madman on 2005-01-17
[QUOTE=acejones]ok, i can't copy the contents from the cd, b/c when I insert the cd, nothing happens.  i tried mounting it, but i get errors that the cd-rom drive is not listed in the fstab.  i also tried copying from a network drive by using 
cp //west/wntinf/admin/Inetpub /var/www , but i got
cannot copy: no such file or directory.

here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

help![/QUOTE]
Try [from a standard terminal]:
sudo cp /media/cdrom0/west/wntinf/admin/Inetpub /var/www

---

### Post by acejones on 2005-01-17
[QUOTE=Madman]Try [from a standard terminal]:
sudo cp /media/cdrom0/west/wntinf/admin/Inetpub /var/www[/QUOTE]
 cp: cannot stat `/media/cdrom0/west/wntinf/admin/Inetpub': No such file or directory

---

### Post by cpinto on 2005-01-17
Mount the CD-Rom first with:
% mount /media/cdrom0

then copy your files...

---

### Post by acejones on 2005-01-17
[QUOTE=cpinto]Mount the CD-Rom first with:
% mount /media/cdrom0

then copy your files...[/QUOTE]
 mount: special device /dev/scd0 does not exist

---

### Post by acejones on 2005-01-25
bump

---

### Post by mr_ed on 2005-01-28
So when you stick the CD in the drive, it doesn't show up on the desktop?

On the (IDE) CD-ROM on my laptop, sometimes it doesn't register that there's a CD in the drive unless I boot with it already in the drive.

Otherwise I get "mount: special device /dev/hdc does not exist."

I just thought it was a hardware issue (since it doesn't happen on my desktop), but maybe it's a kernel bug.

Just for kicks, try booting with it in the drive and see if it shows up on your desktop.  If it does, you're good to go.

---

### Post by acejones on 2005-02-01
[QUOTE=mr_ed]So when you stick the CD in the drive, it doesn't show up on the desktop?

On the (IDE) CD-ROM on my laptop, sometimes it doesn't register that there's a CD in the drive unless I boot with it already in the drive.

Otherwise I get "mount: special device /dev/hdc does not exist."

I just thought it was a hardware issue (since it doesn't happen on my desktop), but maybe it's a kernel bug.

Just for kicks, try booting with it in the drive and see if it shows up on your desktop.  If it does, you're good to go.[/QUOTE]
 nope.  didn't work.

---

### Post by acejones on 2005-02-04
[QUOTE=acejones]nope.  didn't work.[/QUOTE]
 Ok, I was finally able to get the folders in the Inetpub directory into /var/www.  now, since I know absolutely nothing, I need help configuring my setup so I can access these files (when I go to [http://localhost](http://localhost), i get the Apache2 install page)

---

### Post by brousch on 2005-02-04
How about if you go to *[http://localhost/somefile.php](http://localhost/somefile.php)* , where *somefile.php* is the name of one of the files you copied over?

I think the Apache install page you are seeing is just a placeholder named *index.html*, which is the first file name Apache looks for in a directory if no file is specified.

So if you delete */var/www/index.html* you will probably see a directory listing like you were expecting.

I notice my Apache 1.3.31 on Warty does not have a default *index.html* in */var/www/*, so I could be wrong.

---

### Post by Sleeper Service on 2005-02-09
I've got a fresh install of Apache/PHP/MySQL which I did using the Synaptic Package Manager.  It installed like a dream, so no problems there.

I've copied a website into /var/www - so now I have a file called /var/www/datw.org.uk/index.php

However, though I can view the contents of /var/www/ by looking at [http://localhost](http://localhost), if I try to open my website, my browser's download function is triggered and it won't open the page.

In Firefox, I get a pop-up window saying "You have chosen to open index.php which is a PHP file from [http://localhost/datw.org.uk/](http://localhost/datw.org.uk/)  What should Firefox do with this file?  [ ] Open with... [ ] Save to disk"... etc.

With Opera, I get a similar problem - Opera tells me I'm trying to open a file of type application/x-httpd-php, and what would I like to open it with?

I strongly suspect a server setting here - can anybody advise what it is and how I might go about altering it?

By the way, I'm running Apache 1.3.31.

---

### Post by brousch on 2005-02-09
Make sure you have installed the following packages:
[B]apache-mod_php4
php4
phplib[/B]

The best way to make sure you have them is to search for 'php' in Synaptic and make sure they are installed.

The names may be slightly off from what I posted above, but they should be reasonably similar.

I suspect that you are missing **mod_php4** since that is the package that tells apache how to use php.

After you verify that the packages are installed, restart the apache server (it is one of the following commands, I forget which on Ubuntu):
[I]sudo /etc/init.d/apache restart
sudo /etc/init.d/httpd restart[/I]

If it still does not work, we will have to dig into your httpd.conf and see what is wrong.

---

### Post by Sleeper Service on 2005-02-11
Thanks, brousch -

I can't find a module called apache-mod_php4 with Synaptic.  The closest I can find is libapache2-mod-php4 - but I think that's version 2 of apache, and I prefer 1.3.* as that's closer to my actual hosting environment.

I can't find anything called phplib either.

In the description for the package php4 (which *is* installed), it says:
> This package provides the loadable module for the apache webserver. Compiled
in modules are: bcmath, calendar, curl, dba, exif, filepro, ftp, mm, sockets,
wddx, xml, yp and zlib.
Doesn't that sound as though it *should* properly intergrate with apache?

Anything else I could try?

---

### Post by brousch on 2005-02-11
You are correct about the installed packages. In Ubuntu those are all you need. I went home and verified this on my Ubuntu install (apache 1.3.31.6 and php 4:4.3.8-3ubuntu7 according to Synaptic).

The next step is to look at your /etc/apache/httpd.conf file in the text editor of your choice (I like nano, but you can use vi, emacs, or the gui text editor running as sudo). You must be sudo to make changes.

If you scroll down to about line 786. You should see:

[I]
    # And for PHP 4.x, use:
    #
    #AddType application/x-httpd-php .php
    #AddType application/x-httpd-php-source .phps
[/I]

Now it seems to me that those two AddType lines **should be uncommented** for php to work. However, php is currently working on my system with them commented out. Very strange!

So I suggest you uncomment those two AddType lines so it looks like this:

[I]
    # And for PHP 4.x, use:
    #
    AddType application/x-httpd-php .php
    AddType application/x-httpd-php-source .phps
[/I]

Then save the changes and restart apache (sudo /etc/init.d/apache restart).

Hopefully now you can view [http://localhost/datw.org.uk/index.php](http://localhost/datw.org.uk/index.php)

---

### Post by Sleeper Service on 2005-02-12
Sorry, brousch - it still doesn't work.  Even restarted the computer when just restarting apache didn't work (old W**dows habits die hard!).

Same results in Opera.  Firefox is subtly different - its download pop-up says I'm trying to open a "PHTML" file (it said "PHP" before).

But still no cigar :(

What next?

---

### Post by brousch on 2005-02-12
I am beiginning to suspect that there is something strange with your .php files.

Try to create a blank file named test.php in /var/www/

Make the contents of the file:

[I]<?php
echo "This is a test";
?>[/I]

Then see if you can view [http://localhost/test.php](http://localhost/test.php)

If you can, then php is working correctly, and there is something wrong with the formatting of your other .php files (or permissions on them?).

---

### Post by Sleeper Service on 2005-02-13
I feel very silly, and I'm sorry I might have wasted your time, brouche :/

It was permissions, or ownership I think - both have been altered considerably since backing up on CD the contents of /var/www/html/ from my old Mandrake system and copying it all from the CD to my new /var/www/ directory under Ubuntu.

[http://localhost/datw.org.uk/index.php](http://localhost/datw.org.uk/index.php) was set as *-rwxr--r-- root root*, so perhaps the fact that it wasn't executable was causing the problem.  Other files in other website directories were *-rwx------ root root* - so not surprising they weren't working properly!

Anyway, I changed the owner and group of everything on the server to me, and changed the permissions to 755.

It works fine now.

Again - my apologies!  But many thanks for you help :)

---

### Post by Ces on 2005-04-09
[QUOTE=Sleeper Service]I've got a fresh install of Apache/PHP/MySQL which I did using the Synaptic Package Manager.  It installed like a dream, so no problems there.

I've copied a website into /var/www - so now I have a file called /var/www/datw.org.uk/index.php

However, though I can view the contents of /var/www/ by looking at [http://localhost](http://localhost), if I try to open my website, my browser's download function is triggered and it won't open the page.

In Firefox, I get a pop-up window saying "You have chosen to open index.php which is a PHP file from [http://localhost/datw.org.uk/](http://localhost/datw.org.uk/)  What should Firefox do with this file?  [ ] Open with... [ ] Save to disk"... etc.[/QUOTE]

I'm having the same problem, and the solutions suggested after the above cited post does not help. Any suggestions?

---

### Post by wulf on 2005-04-11
What happens if you try the suggestion of creating a very simple test.php file (as brousch suggested)?

Wulf

---

### Post by Zerlinna on 2005-11-06
Hi Wulf,

I have the same problem (I try to install [Edwiki]("http://www.erziehung.uni-giessen.de/wb/edwiki/wiki.php") and / or [moodle]("http://www.moodle.org")) - neither my firefox nor mozilla nor konqueror (using KDE) can show the .php files. 

I did as told here (uncomment the lines in the httpd.conf, change permissions..)

I created the php.test file and it gives me the same error. 

:confused:

Ok I tried to do as described [here]("http://www.roundridge.com/hs/apache-php-homesite05.php") - and after restarting apache it worked fine. 
(Only now I got an mysql_errno fatal error when trying to install ed.wiki... grmbl!!)

---

### Post by habtish on 2006-06-09
[QUOTE=Sleeper Service]I feel very silly, and I'm sorry I might have wasted your time, brouche :/

It was permissions, or ownership I think - both have been altered considerably since backing up on CD the contents of /var/www/html/ from my old Mandrake system and copying it all from the CD to my new /var/www/ directory under Ubuntu.

[http://localhost/datw.org.uk/index.php](http://localhost/datw.org.uk/index.php) was set as *-rwxr--r-- root root*, so perhaps the fact that it wasn't executable was causing the problem.  Other files in other website directories were *-rwx------ root root* - so not surprising they weren't working properly!

Anyway, I changed the owner and group of everything on the server to me, and changed the permissions to 755.

It works fine now.

Again - my apologies!  But many thanks for you help :)[/QUOTE]


Hello guys, I know this thread has been inactive for a long time but am posting this in hope someone will take the time to look at it and offer some help
I am having the same problem above [.php files opening as source files in browser] I have followed the conversation here and made sure i have all the packages neccessary.
I have a testphp.php file with -rwxr-xr-x permissions and I own the file. I still can not get apache to recognize my php files.
anyone help?

---

