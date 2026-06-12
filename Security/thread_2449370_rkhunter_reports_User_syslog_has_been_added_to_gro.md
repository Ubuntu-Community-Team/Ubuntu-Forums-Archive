---
title: "rkhunter reports User syslog has been added to group tty: Problem?"
date: 2020-08-25
forum: Security
---

### Post by KneadToKnow on 2020-08-25
Full message:
> Warning: Changes found in the group file for group 'tty':
         User 'syslog' has been added to the group
Confirmed via authlog:
> Aug 23 11:44:54 Book gpasswd[3521337]: user syslog added by root to group tty
I did not do this manually, nor did I install any software at around that time.

I'm running rkhunter 1.4.6 on Ubuntu 20.04 with all updates.

---

### Post by &amp;KyT$0P# on 2020-08-25
Did this coincide with an update to rsyslog package?  Specifically, was rsyslog updated to version 8.2001.0-1ubuntu1.1 ?  If so see [this]("https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/1890177").

---

### Post by KneadToKnow on 2020-08-25
Yes, according to /var/log/apt/history.log:
> Start-Date: 2020-08-23  11:44:04
Commandline: aptdaemon role='role-commit-packages' sender=':1.234'
Upgrade: <other stuff> rsyslog:amd64 (8.2001.0-1ubuntu1, 8.2001.0-1ubuntu1.1) <other stuff>
End-Date: 2020-08-23  11:46:03

Do I understand correctly then, that this was a valid change as part of fix to a bug that had been reported?

---

### Post by EuclideanCoffee on 2020-08-26
It is the expected behavior. Here's the source of the change.

```

[COLOR=#333333][FONT=monospace]# debian/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]rsyslog.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]postinst[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]case "$1" in[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]    configure)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        adduser --system --group --no-create-home --quiet syslog || true[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]        adduser syslog adm || true[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]       +adduser syslog tty || true[/FONT][/COLOR]

```

It does the following, which would trigger a change in your rkhunter.

```

[COLOR=#333333][FONT=monospace]Preparing to unpack .../rsyslog_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]8.2001.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0-1ubuntu1+[/FONT][/COLOR][COLOR=#333333][FONT=monospace]test2020307b1_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Unpacking rsyslog (8.2001.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0-1ubuntu1+[/FONT][/COLOR][COLOR=#333333][FONT=monospace]test2020307b1) over (8.2001.0-1ubuntu1) ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Setting up rsyslog (8.2001.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0-1ubuntu1+[/FONT][/COLOR][COLOR=#333333][FONT=monospace]test2020307b1) ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The user `syslog' is already a member of `adm'.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Adding user `syslog' to group `tty' ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]==> Adding user syslog to group tty <==[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Done.

```

[/FONT][/COLOR]Root is the user during a package install. It will follow whatever instructions, and in this example, it adds syslog to tty, which is the trigger you saw. Expected behavior with the patch.

---

### Post by KneadToKnow on 2020-08-26
Excellent news, and I learned some things, too!

---

