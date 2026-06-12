---
title: "init scripts without root privilege"
date: 2008-10-09
forum: Security
---

### Post by greatmercy on 2008-10-09
Hi,

Am setting up a server to run tomcat automatically at startup.  Can do this no problem, but tomcat runs as root.

Am told by the apache community that running tomcat as root is a 'very bad idea' in case it were to get compromised.  Also, if i'm not listening on a port below 1024 (and I'm not), then there really is no need to run tomcat with such high privileges.

So, I've set my init script to call tomcat with:
su - myaccount - c "sh tomcat/bin/startup.sh"

When I run the script myself, as sudo, it works fine.  But, when running at boot up it doesn't.  Why not?  I guess because it needs the password for myaccount, and no-one's there to type it in.

Is there a way around this?  Or another way to start tomcat with lesser privileges?  Or shouldn't I care?

Many thanks,

---

### Post by cdenley on 2008-10-09
> **greatmercy said:**
> Hi,
When I run the script myself, as sudo, it works fine.  But, when running at boot up it doesn't.  Why not?  I guess because it needs the password for myaccount, and no-one's there to type it in.

It works when you run
```

sudo tomcat/bin/startup.sh

```
or
```

sudo /etc/init.d/tomcat start

```
???

You should give the full path to startup.sh. If you have problems with su, you can try sudo. I'm not very familiar with su's syntax, but I don't think you used it correctly.
```

man su

```
> 
When - is used, it must be specified as the last su option.

Also, why is there a space between the "-" and the "c"?

Since the init script is run as root, you shouldn't be prompted for any passwords.

---

### Post by greatmercy on 2008-10-09
Thanks.  Thanks.

It was a problem in the su parameters.  All sorted now.

---

### Post by albertwt on 2010-11-25
how did you do it man ? 

please share it here.

Thanks.

---

### Post by cariboo on 2010-11-26
@albertwt, do you realize that this thread is over two years old, and the op hasn't logged in since. You may be better off starting a new thread, as this one is closed.

---

