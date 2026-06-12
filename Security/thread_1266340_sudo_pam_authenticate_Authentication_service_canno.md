---
title: "sudo: pam_authenticate: Authentication service cannot retrieve authentication info"
date: 2009-09-14
forum: Security
---

### Post by newpreludeking on 2009-09-14
I have successfully installed LDAP Server in Ubuntu 8.04 LTS and it was working fine. I was trying to configure the LDAP Client and I edited the following files

/etc/pam.conf
*/etc/nsswitch.conf*[B]
**/etc/pam.d/common-account**  [/B]


about to edit these two files...

**[B]/etc/pam.d/common-auth**
[/B]**[B]/etc/pam.d/common-password**[/B]

as per the instructions given in the tutorial link except I opened /etc/pam.conf in gedit and saved it.

Now none of the logins are working. now I want to revert back to original state and I am not able to logon using sudo, or even as a normal user. can anyone suggest to recover the authentication service ? 

Thanks

---

### Post by gwmullin on 2009-09-29
If you reboot and add 'init=/bin/bash' to your grub line, you will boot into a root shell.

~Greg

---

