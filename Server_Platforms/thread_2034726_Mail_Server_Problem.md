---
title: "Mail Server Problem"
date: 2012-07-28
forum: Server Platforms
---

### Post by jonedney on 2012-07-28
Howdy,

So after taking a break from working on my VPS, I've decided to go ahead and get some things working on it.  I've managed to get everything from Apache to MySQL, from Bind to phpMyAdmin working.  I installed ISPConfig to manage the accounts and such.  This is running on Ubuntu 12.04 LTS, of course.

I installed SquirrelMail, and when trying to send an email, I receive this error.

```
Message not sent. Server replied:  Service not available, closing channel
421 4.3.0 collect: Cannot write ./dfq6T1wNpj007786 (bfcommit, uid=0, gid=110): No such file or directory
```

Additionally, this is what mail.err has:
```
Jul 28 02:35:12 server postfix/master[3072]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 28 03:15:57 server postfix/master[12748]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 28 04:06:59 server sm-mta[15535]: q6S06x5k015535: SYSERR(root): collect: Cannot write ./dfq6S06x5k015535 (bfcommit, uid=0, gid=110): No such file or directory
Jul 28 05:55:28 server sm-mta[17285]: q6S1tS6R017285: SYSERR(root): collect: Cannot write ./dfq6S1tS6R017285 (bfcommit, uid=0, gid=110): No such file or directory
Jul 29 05:58:24 server sm-mta[7786]: q6T1wNpj007786: SYSERR(root): collect: Cannot write ./dfq6T1wNpj007786 (bfcommit, uid=0, gid=110): No such file or directory

```

I followed a turorial when installing ISPConfig and here is what was installed in relation to mail services.

```
apt-get install **postfix postfix-mysql** **postfix-doc** mysql-client  mysql-server openssl **getmail4 **rkhunter binutils **dovecot-imapd**  **dovecot-pop3d dovecot-mysql dovecot-sieve** sudo
```

I've done some reading around the net about this being a permission-based problem, and I've seen some about it being a problem with the sendmail portion of postfix.

Any help would be awesome.

---

### Post by jonedney on 2012-07-30
Hello,

I appreciate everyone taking a look at my post.  I"ve taken the post/issue to the ISPConfig community forums, since it's their control panel that handles the mail server.

Once I get some direction and find resolution, I will post something in case someone comes across the same issue.

---

### Post by SeijiSensei on 2012-07-31
> Jul 28 02:35:12 server postfix/master[3072]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 28 03:15:57 server postfix/master[12748]: fatal: bind 0.0.0.0 port 25: Address already in use

Something else besides postfix is listening on the SMTP port, 25.  See if you can figure out what that is.  Alternatively postfix keeps trying to respawn itself for some reason and collides with the already-running instance.

What happens if you try "telnet localhost 25"?  If you can connect, try sending a message manually like this:

```

$ [COLOR="Blue"]telnet localhost 25[/color]
[Postfix banner]
[COLOR="Blue"]EHLO localhost[/COLOR]
[Postfix Hello, localhost, ...]
[COLOR="Blue"]MAIL FROM: root[/COLOR]
[OK]
[COLOR="Blue"]RCPT TO: root[/COLOR]
[OK]
[COLOR="Blue"]DATA[/COLOR]
[banner]
[COLOR="Blue"]hello
.
[/COLOR]
[confirmation or error]
[COLOR="Blue"]QUIT[/COLOR]

```

---

