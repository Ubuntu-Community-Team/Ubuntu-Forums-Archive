---
title: "PHP5 loses sessions randomly"
date: 2008-11-20
forum: Server Platforms
---

### Post by JDiss on 2008-11-20
Hopefully the title is descriptive enough and someone can help.

The symptoms of this problem are that I've isolated a problem to my development server whereas the session will be randomly 'disconnected' from the cookie, resulting in a new, blank session being created.  There's no discernible pattern in terms of either time, number of clicks or query passed that can reproduce the problem. 

In trying to track down this problem, I've tested from three different browsers, two different machines and on two different servers, so I'm 99% certain that the problem is connected to the PHP install on my Ubuntu dev machine.

I have also waded hip-deep through the php.ini (/etc/php5/apache2/php.ini) and nothing seems remiss (It's as vanilla as possible).
I've checked that the session save path is correct (and indeed, I can watch the creation of new sessions).

The code is basically simple, session_start() is called at the top of an include file before any other statement, at random points the session 'forgets' that it's connected to a cookie and goes blank.

Relevant info;
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch

Thanks in advance for any assistance or commiseration

---

### Post by JDiss on 2008-11-26
> **JDiss said:**
> Hopefully the title is descriptive enough and someone can help.


It seems that completely deinstalling PHP5 and apache2, then reinstalling both cured the problem.  There were no other symptoms, errors, log entries other than sessions losing their information randomly.

Hope this helps someone.

---

### Post by Philio on 2008-11-26
I've had problems with Suhosin corrupting sessions, might have been something to do with that. I fixed it by disabling session encryption.

---

