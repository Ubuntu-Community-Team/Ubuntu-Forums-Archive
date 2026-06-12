---
title: "Dovecot serverbug"
date: 2011-09-03
forum: Server Platforms
---

### Post by nariub on 2011-09-03
ubuntu 11.04 64bit
running postfix and dovecot
client is evolution.

every day or so i get a Serverbug error while refreshing evolution client


dovecot says;
2011-09-03 07:23:52 IMAP(xxxxxxx): Error: mkdir(/home/xxxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxxxx) egid=1000(xxxxxxx) missing +w perm: /home/xxxxxxx)

service dovecot restart 
will fix it for a few days.

Other than this, she works fine..

Question is,
What is that?

---

### Post by e79 on 2011-09-03
> **nariub said:**
> dovecot says;
2011-09-03 07:23:52 IMAP(xxxxxxx): Error: mkdir(/home/xxxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxxxx) egid=1000(xxxxxxx) **missing +w perm: /home/xxxxxxx)**

As far as I can tell (bold part), you seems to be missing the Write attribute on the /home/xxxxxxx.

I would tend to do a  :

```
chmod u+w /home/xxxxxxx
```
 
But before, could you paste the result of :

```
ls -alh /home/xxxxxxx
```

---

### Post by nariub on 2011-09-03
did you see the part about restarting dovecot will seems to fix it?

the perms seem fine, i have been looking at them for over a week now.

i even changed the imap executable to :mail from root:root
incase it wasn't changing itself correctly
ls -lha 
drwxr-xr-x 36 xxxxxx xxxxxx   12K 2011-09-01 13:04 Maildir

ls -lha Maildir/
drwx------  2 xxxxxx xxxxxx 4.0K 2011-09-01 13:04 cur

Error: mkdir(/home/xxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxx) egid=1000(xxxxxx) missing +w perm: /home/xxxxxx)


2011-09-03 07:28:52 imap-login: Info: Login: user=<xxxxxx>, method=PLAIN, rip=192.168.1.165, lip=192.168.1.212, TLS

when she works..  she works flawlessly.
then she stops and starts barking about missing perms
perms are not any different
and it seems to be exclusive to this one user, (mine actually)

---

### Post by e79 on 2011-09-04
> **nariub said:**
> i even changed the imap executable to :mail from root:root

So now the imap executable runs under ':mail' group with no specified user instead of root:root ? 

> **nariub said:**
> ls -lha Maildir/
**drwx------**  2 xxxxxx xxxxxx 4.0K 2011-09-01 13:04 curError:  mkdir(/home/marione/Maildir/cur) failed: Permission denied  (euid=1000(marione) egid=1000(marione) missing +w perm: /home/marione)

While I don't know why it works for some time and then stops, I still think this is a permission issue. Your Maildir is writable only by your user, and no one else. Dovecot cannot seem to be able to write in your 'cur' folder', preventing you to read (move and mark it as read) your emails at some point.

