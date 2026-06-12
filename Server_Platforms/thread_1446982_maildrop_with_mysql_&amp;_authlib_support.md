---
title: "maildrop with mysql &amp; authlib support?"
date: 2010-04-04
forum: Server Platforms
---

### Post by pot_roast on 2010-04-04
I'm not having any luck today getting maildrop working. 

Ubuntu (Hardy) and everything is from aptitude.

If I use 2.0.3 (the version aptitude serves up) I get this:

maildrop 2.0.3 Copyright 1998-2005 Double Precision, Inc.
GDBM extensions enabled.
Courier Authentication Library extension enabled.
Maildir quota extension enabled.
This program is distributed under the terms of the GNU General Public
License. See COPYING for additional information.

maildrop: authlib: groupid=5150
maildrop: authlib: userid=5150
maildrop: authlib: logname=redacted@redacted.org, home=/home/vmail/redacted.org/redacted, mail=/home/vmail/redacted.org/redacted/.maildir/
/usr/bin/maildrop: You are not a trusted user.

This is after I made maildrop setuid root. It seems that the version aptitude serves us was compiled without the --enable-trusted-users flag at compile time. There appears to be no way around this other than to recompile, according to Sam V, the author of the program. So I'm off to compile my own.

/usr/local/bin/maildrop -v
maildrop 2.4.2 Copyright 1998-2005 Double Precision, Inc.
Maildir quota extension are now always enabled.
This program is distributed under the terms of the GNU General Public
License. See COPYING for additional information.

My compile flags: ./configure --prefix=/usr/local/ --enable-maildropmysql --enable-trusted-users="root postfix vmail" --enable-syslog=1 --enable-maildrop-uid=5150 --enable-maildrop-gid=5150 --with-mysqlconfig=/etc/maildrop/maildropmysql.cf

I set export LDFLAGS="-L/usr/include/mysql" and export CPPFLAGS="-I/usr/include/mysql" before hand and I have libmysqlclient-dev installed.

Since I can't get it to compile with mysql & authlib, I get this:
echo "test" | maildrop -V 9 -d [email]redacted@redacted.org[/email]
Invalid user specified.

It never talks to mysql and obviously isn't authenticating. The aptitude version does talk to mysql, but can proceed no further because it hits that "trusted user" issue.

Are the authlib & mysql libraries somewhere else? There are
How can I solve this? Have any of you successfully compiled maildrop to work with courier-authlib and mysql? This is driving me nuts. 
I'm using courier-imap with virtual users in mysql. This setup has worked just fine for a long time, but I now need to add server side filtering. It seems like I'm almost there....

Help!

---

### Post by KB1JWQ on 2010-04-04
This may not help you overly much, but I had similar issues with mysql support when FreeBSD 8 dropped.  My solution was to migrate to Dovecot-- it was a painless migration, this sort of thing "just worked" and the speed boost was unreal.

---

### Post by pot_roast on 2010-04-08
> **KB1JWQ said:**
> This may not help you overly much, but I had similar issues with mysql support when FreeBSD 8 dropped.  My solution was to migrate to Dovecot-- it was a painless migration, this sort of thing "just worked" and the speed boost was unreal.

Dovecot is just the IMAP server. My IMAP server is working fine. It's maildrop that is the little turkey. ;-)

After much coaxing, I did eventually get it working. I had to tweak some setuid permissions to get everything to cooperate. The next task was getting the Squirrelmail "serversidefilter" plugin up and running. It seems like it's almost abandonware, though. I was going to switch to Roundcube but I really needed the web frontend for Maildrop. 

Anyway, I finally got everything working, and now I'm scared to death of migrating everything to new hardware. haha.

---

