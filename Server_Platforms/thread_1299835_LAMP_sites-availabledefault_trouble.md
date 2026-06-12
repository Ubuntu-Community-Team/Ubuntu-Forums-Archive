---
title: "LAMP sites-available/default trouble"
date: 2009-10-24
forum: Server Platforms
---

### Post by J V on 2009-10-24
I'm setting up a development server that should only be loadable by localhost, the problem is that in doing so I am now getting constant 403 errors on everything but /phpmyadmin...

Here is my /etc/apache2/sites-available/default:
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/user/www
    <Directory /home/user/www/>
        AllowOverride All
        Order deny,allow
        deny from all
        allow from 127.0.0.1
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined


</VirtualHost>
```Could someone explain what I did wrong, and help fix it? Thanks...

---

### Post by J V on 2009-10-26
Oh cmon, I know you guys know apache :)

---

### Post by Lars Noodén on 2009-10-26
Well [403 Forbidden](http://tools.ietf.org/html/rfc2616#section-10.4.4) means that the web server does not have read access to the files and or directories in question.  You can take a closer look at the error log to be sure where the request is failing.  

Then look at your virtual host, the one in *sites-enabled*.  It /home/user/www/ actually readable by www-data (or whatever your web sever runs as) ?

[INDENT][FONT="Courier New"]sudo -u www-data ls /home/user/www/[/FONT][/INDENT]

---

### Post by kevin11951 on 2009-10-26
this works for me:

```
sudo chown -R www-data:www-data /var/www
```
```
sudo chmod -R 0755 /var/www
```

I am sure there is a security problem with that setup, but if it works, then at least we know we are on the right track.

---

### Post by J V on 2009-10-26
Ok, kevin's code worked, but what do I do about it? Do I have to list www-data as owner group every time I add a file?

Can I change the contents without root permissions? How exactly do I give apache permissions but keep ownership?

(755 works without having to change owner/ownergroup)

---

### Post by Lars Noodén on 2009-10-27
Actually that sets execute permissions for the files, not just the directories.

'find' will allow you to apply the permissions differently to the files and directories:

```

# set directories so user and group can read+write, everyone can read
# files created in directory inherit group membership of directory's group
sudo find /var/www -type d -exec chmod 2775 {} \;

# set files so user and group can read+write, everyone can read
sudo find /var/www -type f -exec chmod 0664 {} \;

```

Make a group 'webmasters' or something like that  and add www-data to it, and anyone authorized to work on the web pages.  That still leave the problem of umask and active group.

---

### Post by J V on 2009-10-27
Well atm all the directories are at 755, files at 744, without owner being www-data, and the page loads...

Do I have to let everyone read like this?

---

### Post by Lars Noodén on 2009-10-27
You have to let at least the user or group web server is using read the directories (r-x) and files (r--)

I'm seeing a way to do what you want now, but it may be some work to set up if it is too new.  EXT supports POSIX access control lists (ACL).  Really ACLs of some kind are the way to go for group work on any share file system.  

Check to see that the partition /var/www is mounted in has ACLs available:
```

mount -l
. . .
/dev/sda7 on /var/www type ext4 (rw,nosuid,nodev,relatime,**acl**)
. . .

```

/var/www/ should be mounted with the rw,nosuid,nodev,relatime,acl options.  

Then set the acls, including the defaults:

```

$ sudo setfacl --set default:user::rwx,default:group::r-x,default:group:webwork:rwx /var/www/

$ getfacl /var/www/
user::rwx
group::r-x
**group:webauthors:rwx**
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
**default:group:webauthors:rwx**
default:mask::rwx
default:other::r-x

```

After that, anyone in the group 'webauthors' should be able to create, read or write their own files or those of others.  New directories will, unless specified otherwise, inherit those options.

More on POSIX acls:
[acl](http://manpages.ubuntu.com/manpages/karmic/en/man5/acl.5.html)
[setfacl](http://manpages.ubuntu.com/manpages/karmic/en/man1/setfacl.1.html)
[getfacl](http://manpages.ubuntu.com/manpages/karmic/en/man1/getfacl.1.html)

---

### Post by J V on 2009-10-27
I was thinking more of just assigning it the ownergroup www-data...

Edit: whadaya know, it worked...

---

### Post by Lars Noodén on 2009-10-27
> **J V said:**
> I was thinking more of just assigning it the ownergroup www-data...


Great.

Later, if you have several users creating and deleting files and directories, the acl option may be good to remember.

---

### Post by J V on 2009-11-17
Good thing I didn't [SOLVED] this...

Sorry to dig up an old thread but its pretty much the same problem on a new PC...

Everything about the config files is the same (except the documentroot... Its correct, trust me...) and the permissions have been set to 777 with no success...

I'm clueless here... Start new thread?

---

