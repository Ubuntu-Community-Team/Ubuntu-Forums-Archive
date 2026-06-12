---
title: "Deferred: Connection timed out with mailserver2.domain.com"
date: 2013-04-30
forum: Server Platforms
---

### Post by hash4all on 2013-04-30
Expert,

I am newbie to sendmail.
Any expert to reply on the below error for how to fix it.

SMTP relay error.

root@mailserver3:~# mailq
MSP Queue status...
/var/spool/mqueue-client is empty
                Total requests: 0
MTA Queue status...
                /var/spool/mqueue (3 requests)
-----Q-ID----- --Size-- -----Q-Time----- ------------Sender/Recipient-----------
r3U4eRSH223276   410812 Tue Apr 30 04:40 MAILER-DAEMON
                 (reply: read error from mailserver2.domain.com.)
                                         <user1@domain.com>
r3U0S9Mt115878*  408752 Tue Apr 30 00:28 <user@domain.com>
                 (Deferred: Connection timed out with mailserver2.domain.com)
                                         <user@otherdomain.com>

root@mailserver3:~# tail -f /var/log/mail.err
Apr 28 22:02:00 mailserver3 sm-mta[16851]: r3SL202f016851: SYSERR(root): collect: read timeout on connection from server.domain.com, from=<user1@domain.com>
Apr 29 22:01:47 mailserver3 sm-mta[3474]: r3TL1ks4003474: SYSERR(root): collect: read timeout on connection from server.domain.com, from=<user1@domain.com>

mailserver3 is able to connect mailserver2 as shown below.

root@mailserver3:~# telnet mailserver2 25 < /dev/null 2>&1 | grep "Connected" | awk '{print $1}'
Connected

Thanks

---

### Post by hash4all on 2013-04-30
Any one is there to reply on this error for how to fix it.

Thanks

---

### Post by darkod on 2013-04-30
First, one hour is not that long. Please wait longer before bumping the thread.

It says something about relay error. I haven't worked with sendmail also.

Are you trying to send email from mailserver2 directly, or trying to relay through it? Relaying should be disabled by default, so if you want to relay another server through it, you will have to look into the relay settings.

Do you have any firewall that might be blocking the connection?

---

### Post by hash4all on 2013-04-30
From mail server2 its trying trough relay.

If relay is disabled by default, could you please let me know how to enable it.
No firewall in between.

Thanks

---

### Post by darkod on 2013-04-30
Sorry but I don't have hand on experience with sendmail. The most I can help is what google will tell you too:
[http://www.google.es/search?q=sendmail+relaying&oq=sendmail+relaying&sugexp=chrome,mod=17&sourceid=chrome&ie=UTF-8](http://www.google.es/search?q=sendmail+relaying&oq=sendmail+relaying&sugexp=chrome,mod=17&sourceid=chrome&ie=UTF-8)

---

### Post by SeijiSensei on 2013-04-30
Try simulating a complete SMTP exchange with telnet using the identical From and To addresses in the messages that were not accepted. Let's assume the computer that is making the connection is mailserver3.domain.com:

```

[color=blue]telnet mailserver2.domain.com 25[/color]
[server replies with banner]
[color=blue]ehlo mailserver3.domain.com[/color]
[server confirms]
[color=blue]mail from: user@domain.com[/color]
[server replies]
[color=blue]rcpt to: anotheruser@domain.com[/color]
[server replies]

```

(Type the items in blue.)  By now the server should reject the connection, either at the "mail from" command or at the "rcpt to" command.  

What does /var/log/mail.log on mailserver2 say when messages are refused?

---

### Post by hash4all on 2013-04-30
[COLOR=#0000ff]root@mailserver3:~# telnet mailserver2 25[/COLOR]
Trying IP Address...
Connected to mailserver2.domain.com.
Escape character is '^]'.
220 ****************************************************************************************************************************************************************************************************************
[COLOR=#0000ff]ehlo mailserver3.domain.com
250-mailserver2.domain.com Hello mailserver3.domain.com [IP Address], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-XXXXXXXXA
250 XXXB
mail from: [email]user@domain.com[/email]
250 2.1.0 [email]user@domain.com[/email]... Sender ok
rcpt to: [email]user@otherdomain.com[/email]
250 2.1.5 [email]user@otherdomain.com[/email]... Recipient ok
DATA
354 Enter mail, end with "." on a line by itself
.
250 2.0.0 r3UHXVTI027863 Message accepted for delivery
QUIT
221 2.0.0 mailserver2.domain.com closing connection
Connection closed by foreign host.[/COLOR][COLOR=#000080]
[/COLOR]root@mailserver3:~#

I don't see any errors in the logs of mailserver2.

Thanks

---

### Post by SeijiSensei on 2013-05-01
Maybe the problem is between mailserver2 and the MX host for otherdomain.com?  If you run the same test on mailserver2 and connect to the MX host for otherdomain.com, does that work?

---

### Post by darkod on 2013-05-01
I don't know this and and the logs in details like Sensei, so maybe that's why I'm still confused.

Are you using mailserver2 directly, or not? According to the test you did, mailserver2 does accept sending emails from that user.
But, if you are actually trying to use mailserver3 as your mailserver, which then connects to mailserver2, a disabled relay might be the problem. I think all relaying is disabled by default to block spammers from using your server to send spam. And if enabling relaying make sure you know what you are doing and how to do it. If you enable it for all, your server will soon be sending few thousand spam emails in its queue.

---

### Post by SeijiSensei on 2013-05-02
Sendmail relays are pretty much a cinch to configure.  You just have to make sure the relay's daemon listens on the external port then add the relay's hostname to the "DS" directive in sendmail.cf on the client.  You can also use a "[mailertable]("http://www.sendmail.com/sm/open_source/docs/m4/mailertables.html")" for more complex relaying needs, like selecting the relay destination based on the message's delivery domain.

Controlling access to the relay is usually done in the "[access]("http://www.sendmail.com/sm/open_source/docs/m4/anti_spam.html")" database.  You specify the domains for which you will accept mail; any other destinations are rejected by default.

---

