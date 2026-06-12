---
title: "mod-security"
date: 2009-09-15
forum: Security
---

### Post by phillw on 2009-09-15
I've managed to lock 127.0.0.1 out by getting the p/word wrong 3 times ... No sniggerring ...

evidently 

SecRule REMOTE_ADDR "^127\.0\.0\1$"       phase:1,nolog,allow,ctl:ruleEngine=Off


Turns it off, but where do i put it - also, where is the list of blocked IP's held so i can remove 127.0.0.1?


Thanks


Phill.


P.S. - At least I know it's working :)

---

### Post by phillw on 2009-09-17
Hi,

I've had to turn off mod-security - I still cannot find the answer ... Any ideas, anyone ?

Thanks.

Phill.

---

