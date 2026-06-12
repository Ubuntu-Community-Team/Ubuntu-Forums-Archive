---
title: "Dovecot Replication Issue"
date: 2015-04-10
forum: Server Platforms
---

### Post by terencewklau on 2015-04-10
Hi All,

I've got 2 Postfix/Dovecot servers running on Ubuntu Server 14.04.  Dovecot version is 2.2.9 while Postfix is 2.11.

I've set up replication with the following config on SERVER1:
```

mail_plugins = $mail_plugins notify replication
service replicator {
  process_min_avail = 1
}
service replicator {
  unix_listener replicator-doveadm {
    mode = 0600
  }
}
replication_max_conns = 10
service aggregator {
  fifo_listener replication-notify-fifo {
    user = vmail
    mode = 0600
  }
  unix_listener replication-notify {
    user = vmail
    mode = 0600
  }
}
service doveadm {
  user = vmail
}
service config {
  unix_listener config {
    user = vmail
  }
}
dsync_remote_cmd = ssh -l%{login} %{host} doveadm dsync-server -u%u
plugin {
  mail_replica = remote:vmail@SERVER2.domain.com
}
```

After restarting the dovecot service, the single mailbox that was created earlier was synced to SERVER2.  But changes after that are not synced.  Restarting the dovecot service also doesn't sync the changes over.

But if I sync it manually, it works:

doveadm sync -u [email]test@domain.com[/email] remote:SERVER2.domain.com

From what I understand, dovecot will be notified of any changes and then sync them over immediately.  At least when the service is started, it should also sync any changes immediately.  But that's not happening.  I've enabled debug logs but there's nothing in there that can point me in the right direction.

Any advice would be most appreciated.

Thanks.

---

### Post by sandyd on 2015-04-10
Whats the output of
```

doveadm replicator status
```

---

### Post by terencewklau on 2015-04-10
```
root# doveadm replicator status
Queued 'sync' requests        0
Queued 'high' requests        0
Queued 'low' requests         0
Queued 'failed' requests      0
Queued 'full resync' requests 0
Waiting 'failed' requests     0
Total number of known users   1

root# doveadm replicator status [email]test@domain.com[/email]
username                                               priority fast sync full sync failed
[email]test@domain.com[/email]                                   none     00:23:12  03:18:43  -
```

---

