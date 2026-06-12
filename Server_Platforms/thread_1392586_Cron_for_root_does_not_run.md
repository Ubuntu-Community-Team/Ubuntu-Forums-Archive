---
title: "Cron for root does not run"
date: 2010-01-28
forum: Server Platforms
---

### Post by eroy4u on 2010-01-28
Cron for root does not run,
it's 8.04LTS ubuntu server,
however Cron runs for other users,
Can anyone help?
i've checked many times that i have the right syntax.

---

### Post by cdenley on 2010-01-28
You're not giving us much information to work with. Where is the cron entry, what is it, and what script is it running? Also, perhaps it has something to do with the root user, so post this output:
```

getent passwd root
sudo getent shadow root|grep "^root\:\!\:"

```

---

### Post by eroy4u on 2010-01-28
thanks and sorry for being so careless.
i just try "sudo crontab -e" and enter "* * * * * touch /root/test.txt", it won't execute although it says "installing crontab" as usual after i saved the crontab file

the output is

```

root:x:0:0:root:/root:/bin/bash

```

---

### Post by cdenley on 2010-01-28
I specifically wrote that command so it wouldn't print any output if it contained a password hash. You apparently ignored the grep part, and posted the previous root password hash! Edit that immediately, and don't re-use what that password may have been!

---

### Post by cdenley on 2010-01-28
Your crontab has no PATH variable. The "touch" command will not be found.
```

* * * * * /bin/touch /root/test.txt

```

---

### Post by eroy4u on 2010-01-28
thanks in fact i know but i've locked root account and it has no password, so i don't care
and thanks to you i found my problem is "locked root account",

do you know another way to remove password for root beside locking?

---

### Post by cdenley on 2010-01-28
> **eroy4u said:**
> thanks in fact i know but i've locked root account and it has no password, so i don't care
and thanks to you i found my problem is "locked root account",

do you know another way to remove password for root beside locking?

You locked it, which prepends the hash with a "!", rendering it invalid thus preventing anyone from authenticating. By default, and to erase your previous password's hash, simply replace the entire hash with "!". You should also remove the expiration.
```

sudo usermod -p ! -e "" root

```

I knew it was locked, but my concern was people typically re-use the same password for things such as your account on this forum.

Once again, you also either need the full path to command, or set the PATH variable.

---

### Post by eroy4u on 2010-01-28
thanks
you mean locking root should not be a problem? however account expiration field being set to 1 causes the cron not run?

thanks for your tip about full path, in fact i used full path "/bin/touch ", just for faster typing i omit it, sorry for causing misunderstanding

---

### Post by eroy4u on 2010-01-28
thanks
you're right it's the expiration that make the crontab not running,
it works now with root locked
thanks

---

### Post by cdenley on 2010-01-28
> **eroy4u said:**
> 
you mean locking root should not be a problem? however account expiration field being set to 1 causes the cron not run?


The password hash shouldn't matter. I think the expiration date does, though. Having it set to "1" means the account expired Jan 2, 1970. Are there errors about the account being expired in /var/log/auth.log?
```

grep cron /var/log/auth.log

```

---

### Post by eroy4u on 2010-01-28
yes it works with expiration set to 1,
isn't it strange? the root account is expired, which is same as before but it works now?

---

### Post by cdenley on 2010-01-28
> **eroy4u said:**
> yes it works with expiration set to 1,
isn't it strange? the root account is expired, which is same as before but it works now?

I just tested it, and if the account is expired, it will not work.

```

sudo usermod -e 1970-01-02 root

```

```

cdenley@ubuntu:~$ grep cron /var/log/auth.log|tail -n 1
Jan 28 11:35:01 MYSYS CRON[17148]: pam_unix(cron:account): account root has expired (account expired)

```

---

### Post by Windows95 on 2010-02-10
> **eroy4u said:**
> Cron for root does not run,
it's 8.04LTS ubuntu server,
however Cron runs for other users,
Can anyone help?
i've checked many times that i have the right syntax.

I have the opposite of this problem,I can't run my job unless logged as root.How can I configure it to run as root?

```
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh

```Thanks in advance.

---

### Post by cdenley on 2010-02-10
Everything except the crontabs for individual users does run as root.

---

### Post by Gfy on 2010-02-16
> **cdenley said:**
> ```

sudo usermod -p ! -e "" root

```

I had the same problem and this solved it. Thanks.

---

### Post by kiddjmadd on 2010-09-09
This worked for me too. X10 home controls are now officially in business.

---

