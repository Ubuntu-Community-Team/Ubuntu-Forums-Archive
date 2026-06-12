---
title: "Debian based LDAP setup Howto found :)"
date: 2006-07-21
forum: Server Platforms
---

### Post by cptnapalm on 2006-07-21
I had been unsuccessful in getting ldap to work at all until I bumped into this:

[http://enterprise.linux.com/article.pl?sid=05/09/15/1930256](http://enterprise.linux.com/article.pl?sid=05/09/15/1930256)

It is Debian based, but as we are using a Debian based distro, it seems to work fine.  What I do not know is if using the traditional tools of adduser will use ldap instead.  I suspect not, but I am not yet well versed enough to figure out how to do that.

I have been trying to use lat to do ldap administration stuff.  I can see the records okay, but any attempted modification throws a fit and crashes the program.  (Why does it seem like I have more program crashes with mono apps than any other?)

One word of caution I saw was that root needs to not need ldap since if you break something, there will be no login for you!

Ultimately, what I would like to have up and running is an ldap server which syncs local and samba accounts with their passwords across my local machines... Might take some doing.

---

### Post by compbrain on 2006-07-21
Hi.

So, that howto looks like its pretty decent. Adduser and such will not work, instead you will need some custom utils, or a management app. I am told phpLdapAdmin ([http://phpldapadmin.sourceforge.net](http://phpldapadmin.sourceforge.net)) works quite well, but we do not use that tool here.

---

