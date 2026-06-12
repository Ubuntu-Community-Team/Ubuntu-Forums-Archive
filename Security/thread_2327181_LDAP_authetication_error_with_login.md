---
title: "LDAP authetication error with login"
date: 2016-06-08
forum: Security
---

### Post by mir4 on 2016-06-08
I have LDAP client setup using nss and pam . I have the below error in /var/log/auth.log . When an LDAP user logs in it logs in successfully but throws a error before logging in .


Jun  8 13:38:29 S000001 login[19167]: pam_unix(login:auth): authentication failure; logname=amir uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=amir
Jun  8 13:38:29 S000001 login[19167]: pam_unix(login:session): session opened for user amir by amir(uid=0)

I have the authentication to check local accounts first and then ldap user accounts . I know swapping the pam_unix and pam_ldap in common-auth file fixes it .
But I would like to search my local accounts first that is the reason I have pam_unix first and then pam_ldap module in common-auth.
 Is there any other way ,I can suppress the authentication failure line in auth.log.
Any help would be great guys !!!!


These are how my common-* files look like

common-auth
auth    required                pam_env.so
auth    required                pam_tally2.so onerr=fail deny=6 unlock_time=180
auth    sufficient              pam_unix.so
auth    sufficient              pam_ldap.so try_first_pass
auth    required                pam_deny.so



common-account
account requisite                       pam_unix.so
account required                        pam_tally.so
account sufficient                      pam_localuser.so
account required                        pam_ldap.so use_first_pass


common-session
session required                        pam_limits.so
session required                        pam_unix.so
session optional                        pam_ldap.so






common-password
password        [success=2 default=ignore]      pam_unix.so sha512 shadow nullok try_first_pass
password        [success=1 user_unknown=ignore default=die]     pam_ldap.so try_first_pass
password        requisite                       pam_deny.so
password        required                        pam_permit.so
password        optional        pam_gnome_keyring.so

---

