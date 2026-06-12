---
title: "Disable login for a group of users"
date: 2011-09-05
forum: Security
---

### Post by mök on 2011-09-05
The system is used as mail server and mail users have normal unix user accounts. All mail users are members of a dedicated group. This group is their primary group, specified in /etc/passwd.

Simply setting the shell for these users to /bin/false is not an option, since their accounts must be able to execute the vacation program for Out of Office replies. Postfix will use users' login shell to execute it.

So far, I have disabled ssh access for mail users by adding a "DenyGroups" option to /etc/ssh/sshd_config.

Now I also want to disable login via tty1-6 and gdm. I trust that this should be possible with PAM, but right now I know nothing about PAM.

Altering the mail server so that mail users are not system users is not an option.

Can someone who knows PAM please give me some hints how I might achieve this?

---

### Post by mök on 2011-09-07
I believe I solved it:

Add

account required pam_access.so

to /etc/pam.d/login and to /etc/pam.d/gdm, and add

-:replacewithgroupname:ALL

to /etc/security/access.conf

I realize I might have posted to the wrong forum location. Feel free to relocate if you can.

---

