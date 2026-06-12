---
title: "Password should be 8 characters at minimum"
date: 2004-11-02
forum: Server Platforms
---

### Post by Charlotte on 2004-11-02
Hi all,

I really wish preventing my users from choosing passwords being shorter than 8 characters but up to now I failed to do so.

First of all I installed cracklib and edited /etc/pam.d/passwd as it is described in the Ubuntu help ("Cracklib2 - a pro-active....). 
There I set the parameter "minlen" to 8. 
No hope - the system accepted a password with a minimum of 6 characters, 
but rejected some as too "simplicistic" or having not enough different characters and so on. 

After guessing /etc/pam.d/common-password might have to be edited, 
too I did that to my best setting there the minlen parameter to 8 either.
Same results as described above.

Any idea what's going wrong?

Surprisingly using the GUI interface to create test accounts after installing 
Cracklib Ubuntu seems to find 4 characters making up a sufficient password... - 
maybe a feature?

Thanks for your help in advance.

Regards,
Charlotte

---

