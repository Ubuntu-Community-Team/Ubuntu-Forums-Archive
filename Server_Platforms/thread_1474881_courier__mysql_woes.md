---
title: "courier / mysql woes"
date: 2010-05-06
forum: Server Platforms
---

### Post by bluethundr on 2010-05-06
Hello!

I have been attempting to get an IMAP enabled mail server working for the past couple of weeks... the good news is that I have a MAJOR success to report!

I was using an old flavor of Ubuntu to get this going in the hopes that I could more easily install a Zimbra interface as Zimbra is lagging behind the times in Debian compatible releases vs Red Hat based releases. There are a lot of messy things you have to do on a modern Debian based OS to get Zimbra to work that I just would prefer not to deal with.

Long story short, I launched a Hardy 8.04 image and got what I needed. The missing link in my Dapper 6.06 attempt was libauthmysql.so which is installed by the package courier-authlib-mysql.

Dapper just doesn't have this package for some reason.

Anywho...

I installed said library, did a quick rebuild of the system and THIS was the happy result!!!

```


May  6 07:45:28 cloud3 authdaemond: received auth request, service=imap, authtype=login
May  6 07:45:28 cloud3 authdaemond: authmysql: trying this module
May  6 07:45:28 cloud3 authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "walbs {at } nedom {dot } com" AND (enabled=1)
May  6 07:45:28 cloud3 authdaemond: password matches successfully
May  6 07:45:28 cloud3 authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=walbs {at } nedom {dot } com, fullname=Walkiria, maildir=/var/spool/mail/virtual/walbs/, quota=<null>, options=<null>
May  6 07:45:28 cloud3 authdaemond: authmysql: clearpasswd=<null>, passwd=EncryptedPass
May  6 07:45:28 cloud3 authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=walbs {at } nedom {dot } com, fullname=Walkiria, maildir=/var/spool/mail/virtual/walbs/, quota=<null>, options=<null>
May  6 07:45:28 cloud3 authdaemond: Authenticated: clearpasswd=herPass, passwd=EncryptedPass
May  6 07:45:28 cloud3 imapd: LOGIN, user=walbs {at } nedom {dot } com, ip=[::ffff:10.249.74.116], port=[57091], protocol=IMAP
May  6 07:57:22 cloud3 imapd: DISCONNECTED, user=walbs {at } nedom {dot } com, ip=[::ffff:10.249.74.116], headers=0, body=0, rcvd=65, sent=277, time=714

```As you can see, I used somebody else's account that I had created (in this case my fiancee's) and everything just WORKED!!!

However, more oddness seems to be ensuing that I do need to get ironed out. I hope you can help me here!

I noticed that when I tried to login with MY username and password I was getting nowhere fast even tho I was entering the right password information.

```


May  6 08:20:47 cloud3 imapd: Connection, ip=[::ffff:10.249.74.116]
May  6 08:21:17 cloud3 authdaemond: received auth request, service=imap, authtype=login
May  6 08:21:17 cloud3 authdaemond: authmysql: trying this module
May  6 08:21:17 cloud3 authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "bluethundr {at } nedom {dot } com" AND (enabled=1)
May  6 08:21:17 cloud3 authdaemond: supplied password 'myUserPass' does not match encrypted password 'sdtrusfX0Jj66'
May  6 08:21:17 cloud3 authdaemond: authmysql: REJECT - try next module


```I noticed in the logs that the 'crypt' password was NOT changed from the default entry 'sdtrusfX0Jj66'. In my fiancee's account on the other hand, her 'crypt' password was sufficiently randomized when you looked at the contents of the user table.

I then did the following things:

I deleted my user account record from the database and recreated it making sure to NOT encrypt the password in the table. That had no result, the password was still defaulting to 'sdtrusfX0Jj66'.

I then dropped the whole table and re-created it (I do have a backup of the older maildb)

Same result. And THIS time when I re-added my fiancee's account HER account was behaving in the same exact way!

Here is the user table:

```


    CREATE TABLE `users` (
`id` varchar(128) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;


```In order to add my user account(s) I populate the users table with the following information:
```


INSERT INTO users (id,name,maildir,clear) VALUES
    ('bluethundr {at } nedom {dot } com','Tim','bluethundr/',encrypt('myUserPass'));


And I am not sure if this is worth mentioning, but I also populate the 'aliases' table with the following info...

``````


INSERT INTO aliases (mail,destination) VALUES
    ('bluethundr {at } newdom {dot } com','bluethundr {at } nedom {dot } com')

```So in short I have some encouraging progress to report and things are indeed looking up!!! ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Apollo: "I will not serve under a man who questions my integrity."

Adama: "And I won't have an officer under my command who doesn't have any."


This is my public RSA key: 5A4873A9
Key fingerprint = 0C0F 1769 83C3 8318 7424 73B1 55C5 4B3E 5A48 73A9
GPG me!!!

---

