---
title: "SSSD and local user"
date: 2024-04-18
forum: System76 Support
---

### Post by greg-g91 on 2024-04-18
I encounter a problem when I want to connect with the local user _**WITHOUT**_ the network connection.


 When the network comes back, no problem with local users and ldap (SSSD) users. The SSSD is configured and working.


 According to my research it's in /etc/pam.d in the " **common-*** " configuration files :

 
[LIST]
[*][B]common-account
[/B] 
[*]**common-auth** 
[*]**common-password** 
[*]**common session** 
[/LIST]

 Do you know where the blockage comes from? 
The behavior without the network in the login menu, when entering the password, is in vain.

 Here are my common-conf files:

 ***common-account:***

 ```
account [success=1 new_authtok_reqd=done default=ignore] pam_unix.so
account requisite pam_deny.so
account required pam_permit.so
account sufficient pam_localuser.so
``` 

***common-auth:***
  ```
auth [success=2 default=ignore] pam_unix.so nullok_secure
 auth [success=1 default=ignore] pam_sss.so use_first_pass
 auth requisite pam_deny.so
 auth required pam_permit.so
 auth optional pam_cap.so
```

 ***common-password:***
  ```
password requisite pam_pwquality.so retry=3
 password [success=2 default=ignore] pam_unix.so obscure use_authtok try_first_pass sha512
 password sufficient pam_sss.so use_authtok
 password requisite pam_deny.so
 password required pam_permit.so
 password optional pam_gnome_keyring.so
```

 ***common session:***
  ```
session [default=1] pam_permit.so
 session requisite pam_deny.so
 session required pam_permit.so
 session optional pam_umask.so
 session required pam_unix.so
 session optional pam_sss.so
 session optional pam_systemd.so
 session optional pam_oddjob_mkhomedir.so
 session required pam_mkhomedir.so skel=/etc/skel/umask=0077
```

 Thank you.

---

