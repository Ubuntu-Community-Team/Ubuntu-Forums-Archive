---
title: "Problems with PAM Tester"
date: 2009-04-11
forum: Ubuntu Dev Link Forum
---

### Post by ritchie-w on 2009-04-11
Hi,

I am working with the pamtester to understand the PAM concept.

Does somebody knows, why I can not use another user than the 
actual user for pamtester. Please see the attached "Screenprintout" 
of a terminal session with pamtester. 

Here the definition of the service "bdo"

> 
auth       required     pam_unix.so
account    required     pam_unix.so


Does someone has a hint for me, where too look ?
The main reason is, that I am write a PAM function for a GUI appplication
and the function works only for the actual linux user.

Thanks for any help

Ritchie

Solved: needs roots rights

---

