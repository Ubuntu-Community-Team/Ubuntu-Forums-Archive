---
title: "Cyrus21 Imap &amp; cyradm"
date: 2005-08-16
forum: Server Platforms
---

### Post by nocturn on 2005-08-16
I installed my Ubuntu server with Cyrus Imap.  I actually managed to copy over the mailboxes from my old Gentoo server.

But I have a problem authenticating using sasldb.  I created passwords for my users, including the cyrus user using saslpasswd2 -c <user>.
sasldblistusers2 shows them fine with UserPassword.

Whe I try to connect using either an Imap client or cyradm, I get this error in the logs:
```

cyrus/imapd[975]: badlogin: localhost.localdomain[127.0.0.1] DIGEST-MD5 [SASL(-13): user not found:
 no secret in database]

```

The only authentication that works (from Evolution) is GSSAPI.  But cyradm does not seem to do this either.

I need to run cyradm to create new mailboxes, so I'm kinda stuck for now...

I saw this thread: [http://ubuntuforums.org/showthread.php?t=31858&highlight=cyradm](http://ubuntuforums.org/showthread.php?t=31858&highlight=cyradm), but it did not work for me.

---

### Post by nocturn on 2005-08-23
I fixed it!

Strange though... on this server I need to create users with:
saslpasswd2 -u mail.domain -c user

Then it works...  now on to the next challenge

---

