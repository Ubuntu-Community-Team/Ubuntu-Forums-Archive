---
title: "apache2 mod help"
date: 2009-04-03
forum: Server Platforms
---

### Post by xkaliburx on 2009-04-03
After seeing the problems I am going to have with package support with CentOS/PHP I want to move to ubuntu-server.  I am pretty ubuntu saavy, very redhat/suse, etc. but some things are going to take a push in the right direction, so expect a few more posts with apache ;)

For the 1st one, I took our existing conf file, simply moved it, apache is setup, php and coldfusion all running / working nicely.  When I move the conf and start I am getting a startup error saying;
Invalid command 'AddExternalAuth', perhaps misspelled or defined by a module not included in the server configuration

I did see/install libapache2-mod-auth-pgsql and libapache2-mod-authnz-external but still getting the error on startup.

That should get the ball rolling, as I said, I have a few more things not working, but will keep the posts separate.

Thanks.

---

### Post by kanikilu on 2009-04-03
Did you enable the mods?
```
sudo a2enmod authnz_external
sudo a2enmod auth_pgsql
```

(I think those are the right commands. It's been a while...)

---

### Post by xkaliburx on 2009-04-03
Thanks.  I am not used to (nor did I know) you have to enable the mod's.  The 1st command worked;

sudo a2enmod authnz_external
Enabling module authnz_external.
Run '/etc/init.d/apache2 restart' to activate new configuration!

The 2nd failed;
sudo a2enmod auth_pgsql
ERROR: Module auth_pgsql does not exist!

And aptitude search shows;
i   libapache2-mod-auth-pgsql   

and I did google and confirm that is the correct syntax.  Any other ideas on getting this module installed?

---

### Post by kanikilu on 2009-04-03
Did you check to see if the mod is in /etc/apache2/mods-available/ ? I think that should have the right name that you're supposed to use in the a2enmod command.

---

### Post by kanikilu on 2009-04-03
I don't use that mod, but looking at this page:

[http://packages.ubuntu.com/hardy/i386/libapache2-mod-auth-pgsql/filelist](http://packages.ubuntu.com/hardy/i386/libapache2-mod-auth-pgsql/filelist)

Maybe this would work:

```
sudo a2enmod 000_auth_pgsql
```

?

---

### Post by xkaliburx on 2009-04-03
lol, hit reply as I found it, and your reply came up 1st.  Saw the 000 which I thought was odd, but ran the command and ...

a2enmod 000_auth_pgsql
Enabling module 000_auth_pgsql.
Run '/etc/init.d/apache2 restart' to activate new configuration!

Thanks.   As I said though ... more to come :)

I am reading up on debian apache to understand a bit more where things are and why, but naturally these are the immediates.

Thanks much.

---

### Post by kanikilu on 2009-04-03
No problem, glad you got it working :)

I had a bit of a learning curve moving to debian-based apache as well. I had previously run it on Windows (*shudder*), and was shocked at how easy it was to, for instance, get PHP installed and add Apache modules - that is, once you figure out the system ;)

---

