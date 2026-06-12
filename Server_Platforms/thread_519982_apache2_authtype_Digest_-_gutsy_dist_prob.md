---
title: "apache2 authtype Digest - gutsy dist prob"
date: 2007-08-07
forum: Server Platforms
---

### Post by petersk on 2007-08-07
[FONT="Garamond"]On my home web server, I have an entry to control access to a movie page like this:[/FONT]
[FONT="System"] 
#NameVirtualHost *:80
<VirtualHost *:80>
[INDENT]ServerAdmin me
        DocumentRoot /var/www
   <Directory "/var/www/movie/">[INDENT]
         Order allow,deny
         Allow from all
                AuthType Digest
                AuthName "peters"
                AuthUserFile /etc/apache2/svn-admin/digest-password
                Require valid-user
[/INDENT]
    </Directory>       [/INDENT][/FONT]

[FONT="Garamond"]I used htdigest to create three users.  For some reason though, apache2 doesn't let anyone other than the last user in the digest-password file log in.  Does anyone know what I'm doing wrong?  I can see three entries in the file (I had to put the space after the ":" to avoid an emoticon in this post only):[/FONT]

[FONT="System"]kurt@odin:/etc/apache2/svn-admin$ cat digest-password[INDENT]
kurt: peters:6122a237364e0c80ebc5c3
traci: peters:a57ccacfe135d2b64c9e468dc9
pefamily: peters:c1b09d0f0a2b6c6ee1[/INDENT][/FONT]


[FONT="Garamond"]so, in other words pefamily is the only user allowed to view.
Regards,
Kurt[/FONT]

---

### Post by MJN on 2007-08-08
I've not got personal experience of this but have a look at [http://httpd.apache.org/docs/2.0/mod/mod_auth_digest.html](http://httpd.apache.org/docs/2.0/mod/mod_auth_digest.html) where it appears to be suggesting you should be using the AuthDigestFile (as opposed to AuthUserFile) and AuthDigestDomain directives.

I would be surprised if correcting this didn't solve your problem - you're probably lucky to have it even partly working! ;)

Mathew

P.S. Note the caveat re browser support.

---

### Post by petersk on 2007-08-08
Thanks for the thought, but &#8220;AuthDigestFile&#8221; is invalid in Apache 2.2, use &#8220;AuthUserFile&#8221; according to the things I found.  That's why I'm using AuthUserFile.

[http://forums.macosxhints.com/archive/index.php/t-57430.html](http://forums.macosxhints.com/archive/index.php/t-57430.html)

[http://ubuntuforums.org/showthread.php?t=157415](http://ubuntuforums.org/showthread.php?t=157415)

[http://people.debian.org/~terpstra/message/20070708.213002.dcf795ad.en.html](http://people.debian.org/~terpstra/message/20070708.213002.dcf795ad.en.html)

[http://httpd.apache.org/docs/2.2/upgrading.html](http://httpd.apache.org/docs/2.2/upgrading.html)

---

### Post by MJN on 2007-08-09
Ah, okay, sorry - I'm out of ideas. As I say I have no experience of Digest authentication (or 2.2 for that matter) so can only go off the examples.

Good luck!

Mathew

---

