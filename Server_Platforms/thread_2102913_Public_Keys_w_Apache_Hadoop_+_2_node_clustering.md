---
title: "Public Keys w/ Apache Hadoop + 2 node clustering"
date: 2013-01-08
forum: Server Platforms
---

### Post by Crafty Kisses on 2013-01-08
I'm having a Public Key issue, as stated 2 node clustering w/ Apache Hadoop running

```
cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys
copy authorized_keys over to PROWL:/home/hduser/.ssh/
ssh localhost - ok
```

Then

```
[hduser@prowl3 ~]$ ssh 'hduser@montanaprowl'
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
[hduser@prowl ~]$
```

```
/etc/ssh/sshd_config
PasswordAuthentication no
```

I've chmodded the proper directories for permission using

```
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

To no avail, still having Pubic Key issues, any ideas? 

Thanks, Montana!

---

