---
title: "SFTP server installation with chroot jail"
date: 2014-06-19
forum: Server Platforms
---

### Post by shaileshjain-1975 on 2014-06-19
[COLOR=#000000]Hi All,[/COLOR]

[COLOR=#000000]Please can some help me for SFTP server installation with chroot jail with the sftp log.

[/COLOR]
[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]shailu[/COLOR]

---

### Post by shaileshjain-1975 on 2014-06-23
Hi All,

pls help me for the SFTP server with the logs.

Thanks,
Shailu

---

### Post by Lars Noodén on 2014-06-23
First set up chrooted SFTP.  What version of Ubuntu are you using?

```

Subsystem sftp internal-sftp

Match Group sftp-only
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u

```

---

### Post by Lars Noodén on 2014-06-23
Once you have that working, you can prepare a /dev/log socket in the chroot directory.  Because you are in a chroot, sftp cannot use the main one at /dev/log but instead must have one created inside the chroot itself.  If, like above, the chroot is /home then it would be like this:

```

sudo mkdir /home/dev

```

And add this line to /etc/rsyslog.conf

```

$AddUnixListenSocket /home/dev/log

```

(However, that [AddUnixListenSocket](http://www.rsyslog.com/doc/master/configuration/modules/imuxsock.html) is deprecated and my example badly out of date.  I do not know the new method.)

And reload the rsyslog configuration

```

sudo service rsyslog restart

```

Then [change the log level for the SFTP server](http://manpages.ubuntu.com/manpages/trusty/en/man8/sftp-server.8.html).

```

Subsystem sftp internal-sftp

Match Group sftp-only
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u **-l INFO** 

```

LogLevel INFO and VERBOSE ought to give you session logging info.  Just be aware that there can be legal consequences for collecting such logs and that you might have to check locally for any requirements or gotchas.

---

