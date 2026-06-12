---
title: "Problem configuring exim to maildir"
date: 2009-05-28
forum: Server Platforms
---

### Post by ianhaycox on 2009-05-28
Hi,

I trying to re-configure exim to deliver local mail in Maildir format rather than mbox but after re-configuring it still delivers in /var/mail

I ran

```

$ dpkg-reconfigure exim4-config

```

Chose local delivery and maildir_home. The config went OK and the MTA restarted. Running the following,

```

$ echo "body" | mail -s "test" $USER

```

showed the message appended in /var/mail/$USER not in ~/Maildir ! I created ~/Maildir via mb2md but still messages go to spool not ~/Maildir.

The file /etc/exim4/update-exim4.conf.conf has the line

```

dc_localdelivery='maildir_home'

```


Any ideas anyone ?

---

