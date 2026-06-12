---
title: "can't seem to ssh to my server"
date: 2010-08-24
forum: Server Platforms
---

### Post by williamburn on 2010-08-24
I have setup 10.04.1 and completed the open ssh server install, changed the /etc/ssh/sshd_config file to allow my user -- AllowUsers wburn -- to SSH, but still cannot connect remotely.  I get prompted for the login, but the authentication doesn't pass properly or allow me to log in.

netstat -ant | grep 22 -->

tcp     0     0 0.0.0.0:22   0.0.0.0:*     LISTEN

I have also updated /etc/hosts.allow to allow:

ALL:ALL


Any suggestions, and thanks

---

### Post by CharlesA on 2010-08-24
Are you able to ssh to localhost? That'll tell you if ssh is installed and configured correctly.

Are you using pub key authentication or password authentication?

Encrypted home directory?

---

### Post by williamburn on 2010-08-24
Yes, ssh localhost works.  I am using password authentication.  This server is on my lan and will not be used to authenticate externally.  No encryption on the homedir.

---

### Post by CharlesA on 2010-08-24
Try using ssh -vvv user@host and post the results.

---

### Post by williamburn on 2010-08-24
I am logged into the iDRAC interface and am unable to capture the output of the -vvv session.  apparently > redirecting it to a file doesnt work either.  Do you know of a way to redirect the session to a text file that I can copy and paste or check the logs.  When i try putty from another box I get the prompt so I know SSH is in fact working, and it works locally.  However I get access denied.  It seems to me that it doesnt like my user.

---

### Post by CharlesA on 2010-08-24
I don't know if you can redirect it to a file or not, maybe by using tee and sending it to a file.

```
ssh -vvv user@host | tee > ~/somefile
```

What does /var/log/auth.log say?

---

### Post by williamburn on 2010-08-24
Charles, thanks a lot for the help.  Apparently, the iDRAC keyboard doesnt map the keys properly.  On a whim, i changed my password to abc and guess what.  it works.  the iDRAC keyboard doesnt map special chars properly.

Thanks again...

---

### Post by CharlesA on 2010-08-24
Good to hear you got it working. :)

---

