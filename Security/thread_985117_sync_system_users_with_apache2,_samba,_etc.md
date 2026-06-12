---
title: "sync system users with apache2, samba, etc?"
date: 2008-11-17
forum: Security
---

### Post by IndieRockSteve on 2008-11-17
Hi all! I'd like to know if its possible to sync the users of the system with Apache2 (currently I'm just using httpd-passwords) and samba so that I can create accounts for the people I live with so that they will have a single password that if they change gets changed across the board?

I'm not really sure what terms to search for in google for this, so even help in just what this is called so I can do some research would be helpful, thanks!

---

### Post by cdenley on 2008-11-17
> **IndieRockSteve said:**
> Hi all! I'd like to know if its possible to sync the users of the system with Apache2 (currently I'm just using httpd-passwords) and samba so that I can create accounts for the people I live with so that they will have a single password that if they change gets changed across the board?

I'm not really sure what terms to search for in google for this, so even help in just what this is called so I can do some research would be helpful, thanks!

If you want apache to authenticate using your system password, install and configure libapache2-mod-auth-pam. Samba can't use your system password, because it needs an NT hash. I think samba, by default, is configured to update the system password when the NT password is changed. I'm not sure if PAM is or can be configured to update the samba password.

---

### Post by IndieRockSteve on 2008-11-18
> **cdenley said:**
> If you want apache to authenticate using your system password, install and configure libapache2-mod-auth-pam. Samba can't use your system password, because it needs an NT hash. I think samba, by default, is configured to update the system password when the NT password is changed. I'm not sure if PAM is or can be configured to update the samba password.

Ok, so if I have SAMBA users that match system users and I set it so SAMBA updates the system password if a change is made to its password then I could set it up so all the user would have to do is change their password in SAMBA and the system password would change which would mean the password APACHE uses would change (assuming I install and configure that mod as you state).

Is there a web-based system I could setup that would allow the users to modify their password in SAMBA?

Thanks!!

---

### Post by cdenley on 2008-11-18
> **IndieRockSteve said:**
> 
Is there a web-based system I could setup that would allow the users to modify their password in SAMBA?


Not that I know of.

---

### Post by IndieRockSteve on 2008-11-18
cool, thanks for the help!

---

