---
title: "Correct setquota syntax?"
date: 2009-02-09
forum: Server Platforms
---

### Post by mysteron on 2009-02-09
Hi.

I'm trying to run the following command on a ubuntu server:

setquota -u test 50000 75000 5000 10000

and all I get is the help message for the setquota command.

Please help :)


Regards,
/mysteron

---

### Post by mysteron on 2009-02-09
Ok... I should have read the error message... It was so obvious...

setquota -u test 50000 75000 5000 10000

should be

setquota -u test 50000 75000 5000 10000 /home/


Case closed.

---

