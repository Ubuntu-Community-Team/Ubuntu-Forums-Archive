---
title: "Ubuntu Server 14.04.1 login incorrect"
date: 2014-11-06
forum: Server Platforms
---

### Post by dementhor on 2014-11-06
Hello,

Suddenly when I try to enter my username in order to login to my Ubuntu Server OS, I get the error message of "Login incorrect". I am not receiving any prompts to enter the password. Unfortunatelly this is the only admin account. All services are starting OK, and everything else seems to work fine as before.

Are any of you aware of this issue?

Thanks!

---

### Post by andrew102 on 2014-11-06
How are you logging in: over SSH or console? 
Are you able to determine if it is a network or firewall problem.

"everything else seems to work" - are you running a web server ? is there some way to check for code base changes?

If you have another unprivileged account that you are able to log into - try running the ```
 lastlog 
``` command from a terminal - it will tell you when users last logged in. Might help to determine if somebody has changed the login/password config.

---

### Post by dementhor on 2014-11-06
I tried via SSH and on the machine itself and I encountered the same error. So, there is no network or firewall problem.

There is no webserver running.

There is no other user able to login.

Thanks!

---

### Post by cariboo on 2014-11-06
Can you start in recovery mode, then run:

```
last
```

to see if any one else has logged in.

---

### Post by TheFu on 2014-11-06
CAPSLOCK?

And don't be offended, but I've come across a Windows Admin trying to use his full "first{space}lastname" as the login. UNIX logins are 1 word, lowercase.  I helped him hack into the system 5 times before actually watching him attempt to login myself. jsmith, not "John Smith".

If you are really stuck, you can hack in with physical access. Lots of how-tos for that out there - look for "reset login password ubuntu" [http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/) is one.

---

