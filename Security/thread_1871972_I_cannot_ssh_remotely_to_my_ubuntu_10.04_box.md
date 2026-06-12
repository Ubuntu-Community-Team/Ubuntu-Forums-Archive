---
title: "I cannot ssh remotely to my ubuntu 10.04 box"
date: 2011-10-29
forum: Security
---

### Post by untitledtv on 2011-10-29
I created a user and it works if I am on the box and do the following:

```
    ssh -p 3020 airy@localhost
```

However, when I do test from the same box to check if I can access remotely (it doesn't), by typing the following:

```
ssh -vvv -p 3020 airy@domain.com
```

My logs show that the password is accepted, but then the user is rejected.

On the client side, I see the following:

```
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to domain.suroot.com [62.232.121.23] port 3020.
debug1: connect to address 29.232.121.23 port 3020: Connection timed out
```

On the server side, this is the output in the logs:

```
Oct 29 15:17:01 timothy-laptop CRON[3593]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 29 15:17:01 timothy-laptop CRON[3593]: pam_unix(cron:session): session closed for user root
```

---

### Post by Toz on 2011-10-29
> debug1: connect to address 29.232.121.23 port 3020: Connection timed out
Do you have a firewall enabled on the server? Is port 3020 being allowed in?

---

### Post by papibe on 2011-10-29
From where are you trying to access your server? Is it from the same LAN?

Regards.

---

