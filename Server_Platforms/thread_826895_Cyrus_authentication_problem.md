---
title: "Cyrus authentication problem"
date: 2008-06-12
forum: Server Platforms
---

### Post by satimis on 2008-06-12
Hi folks,


Ubuntu 6.06 LAMP server amd64


Having tried 2 days on authentication problem without result.  The sever can send and receive mails. Apache and SquirrelMai are running. 


Discovery are as follows


$ testsaslauthd -f /var/spool/postfix/var/run/saslauthd/mux -u cyrus -p xyz```

0: OK "Success."

```


$ cyradm -u cyrus localhost```

IMAP Password: xyz
              Login failed: generic failure at
/usr/lib/perl5/Cyrus/IMAP/Admin.pm line 118
cyradm: cannot authenticate to server as cyrus

```


line 118```

    my $rc = $self->{cyrus}->authenticate(@_);

```


$ telnet localhost imap```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE
THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION
STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision,
Inc.  See COPYING for distribution information.
imap login cyrus xyz
imap NO Login failed.
Connection closed by foreign host.

```


Tried another user


$ telnet localhost imap```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE
THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION
STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision,
Inc.  See COPYING for distribution information.
imap login satimiscyrus abc
imap NO Login failed.
Connection closed by foreign host.
```


$ cat /etc/default/saslauthd```

START=yes
PARAMS="-m /var/spool/postfix/var/run/saslauthd -r"
MECHANISMS="pam"

```


$ sudo find / -name imap.conf
No printout


$ cat /etc/pam.d/imap ```

@include common-auth
@include common-account

```


$ cat /etc/pam.d/common-auth ```

auth    required        pam_unix.so nullok_secure

```


$ cat /usr/share/pam/common-auth```

auth    required        pam_unix.so nullok_secure

```


$ cat /etc/pam.d/common-account ```

account required        pam_unix.so

```


$ cat /usr/share/pam/common-account ```

account required        pam_unix.so
```


$ ls -l /usr/lib/sasl2/```

total 500
-rw-r--r-- 1 root root 19036 2006-04-24 19:38 libanonymous.a
-rw-r--r-- 1 root root   855 2006-04-24 19:38 libanonymous.la
lrwxrwxrwx 1 root root    22 2008-04-18 07:24 libanonymous.so ->
libanonymous.so.2.0.19
lrwxrwxrwx 1 root root    22 2008-04-18 07:24 libanonymous.so.2 ->
libanonymous.so.2.0.19
-rw-r--r-- 1 root root 15712 2006-04-24 19:38 libanonymous.so.2.0.19
-rw-r--r-- 1 root root 21802 2006-04-24 19:38 libcrammd5.a
-rw-r--r-- 1 root root   841 2006-04-24 19:38 libcrammd5.la
lrwxrwxrwx 1 root root    20 2008-04-18 07:24 libcrammd5.so ->
libcrammd5.so.2.0.19
lrwxrwxrwx 1 root root    20 2008-04-18 07:24 libcrammd5.so.2 ->
libcrammd5.so.2.0.19
-rw-r--r-- 1 root root 19104 2006-04-24 19:38 libcrammd5.so.2.0.19
-rw-r--r-- 1 root root 59792 2006-04-24 19:38 libdigestmd5.a
-rw-r--r-- 1 root root   864 2006-04-24 19:38 libdigestmd5.la
lrwxrwxrwx 1 root root    22 2008-04-18 07:24 libdigestmd5.so ->
libdigestmd5.so.2.0.19
lrwxrwxrwx 1 root root    22 2008-04-18 07:24 libdigestmd5.so.2 ->
libdigestmd5.so.2.0.19
-rw-r--r-- 1 root root 46336 2006-04-24 19:38 libdigestmd5.so.2.0.19
-rw-r--r-- 1 root root 19262 2006-04-24 19:38 liblogin.a
-rw-r--r-- 1 root root   835 2006-04-24 19:38 liblogin.la
lrwxrwxrwx 1 root root    18 2008-04-18 07:24 liblogin.so ->
liblogin.so.2.0.19
lrwxrwxrwx 1 root root    18 2008-04-18 07:24 liblogin.so.2 ->
liblogin.so.2.0.19
-rw-r--r-- 1 root root 16352 2006-04-24 19:38 liblogin.so.2.0.19
-rw-r--r-- 1 root root 38724 2006-04-24 19:38 libntlm.a
-rw-r--r-- 1 root root   829 2006-04-24 19:38 libntlm.la
lrwxrwxrwx 1 root root    17 2008-04-18 07:24 libntlm.so ->
libntlm.so.2.0.19
lrwxrwxrwx 1 root root    17 2008-04-18 07:24 libntlm.so.2 ->
libntlm.so.2.0.19
-rw-r--r-- 1 root root 32264 2006-04-24 19:38 libntlm.so.2.0.19
-rw-r--r-- 1 root root 27142 2006-04-24 19:38 libotp.a
-rw-r--r-- 1 root root   829 2006-04-24 19:38 libotp.la
lrwxrwxrwx 1 root root    16 2008-04-18 07:24 libotp.so ->
libotp.so.2.0.19
lrwxrwxrwx 1 root root    16 2008-04-18 07:24 libotp.so.2 ->
libotp.so.2.0.19
-rw-r--r-- 1 root root 48856 2006-04-24 19:38 libotp.so.2.0.19
-rw-r--r-- 1 root root 19342 2006-04-24 19:38 libplain.a
-rw-r--r-- 1 root root   835 2006-04-24 19:38 libplain.la
lrwxrwxrwx 1 root root    18 2008-04-18 07:24 libplain.so ->
libplain.so.2.0.19
lrwxrwxrwx 1 root root    18 2008-04-18 07:24 libplain.so.2 ->
libplain.so.2.0.19
-rw-r--r-- 1 root root 16384 2006-04-24 19:38 libplain.so.2.0.19
-rw-r--r-- 1 root root 29164 2006-04-24 19:38 libsasldb.a
-rw-r--r-- 1 root root   856 2006-04-24 19:38 libsasldb.la
lrwxrwxrwx 1 root root    19 2008-04-18 07:24 libsasldb.so ->
libsasldb.so.2.0.19
lrwxrwxrwx 1 root root    19 2008-04-18 07:24 libsasldb.so.2 ->
libsasldb.so.2.0.19
-rw-r--r-- 1 root root 21288 2006-04-24 19:38 libsasldb.so.2.0.19
```


Please help.  TIA


B.R.
satimis

---

### Post by q.dinar on 2008-07-25
hello.
i installed cyrus on ubuntu 7.10.
nothing ese i installed: no postfix, on smtp.
but exim i think installed when cyrus was being installed.

now i write:
cyradm
server domain.dom
it asks for password.
what i should write? cyrus's password? i write but it sais "failed".

---

### Post by q.dinar on 2008-07-25
and i have uncommented "admins: cyrus" line in imapd.conf

---

