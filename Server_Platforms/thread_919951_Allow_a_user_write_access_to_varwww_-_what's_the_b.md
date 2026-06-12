---
title: "Allow a user write access to /var/www - what's the best approach"
date: 2008-09-14
forum: Server Platforms
---

### Post by SHRIKEE on 2008-09-14
So i'm wondering, i've got a Ubuntu 8 server set up. LAMP, and it works fine so far.

Now i'm at the point of putting a bunch of files to work on /var/www in order to run a small website.

Turns out my user (arnan) has read only rights on /var/www
root is forbidden in sftp.

I prefer to use sftp. And am not aware of any installed FTP servers.

Now i can just go into the openssh config and allow root access. Or i can do some magic with userrights and change ownership on /var/www to my user.

I'm wondering what would be the best approach. 

I use a mac and use Cyberduck as my FTP client. This allows me to use FTP SFTP and SSH/SSL.
I prefer SFTP.

Please advise! 

Thanks!

---

### Post by crazycaveman on 2008-09-15
The best approach would be to change the user/group rights.  Allowing root probably isn't the best idea, especially when you could change the folder to owned by the group as www-data and make your user a member of that group and give the group folder write access (and sub-folders).  That's my 2 cents

---

### Post by RealPSL on 2008-09-15
In support of the crazycaveman I would also make the changes recommended [here]("http://ask-dr-shell.com/Filesystem/0002.shtml"). Using setgid and umask together ensure that everyone belonging to that group will have write access to the files.

---

### Post by KiLaHuRtZ on 2008-09-15
I agree with crazycaveman as well...

Make sure the group is www-data on '/var/www'.

prompt> sudo chgrp www-data /var/www

Make '/var/www' writable for the group.

prompt> sudo chmod 775 /var/www

Set the GID for www-data for all sub-folders.

prompt> sudo chmod g+s /var/www

Your directory should look like this on an 'ls -l' output.

drwxrwsr-x

Last, add your user name to the www-data group (secondary group).

prompt> sudo useradd -G www-data [USERNAME]

You should now be able to SFTP to your server as your user name and upload to '/var/www' with no problems.

---

### Post by cpetercarter on 2008-09-15
An alternative is simply to move the default Apache site elsewhere - see [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts")

---

### Post by SHRIKEE on 2008-09-15
Thanks all for your kind, prompt and clear answers. I followed Killahurtz's instructions and got the following:

```

Last login: Mon Sep 15 00:15:57 2008 from 192.168.0.50
arnan@motoko:/var$ sudo chgrp www-data /var/www
[sudo] password for arnan: ********************
arnan@motoko:/var$ sudo chmod 775 /var/www
arnan@motoko:/var$ sudo chmod g+s /var/www
arnan@motoko:/var$ sudo useradd -G www-data arnan
useradd: user arnan exists
arnan@motoko:/var$ 

arnan@motoko:/var$ ls -lt
total 40
drwxr-xr-x  2 root root     4096 2008-09-15 06:28 backups
drwxr-xr-x 10 root root     4096 2008-09-15 06:28 log
drwxr-xr-x 10 root root      380 2008-09-15 01:04 run
drwxr-xr-x 25 root root     4096 2008-09-15 00:54 lib
drwxrwxrwt  3 root root       60 2008-09-14 03:12 lock
drwxrwsr-x  2 root www-data 4096 2008-09-13 18:37 www
drwxr-xr-x  8 root root     4096 2008-09-13 18:37 cache
drwxr-xr-x  3 root root     4096 2008-09-13 18:37 spool
drwxrwsr-x  2 root mail     4096 2008-09-13 18:32 mail
drwxr-xr-x  2 root root     4096 2008-09-13 18:32 opt
drwxrwsr-x  2 root staff    4096 2008-06-13 16:14 local
drwxrwxrwt  2 root root     4096 2008-06-13 16:14 tmp

```

I then logged in with my user 'arnan' via SFTP and tried to upload a file to the /var/www but i still got the permission denied thing. 

I'm guessing folder ownership should remain root? Or should i change that too?

Thanks!

---

### Post by SHRIKEE on 2008-09-15
Just tried :

```
sudo chown arnan /var/www
```

which seems to work fine, apache still reads the thing and i can view the "site". the "IT WORKS!" thing...

THanks again for all your help guys!

---

### Post by ocdude on 2008-12-07
> **SHRIKEE said:**
> Just tried :

```
sudo chown arnan /var/www
```which seems to work fine

Sorry to resurrect this thread, but I found it via Google...

Anyway, the "proper" way of adding an existing user to a group is to use ```
sudo usermod -a -G {group} {username}
```

I'm adding this just in case someone else finds it useful.

---

### Post by Buffalo Soldier on 2008-12-07
Another method that I like to use is to enable the **userdir** mod.

```
sudo a2enmod userdir
```

All the user needs to do is save his PHP/HTML files in -> **/home/<<username>>/public_html**

Browse it at URL -> **[http://localhost/~username/](http://localhost/~username/)**

For example if my username is john, I need to save my web files in **/home/john/public_html** and to browse it just point my webbrowser to **[http://localhost/~john/](http://localhost/~john/)**

This way, each web developer has his/her own folder. Less chance of messing things up. Only when a site or project is ready to go live, then only I'll migrate it to the proper /var/www/

---

### Post by mtsgeo on 2009-10-13
> **Buffalo Soldier said:**
> Another method that I like to use is to enable the **userdir** mod.
....


Thanks so much!  this approach is exactly what i was looking for.  cheers.

---

### Post by spec36 on 2009-11-19
Thanks for the help. This thread solved my issue as well.

---

### Post by Tuliku on 2010-01-10
This worked perfectly for me, thanks !

> **KiLaHuRtZ said:**
> I agree with crazycaveman as well...

Make sure the group is www-data on '/var/www'.

prompt> sudo chgrp www-data /var/www

Make '/var/www' writable for the group.

prompt> sudo chmod 775 /var/www

Set the GID for www-data for all sub-folders.

prompt> sudo chmod g+s /var/www

Your directory should look like this on an 'ls -l' output.

drwxrwsr-x

Last, add your user name to the www-data group (secondary group).

prompt> sudo useradd -G www-data [USERNAME]

You should now be able to SFTP to your server as your user name and upload to '/var/www' with no problems.

---

### Post by sonik88 on 2010-05-05
> **ocdude said:**
> Sorry to resurrect this thread, but I found it via Google...

Anyway, the "proper" way of adding an existing user to a group is to use ```
sudo usermod -a -G {group} {username}
```

I'm adding this just in case someone else finds it useful.

Exactly what did it. Thank you!

---

### Post by andikatjacobdennis on 2011-03-04
sudo chmod 777 /var/www

---

### Post by SeijiSensei on 2011-03-05
That's absolutely the wrong advice.  Granting global permissions like that means you're not willing to invest the effort needed to determine a secure solution with the minimal permissions required.

Oh, and this thread is about two years old now.

---

### Post by CharlesA on 2011-03-05
> **SeijiSensei said:**
> That's absolutely the wrong advice.  Granting global permissions like that means you're not willing to invest the effort needed to determine a secure solution with the minimal permissions required.

+1.

Thread closed due to necro.

---

