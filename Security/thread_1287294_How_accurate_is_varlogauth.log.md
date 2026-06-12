---
title: "How accurate is /var/log/auth.log?"
date: 2009-10-10
forum: Security
---

### Post by taquinas on 2009-10-10
There are two users A and B.
User A was logged in when user B claims to have restarted the machine (without logging out user A) so that user B can log in to get more bandwidth.
Now the /var/log/auth.log shows that 13 seconds have passed since user A has been logged out and user B logged in. 

In an actual restart the computer can be logged into in 90 seconds.
That's what /var/log/auth.log shows. 

Basically logging out and login in shows 13 seconds difference.
A computer restart and login shows 90 seconds.

So can a restart show a 13 second difference like what the user B claims or has /var/log/auth.log made a mistake. 

I can clarify more if needed.

Thanks for the help.

---

### Post by unspawn on 2009-10-10
In cases like these I'd rely on facts as the system sees it (meaning log entries and logs written to by Syslog) rather than on a human account of events which is definately unreliable. Next to /var/log/{auth,secure,message}* you have got auth and boot records accessable with the 'last' command. 


> **taquinas said:**
> I can clarify more if needed.
Providing actual log lines and auth records could help.

---

### Post by taquinas on 2009-10-11
Thanks for your help. The 'last' command helped me figure it out.

---

### Post by Lars Noodén on 2009-10-11
Be sure to keep the clocks synchronized using ntp or openntp, otherwise that kind of log investigation gets too difficult to be practical.

---

