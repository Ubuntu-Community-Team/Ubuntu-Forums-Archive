---
title: "Restricting directory access for a user"
date: 2010-08-04
forum: Security
---

### Post by ukukwazi on 2010-08-04
Hi,

I had trouble setting up SFTP and gave up, so I've just got FTP, available for some lowly login, lets say, test_user.

My idea is that if I can restrict test_user's access to his home directory, then I can use FTP and not have to worry about people snooping the password, because they won't be able to do anything.  Like a security sandbox.

Then I can use my su to copy stuff out of test_user's home directory.   

How would I, as root, set test_user's ability to only read his own login dir?  currently he can run around like a maniac, copying anything he wants.

I just want to set one user's permissions, not change folder permissions in general.

How do i do this?
Thanks

---

### Post by .nedberg on 2010-08-04
If you use vsftpd it can be done with
```
chroot_local_user=YES
```
in the config.

If you want it for only some users have a look here:
[http://www.foogazi.com/2007/10/24/quickzi-how-to-jail-vsftpd-users/](http://www.foogazi.com/2007/10/24/quickzi-how-to-jail-vsftpd-users/)

---

### Post by cariboo on 2010-08-04
Proftpd also has that option:

```
# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
#DefaultRoot ~
```

---

