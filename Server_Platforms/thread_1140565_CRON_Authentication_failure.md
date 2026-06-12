---
title: "CRON: Authentication failure"
date: 2009-04-27
forum: Server Platforms
---

### Post by tr333 on 2009-04-27
I am getting cron authentication errors appearing in the syslog:
```
Apr 28 07:20:01 wiki CRON[13514]: Authentication failure
Apr 28 07:30:01 wiki CRON[13546]: Authentication failure
Apr 28 07:39:01 wiki CRON[13575]: Authentication failure
Apr 28 07:40:01 wiki CRON[13579]: Authentication failure
Apr 28 07:50:01 wiki CRON[13611]: Authentication failure
Apr 28 08:00:01 wiki CRON[13643]: Authentication failure
Apr 28 08:09:01 wiki CRON[13672]: Authentication failure
Apr 28 08:10:01 wiki CRON[13676]: Authentication failure
Apr 28 08:17:01 wiki CRON[13699]: Authentication failure
Apr 28 08:20:01 wiki CRON[13709]: Authentication failure
Apr 28 08:30:01 wiki CRON[13741]: Authentication failure
Apr 28 08:39:01 wiki CRON[13770]: Authentication failure
Apr 28 08:40:01 wiki CRON[13774]: Authentication failure
Apr 28 08:50:01 wiki CRON[13806]: Authentication failure
Apr 28 09:00:01 wiki CRON[13838]: Authentication failure
Apr 28 09:09:01 wiki CRON[13867]: Authentication failure
```
Can anyone explain why these errors are occuring?

I checked /var/log/auth.log and noticed the following cron errors:
```
Apr 28 09:00:01 wiki CRON[13838]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Apr 28 09:00:01 wiki CRON[13838]: pam_lwidentity(cron:account): failed to get GP info
Apr 28 09:00:01 wiki CRON[13838]: pam_lwidentity(cron:account): request failed
Apr 28 09:00:01 wiki CRON[13838]: pam_lwidentity(cron:account): User 'root' is not known.
Apr 28 09:00:01 wiki CRON[13838]: pam_lwidentity(cron:account): Returning 7 for user "root"
Apr 28 09:00:01 wiki CRON[13838]: pam_unix(cron:account): account root has expired (account expired)
Apr 28 09:09:01 wiki CRON[13867]: pam_lwidentity(cron:account): PAM config: global:krb5_ccache_type 'FILE'
Apr 28 09:09:01 wiki CRON[13867]: pam_lwidentity(cron:account): failed to get GP info
Apr 28 09:09:01 wiki CRON[13867]: pam_lwidentity(cron:account): request failed
Apr 28 09:09:01 wiki CRON[13867]: pam_lwidentity(cron:account): User 'root' is not known.
Apr 28 09:09:01 wiki CRON[13867]: pam_lwidentity(cron:account): Returning 7 for user "root"
Apr 28 09:09:01 wiki CRON[13867]: pam_unix(cron:account): account root has expired (account expired)
```
Is it related to having likewise-open installed?

---

### Post by julrich on 2009-05-07
Have you found out anything about this?  I'm having the same problem -- system and auth logs are full of the same types of messages.  The cause is pretty obvious, I'm just not sure how to fix it.

---

### Post by doogy2004 on 2009-05-07
I've had this problem before.

Use the following to unlock the account:
```
sudo passwd -u ACCOUNT_NAME
```
Then re-lock the account with:
```
sudo usermod -l ACCOUNT_NAME
```

---

### Post by tr333 on 2009-05-08
It appears to be from [Bug #238755](https://bugs.edge.launchpad.net/bugs/238755).  The following steps fixed it for me:
```
# edit /etc/shadow using vipw
$ sudo vipw -s
```
change the line for 'root' user, removing the last field ('1' character).
```

root:!:13919:0:99999:7::**1**:

to
root:!:13919:0:99999:7::

```

---

### Post by cpt_power on 2009-05-26
Getting the same error here.  unlocking and re-locking the root account doesn't fix it, and the /etc/shadow file doesn't have a 1 at the end of the root line.

it is a result of having likewise-open installed (I removed it, and those messages immediately stopped), though I have no idea on the fix for it.

---

### Post by doogy2004 on 2009-05-26
> **cpt_power said:**
> it is a result of having likewise-open installed (I removed it, and those messages immediately stopped), though I have no idea on the fix for it.

you probably need to map the root account to the AD Administrator account.

---

