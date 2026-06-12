---
title: "[SOLVED] Imap and dovecot"
date: 2008-08-21
forum: Server Platforms
---

### Post by gishaust on 2008-08-21
I have been trying to get and email server going everything is going fine except one thing in dovecot.

I can sent mail to the new postfix server but when I Imap through telnet I have a problem logging in I get the below issue.

```


telnet localhost pop3
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Dovecot ready.
user sal@prt.com
+OK
pass 1234
-ERR Temporary authentication failure.

```

I know the password is correct because I used postfix.admin to set it up.
and my dovecot-delivery.log says this so I had at sometime use Imap to deliver it
```

deliver(sal@prt.com): 2008-08-21 12:07:38 Info: msgid=<20080821020700.46B8A32C239@mta>: saved mail to INBOX

```

I think this is the issue it taken from the mail log
```

sql(sal@prt.com,127.0.0.1): Password query failed: Table 'postfix.view_users' doesn't exist

```

In mysql database it looks like this
```

CREATE TABLE mailbox (
  username varchar(255) NOT NULL default '',
  password varchar(255) NOT NULL default '',
  name varchar(255) NOT NULL default '',
  maildir varchar(255) NOT NULL default '',
  quota int(10) NOT NULL default '0',
  domain varchar(255) NOT NULL default '',
  created datetime NOT NULL default '0000-00-00 00:00:00',
  modified datetime NOT NULL default '0000-00-00 00:00:00',
  active tinyint(1) NOT NULL default '1',
  PRIMARY KEY  (username),
  KEY username (username)
) COMMENT='Postfix Admin - Virtual Mailboxes';

```

In the /etc/dovecot/dovecot-sql.conf it says this
```

driver = mysql
connect = host=127.0.0.1 dbname=mailserver user=mailuser password=mailuser2007
default_pass_scheme = PLAIN-MD5
password_query = SELECT email as user, password FROM view_users WHERE email='%u';

```

should this line be like this
```

password_query = SELECT mailbox as user, password FROM password WHERE email='%u';


```

gishaust

---

### Post by gishaust on 2008-08-24
bump

---

### Post by gishaust on 2008-08-24
After not getting a response to this issues I went to the dovecot mailing list they were very helpful. Below is the response that they gave me.



On Mon, 25 Aug 2008, gishaust wrote:

> hi everyone I am new to dovecot  and I am having  a little trouble
>
> I am getting this error  in my mail.log I have google it and can't find a response,
>
> Aug 25 08:14:24 mta dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (postfix)
> Aug 25 08:14:24 mta dovecot: auth-worker(default): sql(sal@prt.com,127.0.0.1): Password query failed: Table 'postfix.password' doesn't exist

There's your hint.. :-)

Sounds like your sql statement for passwd lookup simply needs some
adjustment.

for example, my table in MySQL looks like this:
+------------------------+------------------------------------+--------------
| username               | password                           | name
| maildir                 | quota | domain        | created
| modified            | active |
+------------------------+------------------------------------+---------------

I use the statement: password_query = SELECT password FROM mailbox WHERE username = '%u'

to ensure the lookup is correct.

If you can do the following, I can write you the correct sql statement:

mysql -u root -p
use postfix;
show tables;  <---  output of this required.
select * from mailbox <-- ditto for this

> connect = host=127.0.0.1 dbname=postfix user=postfix password=*******
> default_pass_scheme = PLAIN-MD5
> password_query = SELECT mailbox as user, password FROM password WHERE email='%u';

This is the section more than probably at fault - paste the above into a pastebin
(pastebin.ca is good) and let us know the outputs.

Cheers, 


then I came up with a the following error,

On Mon, 25 Aug 2008, gishaust wrote:
> dovecot-mysql.conf  and then restarted dovecot. then telnet and came up with the same issue

Right - we're getting there then..! :)

> the log says the following
>
> Aug 25 10:09:12 mta dovecot: Dovecot v1.0.10 starting up
> Aug 25 10:09:13 mta dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (postfix)
> Aug 25 10:11:33 mta dovecot: auth-worker(default): plain_md5_verify(sal@prt.com): Invalid password encoding

Easily fixed.  (You are using MD5 for your passphrases, right?)

in dovecot-sql.conf
default_pass_scheme = MD5

/etc/init.d/dovecot restart

That should work. 


and yes it did thanks dovecot mailing list and Christopher J. Buckley

---

