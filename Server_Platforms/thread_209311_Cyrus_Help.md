---
title: "Cyrus Help"
date: 2006-07-04
forum: Server Platforms
---

### Post by Khaine on 2006-07-04
I'm running dapper and I'm trying to setup postfix / cyrus.  So far I've followed these guides:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

I'm am trying to get cyrus and postfix to communicate using lmtp

but when I go to login to cyradm it won't authenticate

```
$ cyradm --user cyrus localhost
Password:
cyradm: cannot authenticate to server as user cyrus

```

I'm not entirely sure what the problem is, I think it lies with my configuration of saslauthd.

my /etc/default/saslauthd looks like this

```

# This needs to be uncommented before saslauthd will be run automatically
 START=yes

PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

MECHANISMS="pam"

```

any help would be greatly appreciated

---

### Post by Khaine on 2006-07-05
Ok so I found out that you need to set the password for the cyrus user like so:

```
sudo saslpasswd2 cyrus
```

and now I can access cyradm (yay!)

I created a user using the following:

```
localhost>cm user.firstname.lastname
```

and gave the user a password:

```
sudo saslpasswd2 firstname.lastname
```

but now when I try to login I get:

imap NO Login failed: generic failure

In /var/log/mail.info:

```
cyrus/imapd[17946]: badlogin: localhost[127.0.0.1] plain
text login SASL(-1): generic failure: checkpass failed
```

and I don't know what to do,

TIA

---

### Post by Tux007 on 2006-07-26
Has anyone solved this problem????
I have the same trouble!

---

### Post by mentecat on 2006-11-14
From the log I can see that you are trying to do a plain text login, saslpasswd2 should be for example for cram-md5 login.

For a plain text login you could try to  use saslauthd, configuring it to use pam.

bye

---

