---
title: "Allowing non-anonymous uploads with vsftpd"
date: 2010-02-02
forum: Security
---

### Post by climhazzard on 2010-02-02
Hi all,

Hope you can help me out.  I'm trying to setup a "drop-box" on ubuntu 9.10 server with vsftpd.  I'm able to login and land in the /home/user directory, however I cannot write anything.  Thanks for your help.

---

### Post by kiranmurari on 2010-02-03
Hi,

Can you check if the following macro is enabled in /etc/vsftpd.conf
```
write_enable=YES
```This macro is by default disabled (commented). Enable this and restart vsftpd.

Hope this helps.

---

### Post by climhazzard on 2010-02-03
Thank you for the reply, the write_enable was set to YES.

---

### Post by kiranmurari on 2010-02-04
> **climhazzard said:**
> Thank you for the reply, the write_enable was set to YES.So is the issue solved...?
If not, can you post your vsftpd.conf file?
Also which user are you logging in as and which home directory do you land in?

---

### Post by climhazzard on 2010-02-09
> **kiranmurari said:**
> So is the issue solved...?
If not, can you post your vsftpd.conf file?
Also which user are you logging in as and which home directory do you land in?

Sorry for the late reply.  I ended up uninstalling vsftpd and went with proftp...working great now.  Thanks for your help!

---

### Post by warbaby on 2010-02-12
on 9.10/64 the default home dir (made by the installer) was /srv/ftp


```
root@ns2:/srv/ftp# tail -n 1 /etc/passwd
ftp:x:111:123:ftp daemon,,,:/srv/ftp:/bin/false

```so...
```

# cd /srv/ftp
# mkdir incoming
# chmod 777 incoming

```This should solve the anonymous "can't write: problem for the next guy who reads this thread.

---

