---
title: "IMAP configuration: Directory/file does not exist"
date: 2013-06-14
forum: Server Platforms
---

### Post by BlueMooneke on 2013-06-14
Hello everybody,

as I am trying to setup a mail server following [this guide]("http://flurdy.com/docs/postfix/"), I stumbled upon a problem:
Whenever I try to login through IMAP, I get this error:  
```
BYE [ALERT] Fatal error: No such file or directory: No such file or directory.
Connection closed by foreign host.
```

As I try to figure out what is wrong here, I guess somehow IMAP can not find the maildir I have specified, is that correct?

So I tried searching for the error. This are some config files:

/etc/courier/authmysqlrc:
```
MYSQL_HOME_FIELD home
MYSQL_MAILDIR_FIELD concat(home,'/',maildir)
```

Into mysql, there are those 2 called fields for each user:
example:
```
home: /var/spool/mail/virtual
maildir: test/
```

Those directories do exist:
```
ll /var/spool/mail/virtual/
drwx--S--- virtual virtual 4096 Jun 14 test/
```

But still the problem arises... Could anybody point me in the right direction?

Thanks in advance!
BlueMooneke

EDIT:
Found out what the problem was.
I just deleted all folders into /var/spool/mail/virtual/
And tried to resend a message to one of the users which created the folder again
Now I the error disappeared!

---

### Post by e_tyash on 2013-11-12
I am having the same challenge. Your fix did not assist. what else can I look at?

Permissions on /var/mail/virtual look like this
root@mailserver:/var/mail# ls -lr
total 44
drwxr-sr-x 2 virtual virtual  4096 Nov 12 12:09 **virtual**

if this may help --- this is how my error when iTail mail.log

Nov 12 04:05:37 mailserver imapd: Connection, ip=[::ffff:127.0.0.1]
Nov 12 04:05:55 mailserver authdaemond: received auth request, service=imap, authtype=login
Nov 12 04:05:55 mailserver authdaemond: authmysql: trying this module
Nov 12 04:05:55 mailserver authdaemond: authmysqllib: connected. Versions: header 50517, client 50529, server 50529
Nov 12 04:05:55 mailserver authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'edward@mydomain'  AND (enabled=1)
Nov 12 04:05:55 mailserver authdaemond: password matches successfully
Nov 12 04:05:55 mailserver authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=edward@mydomain.com, fullname=edward, maildir=/var/spool/mail/virtual/edward/, quota=<null>, options=<null>
Nov 12 04:05:55 mailserver authdaemond: authmysql: clearpasswd=<null>, passwd=$5$8401c764fadc14d9$cque4r0VlRn.Vw4rzzukgeELBeKckKW6ni9umdLvHPA
Nov 12 04:05:55 mailserver authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=edward@mydomain.com, fullname=edward, maildir=/var/spool/mail/virtual/edward/, quota=<null>, options=<null>
Nov 12 04:05:55 mailserver authdaemond: Authenticated: clearpasswd=braintech, passwd=$5$8401c764fadc14d9$cque4r0VlRn.Vw4rzzukgeELBeKckKW6ni9umdLvHPA
Nov 12 04:05:55 mailserver imapd: chdir /var/spool/mail/virtual/edward/: No such file or directory
Nov 12 04:05:55 mailserver imapd: [email]edward@mydomain.com[/email]: No such file or directory

---

