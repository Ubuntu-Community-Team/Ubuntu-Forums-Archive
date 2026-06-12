---
title: "Flurdy/Postfix -- imapd: LOGIN FAILED"
date: 2009-08-11
forum: Server Platforms
---

### Post by localfiend on 2009-08-11
I'm relatively new to linux, and apparently too ambitious for my own good.

I recently set up a web-server on ubuntu, and was so pleased with my success's involving apache2 that I have since tried my hand at setting up an email server.

I've been going off of Flurdy's excellent guide here:

[http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html)

and after several days of troubleshooting I thought I had finally succeeded and worked out all the little bugs.....

I'm using Ubuntu Server 9.04 x64 - Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey + phpMyAdmin.

After some horrible days of learning how to install all of the above programs, and learning how to use mysql I got my server to successfully send mail to my hotmail account using telnet directly off the server.  I am also able to send mail locally from one account to the other via telnet. 

However, I can not log onto my mail server using Thunderbird, or Microsoft outlook.

I have dubugging on full (as far as I know) and here's the error I get (from the mail.* logs): 

```
Aug 11 20:10:01 mydomain imapd: LOGIN FAILED, user=localfiend, ip=[::ffff:myip]
```

I've spent the whole day searching google, and rechecking all of my files to see what my problem could possibly be with no luck.  I'm using mySQL to store the virtual users, domains ect...  I've tried switching between clear text and encrypted passwords, enabling and disabling tls.  phpMyAdmin works, so its easy to check my mail database for errors, but I can't seem to find any.  It's got me pulling out my hair and any help would be appreciated.

Let me know if there is any other logs or configuration information that may help with a diagnosis.

Thanks

---

### Post by localfiend on 2009-08-12
Bump, just to get to the first page again.

---

### Post by localfiend on 2009-08-12
Got a quick update for anyone who is paying attention.  This was driving me nuts so I grabbed another machine I had lying around with a x64 capable processor and started a whole new install from scratch.  While rebuilding the new server I found a typo (repeated debug line) in /etc/courier/authdaemonrc that was preventing me from getting all the information I needed.   

So, after repairing the original machine I now have some new errors to check:

```
Aug 12 15:37:57 mydomain imapd: Connection, ip=[::ffff:myip]
Aug 12 15:38:03 mydomain authdaemond: received auth request, service=imap, authtype=login
Aug 12 15:38:03 mydomain authdaemond: authmysql: trying this module
Aug 12 15:38:03 mydomain authdaemond: authmysqllib: connected. Versions: header 50067, client 50075, server 50075
Aug 12 15:38:03 mydomain authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'localfiend'  AND (enabled=1)
Aug 12 15:38:03 mydomain authdaemond: zero rows returned
Aug 12 15:38:03 mydomain authdaemond: no password available to compare
Aug 12 15:38:03 mydomain authdaemond: authmysql: REJECT - try next module
Aug 12 15:38:03 mydomain authdaemond: FAIL, all modules rejected
Aug 12 15:38:03 mydomain imapd: LOGIN FAILED, user=localfiend, ip=[::ffff:myip]
Aug 12 15:38:13 mydomain imapd: LOGOUT, ip=[::ffff:myip], rcvd=55, sent=484
```

I think that with these errors and google I may be able to figure something out.  Moral of the story is to triple check your debug code lines so you can be absolutely sure they don't have a duplicate.

---

### Post by snarf77 on 2010-01-02
Hi LocalFiend,

I just followed the excellent how to from Flurdy but with a ubuntu 9.10 desktop base.

After fixing some typo problems in different config files I m now stuck with exactly the same problem as yours:

Jan  2 12:19:40 fll imapd: LOGIN FAILED, user=toto, ip=[::ffff:127.0.0.1]
Jan  2 12:19:40 fll authdaemond: zero rows returned
Jan  2 12:19:40 fll authdaemond: no password available to compare
Jan  2 12:19:40 fll authdaemond: authmysql: REJECT - try next module
Jan  2 12:19:40 fll authdaemond: FAIL, all modules rejected
Jan  2 12:19:47 fll imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=71, sent=499

However the first test in local with telnet are OK, directories are created and mail.log do not mention any errors when posting locally with telnet. 
But it is still impossible for me to configure IMAP client...

nevertheless authtest command for login "toto" gives:

Authentication succeeded.

     Authenticated: toto@emailaddress  (uid 5000, gid 5000)
    Home Directory: /var/spool/mail/virtual
           Maildir: /var/spool/mail/virtual/XXX/
             Quota: (none)
Encrypted Password: sdtrusfX0Jj66
Cleartext Password: (none)
           Options: (none)

Did you have any answer or find anything concerning this problem since 6 month this question was posted ??

thanx in advance for any help

Snarf

---

### Post by bonfire89 on 2010-08-30
same problem here. Looking to find out how to set up authentication I suppose.

---

### Post by sh1ny on 2010-08-31
[http://wiki.dovecot.org/](http://wiki.dovecot.org/)

Use dovecot instead of courier and authentication will be a lot simpler + you will get a more stable, feature rich imap/pop3 server. And the wiki has all the guides you'll ever need.

---

