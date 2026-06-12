---
title: "Setting up a home webserver"
date: 2006-01-14
forum: Server Platforms
---

### Post by ixus_123 on 2006-01-14
Hello guys.

I've finally managed to spare a computer that I can use as a dedicated webserver.  I intend to use it to host a blog, perhaps a few articles / reviews, a gallery (either gallery 1.5 or 2) so my friends can see my pictures & upload, & possibly Hula.  I haven't tried Hula yet but I work shift work & it would be handy for my friends to be able to see at a glance when I am available & Hula looks like it fits the bill.

The machine of choice is a Via N10000 mini-itx board with 1ghz C3 chip & 512mb ram with 120gb hard disk.

I'd like a bit of partitioning advice to start me off please.  This is what I had in mind - any critique / comments / suggestions welcome

1. / = 10gb
2. /swap = 1gb
3. /home = 3gb
4. /Var = what ever remains (bulk of the drive)
5. /swap = 1gb 
6. /var/apt/cache/archive = 5gb (I'll probable take a few installs to get it how I like so I figure this is easier than backing up to disc each time)

I plan to do the basic server install & then install xfce (xubuntu-desktop) package.  Should I have more swap for a server?  I don't mind alocating more as I think I have plenty of spare space I can free up from /var

I was thinking an apache / mysql / php install would suit me going for php4 instead of 5 as more things seem to work with it.  I don't know about mysql as I could never get that to work on past attemps.

I've used Gallery 1.5 before & really loved it so that's definetely going on, that or 2.  I thought I'd give joomla, nucleus, drupal, word press all a try for my blog.  I have tried some on opencms.org but think I need to real life test to sort myself out.

That sort of brings me to the next problem.  Installing mysql & getting to run.  I haven't been able to do it so far but found a tutorail on teh word press site that looks like it was written for beginners like me so fingers crossed on that account.

A final question, for changing permissions of folders / files in my /www, should I be using chmod 666 or 777 or something different?

Thanks

---

### Post by Cubicegg on 2006-01-14
Let me know how you get on with hula and setting up the mail server. I've been playing with Hula too....

---

### Post by Cubicegg on 2006-01-14
hi guys,

fairly new to linux.... but am getting there.... i have installed hula but messed it up and want to uninstall and setup again, does anybody know how to do this, and also with similar applications i install via the terminal? 

thanks in advance

---

### Post by karih on 2006-01-14
[QUOTE=ixus_123]Hello guys.

I've finally managed to spare a computer that I can use as a dedicated webserver.  I intend to use it to host a blog, perhaps a few articles / reviews, a gallery (either gallery 1.5 or 2) so my friends can see my pictures & upload, & possibly Hula.  I haven't tried Hula yet but I work shift work & it would be handy for my friends to be able to see at a glance when I am available & Hula looks like it fits the bill.

The machine of choice is a Via N10000 mini-itx board with 1ghz C3 chip & 512mb ram with 120gb hard disk.

I'd like a bit of partitioning advice to start me off please.  This is what I had in mind - any critique / comments / suggestions welcome

1. / = 10gb
2. /swap = 1gb
3. /home = 3gb
4. /Var = what ever remains (bulk of the drive)
5. /swap = 1gb 
6. /var/apt/cache/archive = 5gb (I'll probable take a few installs to get it how I like so I figure this is easier than backing up to disc each time)

I plan to do the basic server install & then install xfce (xubuntu-desktop) package.  Should I have more swap for a server?  I don't mind alocating more as I think I have plenty of spare space I can free up from /var

I was thinking an apache / mysql / php install would suit me going for php4 instead of 5 as more things seem to work with it.  I don't know about mysql as I could never get that to work on past attemps.

I've used Gallery 1.5 before & really loved it so that's definetely going on, that or 2.  I thought I'd give joomla, nucleus, drupal, word press all a try for my blog.  I have tried some on opencms.org but think I need to real life test to sort myself out.

That sort of brings me to the next problem.  Installing mysql & getting to run.  I haven't been able to do it so far but found a tutorail on teh word press site that looks like it was written for beginners like me so fingers crossed on that account.

A final question, for changing permissions of folders / files in my /www, should I be using chmod 666 or 777 or something different?

Thanks[/QUOTE]
I'm no expert and I've never heard of Hula, but I've done pretty much the other things your after so I'll try to help a bit.

Partitioning:
I've recently stopped splitting my hard drive to a bunch of partitions, mostly becase I found no good argument for doing it.  When partitioning too much I often ended in filling some partitions while others where quite empty which usually costed a lot of time wasted moving files and resizing partitions and reinstalling linux, and I didn't seem to gain anything, at least nothing I could see (note that I have not set up any heavy-duty servers which might gain from much partitioning).
Now I usually have a few partitions.  One root partition and one for /home (which is where I keep my www root) seems to be fine for me.  On my "media" server I joined together two disks with [LVM]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29") and had one "virtual partition" for /, one for /home and one for /home/media.
If you would like to have many partitions I recommend looking into LVM because that offers the possibility of resizing partitions afterwards.  Otherwise I don't recommend having many partitions unless if you have a very good reason for it.

If I were you, I'd say, about 10GB for / partition, the rest for /home (and move your www root there). 1GB swap is enough, a webserver doesn't require much ram/swap.

Web server / PHP:
Apache/php is very easy to install, something like this should work:
$ sudo apt-get install apache2 libapache-mod-php4
You might need some other packages but I doubt it.
Configuring Apache to fit you might be more of a challenge.  My setup is something like this:
I have the directory /home/www (owned by root, group is www-data, rwxr-x---).    There inside I have another directory called www (/home/www/www).  That directory is owned by root, the group is www-data and it has read/write/execute permissions for owner and group plus the sticky bit (chmod +t www).  Then my user, which is going to be writing files into the /home/www/www directory is part of the www-data group.  If you add the sticky bit, you can add more users to the www-data group and you can all place files in the www root but you can not remove other peoples files (unless the permissions enable it).
Then go to /etc/apache2/sites-available/default and change the values.  My file is like this:
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin email@domain.tld

        ServerName localhost
        DocumentRoot /home/www/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /home/www/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /home/www/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /home/www/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```Modify it to suit your needs.

MySQL:
Installing with apt is quite easy:
$ apt-get install mysql-server
$ mysql -u root
... and your in.  Now you have to create users inside mysql, look up GRANT in the mysql manual.  I think it was somthing like this to create a super user.
mysql> GRANT ALL ON *.* TO 'user'@'localhost'
    -> IDENTIFIED BY 'pass' WITH GRANT OPTION;
then to remove the passwordless root user
mysql> DELETE FROM mysql.user WHERE user='root';
and finally
mysql> FLUSH PRIVILEGES;
I think that should suffice.

Hope this helps... :)

---

### Post by s0c0 on 2006-01-14
[QUOTE=ixus_123]Hello guys.
I've used Gallery 1.5 before & really loved it so that's definetely going on, that or 2.  I thought I'd give joomla, nucleus, drupal, word press all a try for my blog.  I have tried some on opencms.org but think I need to real life test to sort myself out.

That sort of brings me to the next problem.  Installing mysql & getting to run.  I haven't been able to do it so far but found a tutorail on teh word press site that looks like it was written for beginners like me so fingers crossed on that account.

A final question, for changing permissions of folders / files in my /www, should I be using chmod 666 or 777 or something different?

Thanks[/QUOTE]

Swap space is supposed to be 1.5 times the total amount of system RAM, but in my opinion you should be fine with the 1 gig swap space.  I doubt you will ever need it unless you anticipate a heavy load.

For the permissions my /var/www is set to drwxr-xr-x.   I think thats a 755, which is more secure than a 777.  I would then use the chown command to add your main user to that directory so you don't have to login as root to add/edit files.

---

### Post by ixus_123 on 2006-01-15
[QUOTE=Cubicegg]Let me know how you get on with hula and setting up the mail server. I've been playing with Hula too....[/QUOTE]
I don't really have a need for teh mail server bit although I'm not sure if Hula gives you an option of whether you want to use it or not.  I only want the colourful calander part of it so people (including myself) can easily tell when I'm working.

For anyone that hasn't seen Hula, there's a nice flash demo linked below made using Wink I believe

[http://nat.org/demos/]("http://nat.org/demos/")


karih, thanks - I'm going to go out for a cycle & test out my replacement battery & I'll givr your mysql method a try when I get back :)

Any reason for moving /www to home?  I wasn't even going to bother making a home partition since I doubt it will see many files on my system.  I've never made a separate partition for /var/apt/cache/archive before but I figure that it will make the reinstalls easier with less downloading / inserting CDs as long as the installer doesn't want to write over it.


s0c0, thanks as weell :)
I know what you mena about swap - personally I think the 2x ram etc was only intended for back in the day when computers didn't have much ram.  1x should be enough I think.  I have space to spare on teh drive though & thought another swap partition wouldn't hurt & as they are (hopefully) at different ends of the disk, the system will be able to seek the closest although I don't know if Ubuntu prioritises swap partitions are if they are all treated equally.

I think I'll have to do some reading up n my chmod & chown commands :)

---

