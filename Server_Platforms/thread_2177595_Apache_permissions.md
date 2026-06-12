---
title: "Apache permissions"
date: 2013-09-29
forum: Server Platforms
---

### Post by banedon on 2013-09-29
This has been probably done to death, but I'm struggling with the folder permissions for /var/www on apache (ubuntu x64, v13.04, LAMP)

In a previous post I mentioned having added r/w permissions to www-data and was advise by Lars Nooden that this was a security issue.

As such I'm trying to add the correct permissions and so have managed to unearth this from a seperate post on these forums - but it doesn't work unforutnately (when I use a browser I get a permission error):

```
groupadd webmasters

chown root:webmasters /home/www

find /home/www -type d -exec chmod u=rwx,g=rwxs,o=rx {} \;

find /home/www -type f -exec chmod u=rw,g=rw,o=r {} \;
```


Would this be more appropriate?

```
addgroup webmasters
adduser $USER webmasters
chown -R root:webmasters /var/www
find /var/www -type f -exec chmod 664 {} \;
find /var/www -type d -exec chmod 775 {} \;
find /var/www -type d -exec chmod g+s {} \;
```

Cheers!

---

### Post by banedon on 2013-09-29
I did the above anyway and it seems to work.  Can anyone advise if this is safe?

---

### Post by Lars Noodén on 2013-10-01
Looks fine to me. ;)

The crucial point is that the web server, running as www-data, should not have write access to any directories that are being served.  It's kind of a variation on W^X or least privilege.

If at some point you do need the web server to write to certain directories, consider adding yet another group or user and making use of [SuexecUserGroup](http://httpd.apache.org/docs/2.4/mod/mod_suexec.html#suexecusergroup) to compartmentalize the write access.

---

### Post by banedon on 2013-10-02
> **Lars Noodén said:**
> Looks fine to me. ;)

The crucial point is that the web server, running as www-data, should not have write access to any directories that are being served.  It's kind of a variation on W^X or least privilege.

If at some point you do need the web server to write to certain directories, consider adding yet another group or user and making use of [SuexecUserGroup](http://httpd.apache.org/docs/2.4/mod/mod_suexec.html#suexecusergroup) to compartmentalize the write access.

Hi Lars

I suspected as much, but at this stage would rather check just to be sure as I'm totally new to this - better safe than sorry :)
The website is now up and running.

One thing that really puzzles me is that Ubuntu 13.04 seems to have an old version of Apache installed with a known security flaw... :o

---

### Post by SeijiSensei on 2013-10-03
Security fixes are often "backported" without a major version change.  Take a look at the [Changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4/changelog") for the version of the apache2 package for 12.04LTS.  The backport incremented the final version number from 1ubuntu1.3 to 1ubuntu1.4.  This is a common policy; RedHat applies security updates in the same manner.

Some applications require that the web server be able to write into the publicly visible directory tree, WordPress being one.  It makes it easier to manage updates, uploaded files, and themes from the application's "Dashboard," but it always bothers me from a security perspective.  

When I write applications in PHP that require the server to write a file somewhere, I always define a directory outside the publicly-visible web tree that is owned only by the web server user ("www-data" in Ubuntu).  Third-party applications like WP cannot do that because many people with hosting accounts cannot write outside the public directory.

---

### Post by Lars Noodén on 2013-10-03
To add to what SeijiSensei wrote, Debian, the parent of Ubuntu, is even better at keeping patches and upgrades separate.  Patches will generally only fix a specific problem but leave the service or tool otherwise the same.  Upgrades can include major or minor changes to functionality (even adding or removing), change the UI or API, fix and/or break things, and even make changes to licensing.  Some vendors will ransom their patches with upgrades to force the upgrades on customers.  From a maintenance perspective, especially on servers, changes are undesireable and surprises are the worst so that's one reason for the LTS releases.

---

### Post by banedon on 2013-10-05
I was just a little bit surprised was all as you'd think as the latest OS version it would contain the latest (stable) packages.  I'm only just getting used to how Linux does business hence the questions. Thanks to both of you for your explanation.

On a slightly different subject (but from earlier in the thread), I found this invaluable post which explains permissions very well for beginners (for those in the same boat as me :)):
[http://www.linux.org/threads/file-permissions-chmod.4094/](http://www.linux.org/threads/file-permissions-chmod.4094/)

---

