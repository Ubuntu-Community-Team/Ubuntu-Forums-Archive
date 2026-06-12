---
title: "using pam.d to restrict login time"
date: 2009-01-27
forum: Security
---

### Post by imaca on 2009-01-27
Hi,
I would like to restrict the time users can be logged in.

I have un commented:
account    requisite  pam_time.so
in file etc/pam.d/login

and added
login ; * ; bob ; Al1500-2100
to file etc/security/time.conf

From what I have read I was expecting this would restrict user "bob" from logging in after 2100 or before 1500. Was also hoping it would force "bob" to logout at 2100.
In fact there seems to no effect whatsoever.
What have I done wrong?

---

### Post by daevski on 2009-09-30
I'm doing almost exactly what you are, and it's not working for me either. 

My time.conf:
*;*;testuser;SuMoTuWeTh2000-2300

Sunday-Thursday, user shouldn't be able to login anytime except 8pm-11pm... no?

Any help would be appreciated.

---

