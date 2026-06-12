---
title: "[samba] &quot;valid users&quot; has been removed, what is the replacement?"
date: 2014-05-02
forum: Server Platforms
---

### Post by bimbo on 2014-05-02
the valid users directive in samba to restrict access to a share to specific users seems to have been removed in Samba4. So how do I prevent users from accessing those shares (for a number of reasons, UNIX permissions to prevent them from reading the files that are not really an option as some daemons need access and are running under the same UID)?

---

### Post by bab1 on 2014-05-02
> **bimbo said:**
> the valid users directive in samba to restrict access to a share to specific users seems to have been removed in Samba4. So how do I prevent users from accessing those shares (for a number of reasons, UNIX permissions to prevent them from reading the files that are not really an option as some daemons need access and are running under the same UID)?

What makes you say that?  The man pages show it is still an available option.  I have seen where other users use that option.

The smbd daemon is the same as in Samba v3.6 and the smb.conf file is essentially the same.

---

### Post by bimbo on 2014-05-03
Turns out, it's me being stupid that makes me say this. I had error reports in the lgo about it not being supported but seems like a special char somehow got in there.... 

Thanks a lot, anyway :)

---

