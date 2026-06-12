---
title: "dovecot + LDAP occasionally stops authenticating"
date: 2010-05-19
forum: Server Platforms
---

### Post by mwallette on 2010-05-19
I am running Ubuntu Server 9.10 32-bit as a mail server, using Postfix and Dovecot with LDAP authentication.  We have everything working, but once every week or two, Dovecot stops authenticating until it is restarted.  When this happens, I find...:

# head -1 /var/log/mail.err
May 16 06:33:53 mail dovecot: auth(default): userdb(<...munged...>): user not found from userdb passwd
...
#

...and here is an excerpt from /var/log/mail.log:
May 16 06:33:33 mail dovecot: pop3-login: Login: user=<...munged...>, method=PLAIN, rip=<...munged...>, lip=<...munged...>
May 16 06:33:33 mail dovecot: POP3(<...munged...>): Disconnected: Logged out top=0/0, retr=0/0, del=0/14, size=470843
May 16 06:33:53 mail dovecot: auth(default): userdb(<...munged...>): user not found from userdb passwd
May 16 06:33:53 mail dovecot: pop3-login: Internal login failure (auth failed, 1 attempts): user=<...munged...>, method=PLAIN, rip=<...munged...>, lip=<...munged...>

As you can see from mail.log, there was about a 20 second window between the last successful authentication, and when Dovecot stopped authenticating.  Unfortunately, there is nothing in mail.log to show what changed during that 20 second window.

After running /etc/init.d/dovecot restart, users can authenticate again.

I have added a post-rotate script in /etc/logrotate.d/rsyslog to restart Dovecot every morning when the mail log rotates, but I'd really rather fix the problem than work around the symptom.  Any ideas what may be causing to suddenly stop authenticating, or how to troubleshoot?

---

