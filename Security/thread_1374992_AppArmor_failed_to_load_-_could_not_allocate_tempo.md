---
title: "AppArmor failed to load - could not allocate temporary file"
date: 2010-01-07
forum: Security
---

### Post by negativ on 2010-01-07
I get the error message in the subject line, followed by a red failed message.

However, once the system is finished booting, I can log in and 
```
sudo /etc/init.d/apparmor start 
```
and it starts normally.

Any ideas what may be going on?

this is 9.04 server

---

### Post by negativ on 2010-01-07
*boing*

---

### Post by running_rabbit07 on 2010-01-07
I must say that it looks like AppArmor is unable to find a certain file while the system is still booting. If your run ```
sudo aa-genprof <profile>
``` you should be able to fix this. That is if the warning you are getting tells you the name of the profile that is having the problem.

---

### Post by running_rabbit07 on 2010-01-07
You can also go to /var/log/apparmor and see if there are any log messages.

---

### Post by running_rabbit07 on 2010-01-07
> **logprof | aa-logprof**
 	Quote:
 	 	 		 &#65279;Manage AppArmor profiles. logprof is an interactive tool used to review the learning or complain mode output found in the AppArmor syslog entries and to generate new entries in AppArmor profiles. 

Check this out, too.

---

### Post by bodhi.zazen on 2010-01-08
> **negativ said:**
> I get the error message in the subject line, followed by a red failed message.

However, once the system is finished booting, I can log in and 
```
sudo /etc/init.d/apparmor start 
```and it starts normally.

Any ideas what may be going on?

this is 9.04 server

My guess is that this is due to "concurrency". The boot process is changing and boot scripts are run concurrently, so, how are your logs configures ? Are they on a separate partition ? Are you running in a virtual machine of some kind ?

My guess is that apparmor is starting before your logs are available.

---

### Post by shred_eng on 2010-02-01
did you solve this problem ? because i also have this message now. it has only just started complaining and has been alright up until now.if it cant gain access to its temp file, how can i resolve this? ...ideas?

thanks,

---

### Post by shred_eng on 2010-02-02
hi, although the error is , could not allocate temporary file , at startup, when i type:

sudo /etc/init.d/ apparmor start 

it says : starting apparmor
skipped: apparmor already loaded with profiles

does this mean that everything is working fine and if i just ignore the error, there is no problems?

thanks,

---