[http://wiki.dovecot.org/MailboxFormat/Maildir](http://wiki.dovecot.org/MailboxFormat/Maildir)

> Directory Structure

Dovecot uses Maildir++ directory layout for organizing mailbox directories. This means that all the folders are directly inside ~/Maildir directory:
~/Maildir/new, ~/Maildir/cur and ~/Maildir/tmp directories contain the messages for INBOX. The tmp directory is used during delivery, new messages arrive in new and read shall be moved to cur by the clients. [SIZE=2]
[/SIZE]> **nariub said:**
> and it seems to be exclusive to this one user, (mine actually)

Can you show us the permissions for another user that does not have this issue ?
[SIZE=2]
[/SIZE]

---

### Post by nariub on 2011-09-04
imap is still chrooted and changes into the local user to write to Maildir/  just the group on the exe was changed 
(another suggestion in another thread)

how bout this.
I ssh to my server from my client
Then I open evolution on the client.
And she works fine.

Close Evolution
Close ssh session
Open Evolution
  error again.

```

IMAP command failed: [SERVERBUG] Internal error occurred. Refer to server log for more information. [2011-09-04 07:12:06]

2011-09-04 07:12:06 IMAP(xxxxxx): Error: mkdir(/home/xxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxx) egid=1000(xxxxxx) missing +w perm: /home/xxxxxx)
2011-09-04 07:12:06 IMAP(xxxxxx): Error: mkdir(/home/xxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxx) egid=1000(xxxxxx) missing +w perm: /home/xxxxxx)
2011-09-04 07:12:07 IMAP(xxxxxx): Error: mkdir(/home/xxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxx) egid=1000(xxxxxx) missing +w perm: /home/xxxxxx)
2011-09-04 07:12:49 IMAP(xxxxxx): Error: mkdir(/home/xxxxxx/Maildir/cur) failed: Permission denied (euid=1000(xxxxxx) egid=1000(xxxxxx) missing +w perm: /home/xxxxxx)
2011-09-04 07:13:24 IMAP(xxxxxx): Info: Connection closed bytes=150/888
2011-09-04 07:16:35 imap-login: Info: Login: user=<xxxxxx>, method=PLAIN, rip=192.168.1.165, lip=192.168.1.212, TLS
2011-09-04 07:18:08 IMAP(xxxxxx): Info: Connection closed bytes=246/4165

```

sudo ls -lha /home/yyyyyy/
drwx------ 37 yyyyyy yyyyyy 4.0K 2011-09-02 19:17 Maildir

sudo ls -lha /home/yyyyyy/Maildir/
drwx------  2 yyyyyy yyyyyy 4.0K 2011-09-02 19:16 cur




my mail server has encrypted home directories, as it started as a desktop installation.
and syslog says

```

Sep  4 07:12:03 SERVER dovecot-auth: pam_sm_authenticate: Called
Sep  4 07:12:03 SERVER dovecot-auth: pam_sm_authenticate: username = [xxxxxx]
Sep  4 07:12:03 SERVER dovecot-auth: Passphrase file wrapped
Sep  4 07:15:50 SERVER kernel: [1007573.965815] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Sep  4 07:16:11 SERVER sudo: pam_sm_authenticate: Called
Sep  4 07:16:11 SERVER sudo: pam_sm_authenticate: username = [xxxxxx]
Sep  4 07:16:11 SERVER sudo: pam_sm_authenticate: /home/xxxxxx is already mounted
Sep  4 07:16:35 SERVER dovecot-auth: pam_sm_authenticate: Called
Sep  4 07:16:35 SERVER dovecot-auth: pam_sm_authenticate: username = [xxxxxx]
Sep  4 07:16:35 SERVER dovecot-auth: pam_sm_authenticate: /home/xxxxxx is already mounted
Sep  4 07:17:01 SERVER CRON[21061]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  4 07:18:39 SERVER dovecot-auth: pam_sm_authenticate: Called
Sep  4 07:18:39 SERVER dovecot-auth: pam_sm_authenticate: username = [xxxxxx]
Sep  4 07:18:39 SERVER dovecot-auth: pam_sm_authenticate: /home/xxxxxx is already mounted
Sep  4 07:21:49 SERVER dovecot-auth: pam_sm_authenticate: Called
Sep  4 07:21:49 SERVER dovecot-auth: pam_sm_authenticate: username = [xxxxxx]
Sep  4 07:21:49 SERVER dovecot-auth: Passphrase file wrapped
Sep  4 07:26:49 SERVER kernel: [1008233.041986] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]

```

I really should preview my posts before I submit.
the ls of the dir and the error were mudged together

---

### Post by nariub on 2011-09-04
Even checked with Squirrelmail
which i have installed

if i have an ssh session open to the mail server
squirrelmail works just fine

if i do not have an open ssh session with the mail server
same serverbug and missing permissions

:-) i guess it is more secure that way, but
???

[http://serverfault.com/questions/223662/using-ecryptfs-encrypted-home-directories-with-dovecot]("http://serverfault.com/questions/223662/using-ecryptfs-encrypted-home-directories-with-dovecot")

---

### Post by e79 on 2011-09-04
I must say I'm a bit lost since I don't know where to look next to try and help you. As seen on your link (and from [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)), it seems like Dovecot doesn't get along with encrypted directory.

I would suggest, if you have the time, to create a Virtual Machine and test your configuration on a non-encrypted file system to see if the issue reoccurs. And maybe it might be a good idea to run your mail server in a Virtual Machine...  Just some thoughts

Regards

---

### Post by nariub on 2011-09-06
It is kinda solved. 
more like irrelevant
I removed encryption from my home directory

ecryptfs has an issue with schroot


where schroot needs to use rbind rather than bind when it encounters an ecryptfs directory

this is likely related to the dovecot issue chrooting over to the local user folder.

I cant fix it.
I gave up.

created a tmpadmin, put it in the admin group
opened a second ssh window as tmpadmin
sudo su -
mkdir /home/tmpuser
cp -a /home/myuser/ to /home/tmpuser

rm -rf /home/tmpuser/.ecryptfs
rm -rf /home/tmpuser/.Private

logout as myuser

rm -rf /home/myuser
mkdir /home/myuser
cp -a /home/tmpuser/ /home/myuser
chown myuser:myuser /home/myuser
cp /home/tmpadmin/.bashrc /home/myuser

logon as myuser
ls -la

logoff as tmpadmin
userdel -r tmpadmin

rm -rf /home/.ecryptfs
rm -rf /home/tmpuser

---

