---
title: "PAM in auth.log after upgrade to 8.04"
date: 2008-04-26
forum: Server Platforms
---

### Post by dacool25 on 2008-04-26
Hey everybody,

I just upgraded my server to 8.04 from 7.10 last night, and now my auth.log files are filling up with the following:

```
Apr 26 13:17:01 myserver CRON[7829]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 26 13:17:01 myserver CRON[7829]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 26 13:17:01 myserver CRON[7829]: pam_unix(cron:session): session closed for user root  
Apr 26 13:30:01 myserver CRON[7996]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 26 13:30:01 myserver CRON[7996]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

```

How can I fix this?

---

### Post by Caalador on 2008-04-27
Confirm you're not missing /lib/security/pam_smbpass.so.

If you are, then install libpam-smbpass package.

```

aptitude install libpam-smbpass
```

---

### Post by dacool25 on 2008-04-27
Wasn't it removed in 8.04?

---

### Post by pot_roast on 2008-05-04
1) Open these two files:
/etc/pam.d/common-password 
/etc/pam.d/common-auth

2) Comment out the smbpass entries

(Found this fix in the related bug report)

---

