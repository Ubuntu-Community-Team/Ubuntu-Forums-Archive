---
title: "Cobbler GUI stuck after restart"
date: 2011-12-01
forum: Ubuntu Cloud and Juju
---

### Post by theatreguy on 2011-12-01
Hi,

I'm running 11.10 server on a IBM x3455. 
When I install orchstra, the Cobbler GUI (/cobbler_web) initialy works without problems. However, after "cobblerd restart" or a system reboot, I am unable to log in with the same credentials.
The login page is still served (not cached), but when submitting the login, it simply gets stuck, no error message.

I have tried adding a new user with htdigest /etc/cobbler/users.digest Cobbler user, which was successful, but still would not allow me to log in.

Does anyone have the same problem, or can point me where to look for the problem?

thanks,
theatreguy

---

### Post by UnitedWays on 2012-03-28
Hi theatreguy,

Did you solve this issue? I'm having the same problems here but can't find a way around it..

Cheers and thanks in advance!

---

### Post by theatreguy on 2012-03-28
Hi,

I'm afraid I did not so far.
At one stage I was sure that it was an httpd.conf issue, but then I found that the PXE service wasn't accessible after restart either.
Gone back to Win Server 2000 for the time being, hoping Precise Pangolin might shed some light on the issue - I'll keep trying!
T

---

