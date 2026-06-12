---
title: "Securing Mythweb with Apache2 in Edgy"
date: 2007-04-15
forum: Server Platforms
---

### Post by smitty_srs on 2007-04-15
Hi all!

I'm pretty new to Ubuntu and Linux, but I just setup a MythTV backend on a Dell Power Edge 600SC and am running frontends on XBMC and my Ubuntu/XP laptop.  The 3rd go at it was a charm and I got Mythweb working as well.  What I'm trying to do now is secure Mythweb using Apache2.conf.  I've read several places that this is the preferred method of adding password protection to Mythweb, but all the how-to's don't seem to follow my setup very well.  I'm a complete noob to apache so any help would be much appreciated!

---

### Post by newlinux on 2007-04-15
I can't remember exactly what I did, but it was something similar to the following...

i modified /etc/apache2/sites-enabled/mythwebdir

to something like:
```

<Directory "/var/www/mythweb">
    Options         FollowSymLinks
    AllowOverride   All
    AuthType        Basic
    AuthName        Restricted
    AuthUserFile    FILENAME
    Require         valid-user
</Directory>
```

AuthUserFile can be whatever you want, but make sure to set proper permissions on it. I created it with:
```

htpasswd -c FILENAME USERNAME
```

username is what you want to username to be. It will then ask you for a password. If you want to add more users then you can do the command above without -c and with a different username... FILENAME is the full path to the location of the file...

Hope this helps... I think this is what I did... But I do remember looking at multiple places that didn't exactly apply.... I also protected phpmyadmin as well similarly.

---

### Post by smitty_srs on 2007-04-15
I tried that and and it seemed to go pretty good, so I went to restart apache and I get the following error:

Syntax error on line 1 of /etc/apache2/sites-enabled/mythweb-pword:
Invalid command 'USERNAME:GOBLEEGOOK', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                         [fail]
Any ideas?

---

### Post by newlinux on 2007-04-15
Perhaps there is more that I did before that.

what does 

```
ls -l /etc/apache2/sites-enabled 
```

output?

---

### Post by smitty_srs on 2007-04-15
total 4
lrwxrwxrwx 1 root root 36 2007-04-13 22:11 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 39 2007-04-13 22:11 mythwebdir -> /etc/apache2/sites-available/mythwebdir
-rw-r--r-- 1 root root 21 2007-04-15 19:17 mythweb-pword

---

### Post by newlinux on 2007-04-15
the only real difference I see is there is that the file that contains my password is owned by www-data, and only www-data has read and write access. Did you make the changes on mythwebdir I wrote above a couple days ago? The file date is from 2 days ago, so I just want to make sure you made those changes...

try
```

sudo chown www-data /etc/apache2/sites-enabled/mythweb-pword
 
```

---

### Post by smitty_srs on 2007-04-15
I tried
```

sudo chown www-data /etc/apache2/sites-enabled/

```
as well as what you suggested and there was no change.

---

### Post by newlinux on 2007-04-17
Unfortunately, I'm pretty sure that's all I did... Other than that, I have my password file located in a different place. Try putting the password file someplace other than in the apache2 config file areas, like someplace in your home directory. The error may be due to apache trying to read your password file as a config file because of its location. Don't forget to change the pointer in mythwebdir and delete the password file from its current location

---

