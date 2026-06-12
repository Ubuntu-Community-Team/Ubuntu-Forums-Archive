---
title: "maildrop and ldap support"
date: 2005-11-15
forum: Server Platforms
---

### Post by mmerlone on 2005-11-15
Hello all,

I am setting up a mail server with postfix, squirrelmail, courier-imap/pop, etc with virtual users stored on an OpenLDAP database and Ubuntu 5.10 with no other sources than the official ones. I set maildrop as postfix's MDA, but it seems to be ignoring my ldap setup.

I already have my imap part working ok, so authdaemon and authldaprc are set ok, just maildrop seems to be ignoring my ldap setup.

While running maildrop -v:

[FONT="Courier New"]root@carvalho:/etc/courier # /usr/bin/maildrop -v
maildrop 1.5.3 Copyright 1998-2003 Double Precision, Inc.
GDBM extensions enabled.
Maildir quota extension enabled.
This program is distributed under the terms of the GNU General Public
License. See COPYING for additional information.
root@carvalho:/etc/courier #[/FONT]

ldd over maildrop binary reports no use of any ldap lib. When I submit a message to postfix:

[FONT="Courier New"]Nov 15 22:25:18 carvalho postfix/pipe[15455]: 222061A9831: to=<marcio@domain.tld>, relay=maildrop, delay=0, status=deferred (temporary failure. Command output: /usr/bin/maildrop: Unable to open mailbox. )[/FONT]

and it doesn´t touch my ldap server - according to local4 logs. Searching trough maildrop´s changelog:

[FONT="Courier New"]2004-11-04  Mr. Sam  <mrsam@courier-mta.com>
    * maildrop: remove maildrop's mysql and ldap modules, replace with
    Courier Authentication Library.[/FONT]

So, I assume that if authdaemon is ok, everything else should also.

Any idea on how to glue those pieces together? Thanks for any hint, rtfm, etc in advance.

Best regards,

-- 
Marcio Merlone

---

### Post by calt129 on 2005-12-20
Postfix runs in a chrooted environment AFAIK. I had similar problems with sasld due to this. Check if dropmail can be accessed from Postfix's chroot-dir (default: /var/spool/postfix)

---

### Post by seppe on 2006-03-23
I've got the same problem...
I suspect that maildrop package hasn't been compiled with LDAP support: in a quick survey on breezy's maildrop build log I couln't find any reference to a "--enable-maildropldap" configuration parameter... Moreover I've found an [howto page]("http://deb.riseup.net/mail/buffy/maildrop/") (on maildrop with Debian) where it asserts that
> We need to compile maildrop from source because the debian package version does not include support for ldap
Maybe the package mantainer could give us a clue...
The only solution I can see at the moment is compiling the source package with the LDAP support.

---

