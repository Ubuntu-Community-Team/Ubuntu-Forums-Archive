---
title: "Setting up pure-ftpd but getting an error after using the &quot;pure-pw useradd&quot; command"
date: 2023-06-06
forum: Server Platforms
---

### Post by husker12 on 2023-06-06
This is the script I'm following though I'm entering in the commands individually, one by one:

```
groupadd ftpgroup
useradd -g ftpgroup -d /dev/null -s /usr/sbin/nologin ftpuser
pure-pw useradd husker -u ftpuser -d /ftphome
pure-pw mkdb
cd /etc/pure-ftpd/auth/ - didn't need
ln -s ../conf/PureDB 60pdb - didn't need, link was already there
mkdir -p /ftphome
chown -R ftpuser:ftpgroup /ftphome/
systemctl restart pure-ftpd
```

This is the problematic command:

```
pure-pw useradd husker -u ftpuser -d /ftphome
```

It causes the following error to appear:

```
Password: 
Enter it again: 
Error.
Check that [husker] doesn't already exist,
and that [/etc/pure-ftpd/pureftpd.passwd.tmp] can be written.

```

I know for sure that neither the username husker nor the file pureftpd.passwd.tmp exist.

How do I resolve this issue?

---

### Post by TheFu on 2023-06-07
IMHO, nobody should be using plain FTP since around 2002.  Use sftp, which comes for free when we install the **ssh** package.  Every Linux file manager supports sftp:// URLs.

[https://security.stackexchange.com/questions/145008/what-are-the-risks-of-using-ftp](https://security.stackexchange.com/questions/145008/what-are-the-risks-of-using-ftp)

There's little need to setup any FTP server and hasn't been for decades now.  sftp would use the same authentication as ssh, hopefully ssh-key-based.

I really wish beginning Linux admin classes would stop pushing plain FTP.

---

