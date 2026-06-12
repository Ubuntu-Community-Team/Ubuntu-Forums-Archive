---
title: "Dovecot IMAP remote connection problems"
date: 2006-07-14
forum: Server Platforms
---

### Post by marcndd on 2006-07-14
I have dovecot configured as an IMAP server, and connect to it with email clients locally and remotely. I have done this without a problem on Breezy, and I am pretty sure (but not positive) it worked initially when I upgraded to Dapper. I noticed a couple of dovecot updates since then.

I normally just do email with an email client locally on the Ubuntu desktop, so I don't know exactly when this problem started. What I do know is that now whenever I try to connect from a remote system my email client says something to the effect that "logins are disabled on the server and maybe I need to enable SSL or TLS authentication". I am using plaintext authentication. If it matters my email client on all systems is Seamonkey, which is basically the same as Mozilla or Thunderbird.

I am pretty sure I am not running a firewall (IP Chains or whatever) on the system (unless the Dapper upgrade slipped one in), as I am behind a NAT router. Connecting from the local system still works, which is what is so weird, it is only connections from remote systems that have the problem. And it worked from remote systems until recently.

I looked through the /etc/dovecot/dovecot.conf file and didn't see anything that looked too suspicious, although I manually set the maximum number of simultaneous connections allowed to be sure it allows several. (I almost always leave the local email client running). I did try shutting down the local email client, but the remote still couldn't connect.

The system is up-to-date, there are no dovecot updates available. I Googled and searched the forum, and didn't see anything.

Any ideas?

---

### Post by nagilum on 2006-07-14
Are you sure you connect to the server via a SSL encrypted connection, i.e. port 993? Dovecot disallows plaintext authentication on non-encrypted channels by default. You can change the setting in the dovecot.conf file (search for disable_plaintext_auth) although this is not recommended of course. Was there any helpful information in the log files?

---

### Post by marcndd on 2006-07-15
OK, that did it.  In my dovecot.conf file "disable_plaintext_authentication = yes" was commented out with a "#".  I assumed this meant "uncomment this like to disable plaintext authentication".  I was wrong.

Apparently it still allowed it locally for some reason.

So it wasn't explicitly set in dovecot.conf at all.  When I explicitly set it to "no", then all was well.  So I guess they changed the default value recently.

Thanks for the help!

---

### Post by MJN on 2006-07-18
[LEFT][SIZE=2]> **marcndd said:**
> Apparently it still allowed it locally for some reason.[/SIZE][/LEFT]
[SIZE=2][/SIZE] 
[LEFT][SIZE=2]Plaintext logins are allowed locally because your username/password are not leaving the box (i.e. not traversing a network) hence there's no requirements for them to be encrypted.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]However, and more to the point, are you sure you want to allow non-encrypted (TLS) plaintext logins from remote clients?[/SIZE][/LEFT]
[SIZE=2][/SIZE] 
[LEFT][SIZE=2]Mathew[/SIZE][/LEFT]

---

