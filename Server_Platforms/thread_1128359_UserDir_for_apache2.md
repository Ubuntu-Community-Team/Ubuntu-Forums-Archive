---
title: "UserDir for apache2"
date: 2009-04-17
forum: Server Platforms
---

### Post by xkaliburx on 2009-04-17
As I continue to migrate over and learn from RH, my next error on apache startup is the following;

Invalid command 'UserDir', perhaps misspelled or defined by a module not included in the server configuration

The only apache mod that looks remotely close is libapache2-mod-ldap-userdir.  I did install for the heck of it but no good apache still won't start.

I will continue to google/read but these are the things others have hit and fixed easy enough and hopefully is a simple answer.

Thanks

---

### Post by Bachstelze on 2009-04-17
What's the ouput of this command?

```
sudo a2enmod userdir
```

---

### Post by xkaliburx on 2009-04-17
sudo a2enmod userdir
Enabling module userdir.
Run '/etc/init.d/apache2 restart' to activate new configuration!

naturally the next;
Invalid command 'RewriteEngine',

Is there a list of all the mod's pre-installed that need to be enabled, etc.  I don't want to keep asking the same thing, how to enable this, etc. Well, I don't mind, but rather save the forum's for better questions  :)

Thanks

---

### Post by Bachstelze on 2009-04-17
If you run [font="monospace"]sudo a2enmod[/font] alone, you will have a list of all available modules and you will be propted for those you want to activate.

---

### Post by xkaliburx on 2009-04-17
Very cool.  Just found the mods-avail folder.  There is a lot of subtle diff's between a redhat OS, but I'm still getting through it.

Thanks for the quick responses, after a few more mod's things now seem to be starting ...

Lr

---

### Post by rrll1977 on 2009-05-18
Hi,

Has anybody got to work mod_rewrite with mod_userdir

I can't get mod_rewrite to work with user's pages on /home/user/public_html, although it appears to work fine for server root pages on /opt/lampp/htdocs

Regards

---

