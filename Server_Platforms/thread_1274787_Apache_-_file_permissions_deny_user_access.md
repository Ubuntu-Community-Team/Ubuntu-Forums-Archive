---
title: "Apache - file permissions deny user access"
date: 2009-09-24
forum: Server Platforms
---

### Post by elklabone on 2009-09-24
OK, I'm a dufus. I have some experience with Red Hat a few years back, and am setting up a ubuntu 9.04 server for local LAMP development (mainly php and symfony).

I'm doing great getting everything working the way I want it, and went to get Samba setup to share the /var/www folder so me and another developer can access the Ubuntu server from our Windows clients....

Followed this (old) thread for sharing the /var/www folder through Samba:

[http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

That all worked fine, I can now access the /var/www folder from Windows over our local network, however, instead of getting "It Works!" when I enter the server's IP in my browser, I'm getting:
Forbidden You don't have permission to access / on this server.


OK... so I check the apache logs and see:


[Thu Sep 24 22:15:57 2009] [error] [client ::1] (13)Permission denied: file 

permissions deny server access: /var/www/index.html


My Question:


How do I give apache back the permission it needs and STILL be able to access the /var/www folder through samba?


THANKS! UBUNTU is great, and I'm having a lot of fun with it!

---

### Post by Lars Noodén on 2009-09-25
The guide has some instructions about setting permissions.  Perhaps a typo was made.  

What are the permissions set to for /var/www  and /var/www/index.html ?

---

### Post by terazen on 2009-09-25
Personally I prefer Vsftpd and a firefox ftp plugin to samba.  But yeah, like Lars mentioned check if www-data has read permissions to /var/www and /var/www/index.html.

---

### Post by elklabone on 2009-09-25
ls -l www

-rwxrwx--x 1 root www-users 45 2009-09-24 12:55 index.html

ls -l index.html
-rwxrwx--x 1 root www-users 45 2009-09-24 12:55 index.html

Again, I was following the instructions from here:

[http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

Not familiar with Vsftpd, but will check that out.

My first order of business is to get apache working ...

Thanks for your help!

-Mark

---

### Post by elklabone on 2009-09-26
Could someone tell me how to restore the correct/default permissions to Apache?

I would greatly apprecaite it.

-Mark

---

### Post by mossadacity on 2009-09-27
I'm having the same problem right now... and followed the "Sharing /var/www with Samba Server" from your link :-)

ONLY FOLLOW THESE DIRECTIONS IF YOU'VE PREVIOUSLY FOLLOWED THE DIRECTIONS IN THAT LINK!

I solved it by:

Edit your group file 
```
sudo nano /etc/group
```
and add user www-data to the group www-users.
```
www-users:x:1004:(user1,user2),www-data
```

(www-data is the user apache uses)

Now we give www-data write permissions to [www..](www..).
```

sudo chown -R www-data:www-users /var/www
sudo chmod -R 771 /var/www

```

Next, we force www-data to be the SAMBA user for this directory.
```
sudo nano -w /etc/samba/smb.conf
```
go to the [www] section created earlier, and...
```

force user = www-data

```

Restart samba, and you should be good.
```
sudo /etc/init.d/samba restart
```

I'm a complete linux newbie, so please let me know if anyone has a better way.

---

### Post by Lars Noodén on 2009-09-28
> **mossadacity said:**
> 

Now we give www-data write permissions to [www..](www..).
```

sudo chown -R www-data:www-users /var/www
sudo chmod -R 771 /var/www

```


> **elklabone said:**
> ls -l www

-rwxrwx--x 1 root www-users 45 2009-09-24 12:55 index.html

ls -l index.html
-rwxrwx--x 1 root www-users 45 2009-09-24 12:55 index.html


Eklabone, the permissions are set so that the data file is not readable but is executable. :( 

You want it to look like this instead:
```

ls -l www
-rw-rw-r-- 1 root www-users 45 2009-09-24 12:55 index.html

```

A word of caution regarding **chmod** above.  If the directory is already filled with files, then **-R** will affect both the data files and the directories equally, which is not what you want. 

Here is how to treat directories and data as they need to be:

```

 sudo [find](http://linux.die.net/man/1/find) /var/www type -d -exec [chmod]([URL=http://linux.die.net/man/1/chmod) -R 775 {} \;
 sudo [find](http://linux.die.net/man/1/find) /var/www type -f -exec [chmod]([URL=http://linux.die.net/man/1/chmod) -R 664 {} \;

```

The directories need to be set executable, but the files themselves *must* not be set so unless you have something specific in mind.

---

### Post by elklabone on 2009-09-29
Lars,

I received an error when I ran your command, but after I ran:

sudo chmod -R 775 /var/www/

Everything seemed to be working...

This is just a local test server, and won't be on the internet, BTW.

However, once I access the WWW share through samba (which was my original goal), the permissions get changed to:

-rwxrw---- 1 mark www-users 88 2009-09-29 09:32 index.html

:confused:

---

### Post by elklabone on 2009-09-29
I think I got it...

I had to change the smb.conf file to keep the correct permissions on the files..

[www]
comment = www directory
path = /var/www
public = yes
writable = yes
valid users = mark
**create mask = 0775**
**directory mask = 0775**
force user = mark
force group = www-users

Again, I'm a total noob, so if I did something dumb, let me know.

-Mark

---

### Post by Lars Noodén on 2009-09-30
> **elklabone said:**
> Lars,

I received an error when I ran your command, but after...



Hmm.  I also had left the -R in there like you had. It is the recursive action that causes the problem. 

```


 sudo find /var/www type -d -exec chmod 775 {} \;
 sudo find /var/www type -f -exec chmod 664 {} \;


```

---

