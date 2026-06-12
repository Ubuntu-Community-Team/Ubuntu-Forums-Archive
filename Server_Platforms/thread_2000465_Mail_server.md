---
title: "Mail server"
date: 2012-06-09
forum: Server Platforms
---

### Post by freakinjonathan on 2012-06-09
I'm setting up a mail server following the directions at: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)


Currently I can send messages through squirrelmail, but I cannot recieve messages. If I message myself I receive this error:


```

This is the mail system at host server.example.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<jonathan@xxx.com>: unknown user: "jonathan"

Final-Recipient: rfc822; jonathan@xxx.com
Original-Recipient: rfc822;jonathan@xxx.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "jonathan"

```

I checked mysql and there is a record for my 'jonathan@xxx.com' :( 

Here is my mysql output for the user. 
```

+----------------------+----------+------+------+-------------------------+-----------+---------+-----------------+----------+---------------+-------+------------+----------------+
| id                   | name     | uid  | gid  | home                    | maildir   | enabled | change_password | clear    | crypt         | quota | procmailrc | spamassassinrc |
+----------------------+----------+------+------+-------------------------+-----------+---------+-----------------+----------+---------------+-------+------------+----------------+
| jonathan@xxx.com     | jonathan | 5000 | 5000 | /var/spool/mail/virtual | jonathan/ |       1 |               1 | ChangeMe | sdfjjasdlf340. |       |            |                |
+----------------------+----------+------+------+-------------------------+-----------+---------+-----------------+----------+---------------+-------+------------+----------------+
```


Contents of /etc/postfix/mysql_mailbox.cf:

```

user=mail
password=mysql-password
dbname=maildb
table=users
select_field=maildir
where_field=id
hosts=127.0.0.1
additional_conditions = and enabled = 1

```


Update, I wanted to upload this telnet log.
```

$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 xxx.com ESMTP Postfix
ehlo xxx.com
250-xxx.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: test@xxx.com
250 2.1.0 Ok
rcpt to: jonathan@xxx.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
sadf
sd
f
sdf
sdf
.
250 2.0.0 Ok: queued as A1676204E7
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

---

### Post by freakinjonathan on 2012-06-12
I have figured out the issue. 

I believe this was the fix in case anybody else wants to know


Go to /etc/postfix/main.cf

Then find mydestination and take out your domainame from that line. Let it only route to localhost. 
Then reboot. (I guess you could just reload postfix but whatever)

---

