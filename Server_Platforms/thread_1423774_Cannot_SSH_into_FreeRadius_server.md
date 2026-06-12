---
title: "Cannot SSH into FreeRadius server"
date: 2010-03-07
forum: Server Platforms
---

### Post by D.Sync on 2010-03-07
Hi guys, I had googled for the past 8 hours trying to figure out how to properly setup openSSH, FreeRadius and PAM. The main objective here is to using SSH to authenticate a user into FreeRadius server.

So far whenever I tried to SSH into the freeradius, it didn't connect to the FreeRadius server as there is no message displayed when running on debug mode via radiusd -X. 

Any idea on what's going wrong?

Things I had done:
- Included the PAM module in /usr/local/etc/raddb/radiusd.conf
```
modules {


       pam {
                #
                #  The name to use for PAM authentication.
                #  PAM looks in /etc/pam.d/${pam_auth_name}
                #  for it's configuration.
                #
                #  Note that any Pam-Auth attribute set in the 'users'
                #  file over-rides this one.
                #
                pam_auth = radiusd
        }
}
```


- Uncomment PAM in /usr/local/etc/raddb/sites-enabled/default
- Installed openssh via repository

Here's the radiusd file under /etc/pam.d
```
#%PAM-1.0
auth       required     /lib/security/pam_unix_auth.so shadow md5 nullok
auth       required     /lib/security/pam_nologin.so
account    required     /lib/security/pam_unix_acct.so
password   required     /lib/security/pam_cracklib.so
password   required     /lib/security/pam_unix_passwd.so shadow md5 nullok use_authtok
session    required     /lib/security/pam_unix_session.so
```

And here's the sshd file under /etc/pam.d
```
#%PAM-1.0
auth       sufficient   /lib/security/pam_radius_auth.so
auth       include      system-auth
#auth       sufficient   /lib/security/pam_radius_auth.so
account    required     pam_nologin.so
account    include      system-auth
password   include      system-auth
session    optional     pam_keyinit.so force revoke
session    include      system-auth
session    required     pam_loginuid.so
```

---

