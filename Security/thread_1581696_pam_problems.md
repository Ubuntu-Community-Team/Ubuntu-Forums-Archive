---
title: "pam problems"
date: 2010-09-25
forum: Security
---

### Post by jmc-rit on 2010-09-25
I am trying to wrap my brain around a pam problem we are having on our system

User accounts are stored in an openldap database on another machine; the 10.04 machines are clients.

I know that ldap is connecting because I can get valid user information via getent.
However during login I've discovered a serious flaw in how pam is set up.

If a local user logs in with a valid password, they log in cleanly
If a local user logs in with a blank password, it says login incorrect and fails.
If a local user logs in with an invalid password, it says login incorrect and fails.

So far so good.  But if the user is in LDAP:

if an ldap user logs in with a valid password, it says:
"Your account has expired; please contact the system administrator"
yet logs them in anyways.

if an ldap user provides an invalid password, it says login incorrect and fails.

if an ldap user provides a blank password, it says:
"Your account has expired; please contact the system administrator"
yet logs them in anyways.

this works with su - username as well as when unlocking the screensaver.
Effectively anyone can log in as anyone else, despite the blank password.

common-auth:
auth       required     pam_env.so
 auth       sufficient   pam_unix.so likeauth nullok
#the following line (containing pam_group.so) must be placed before pam_ldap.so 
#for ldap users to be placed in local groups such as fuse, plugdev, scanner, etc..
auth       required     pam_group.so use_first_pass
auth       sufficient   pam_ldap.so use_first_pass
auth       required     pam_deny.so

common-account:
# here are the per-package modules (the "Primary" block)
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so 
account [success=1 default=ignore]      pam_ldap.so 
# here's the fallback if no module succeeds
account requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

common-password:
# here are the per-package modules (the "Primary" block)
password        requisite                       pam_passwdqc.so
password        [success=2 default=ignore]      pam_unix.so obscure use_authtok 
try_first_pass sha512
password        [success=1 default=ignore]      pam_ldap.so try_first_pass
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
password        optional        pam_gnome_keyring.so
# end of pam-auth-update config

common-session:
# here are the per-package modules (the "Primary" block)
session [default=1]                     pam_permit.so
# here's the fallback if no module succeeds
session requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so  
session optional                        pam_ldap.so nonull_secure 
session optional                        pam_ck_connector.so nox11
# end of pam-auth-update config




Thoughts?

---

### Post by luvshines on 2010-09-25
Maybe the LDAP server doesn't exercise tight password rules

Check the graceloginattempts and the pwdminlength for the users

---

### Post by jmc-rit on 2010-09-25
At the moment I have found that if I just set common-account to 

account required                        pam_permit.so

I no longer see the 
"Your account has expired; please contact the system administrator" any more. I know this will be an issue, but at the moment I am trying to tackle why a user can log in with an empty password.

   pam_ldap.so seems to think this is sufficient.

---

### Post by luvshines on 2010-09-25
you are setting pam_permit.so as a single line for common-account ??

AFAIK pam_permit.so will allow all accounts to pass through,
[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_permit.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_permit.html)

This may totally disable the account checking :) which can be dangerous

In your earlier setting, 
account [success=1 default=ignore] pam_ldap.so 

account requisite pam_deny.so

account required pam_permit.so

pam_ldap.so was returning success and was skipping one line that is pam_deny.so and directly reaching pam_permit.so as it was guided to do so [ success=1 ]
If pam_ldap.so itself will return false, I think that will do

So I asked you to check the ldap password policy rules

---

### Post by luvshines on 2010-09-25
Though I haven't checked 'chage' command with LDAP users can you give it a try

chage -l <username>

It will info like:

sudo chage -l scoobydo

Last password change					: Sep 23, 2010
Password expires					: Dec 22, 2010
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 1
Maximum number of days between password change		: 90
Number of days of warning before password expires	: 7

---

### Post by luvshines on 2010-09-25
Oh, just checked it, chage not working with LDAP users. Bad :( !!

---

### Post by luvshines on 2010-09-25
Try an ldapsearch for any LDAP user and see what all info you get

---

### Post by jmc-rit on 2010-09-25
Sorry for not coming back sooner with any input.

as far as I have understood,  common-account was just to check for expired accounts,
or accounts that don't have login on the machine.  currently I am not expiring passwords,
and accounts that are expired themselves are locked with other tools (passwords changed,
chmod 000 HomeDir, etc) so I think for now this isn't a big deal for us.
What I have discovered is that I need to figure out what pam_ldap uses to decide if an 
account is expired. I played around with the shadow settings on one of the ldap accounts and it seems that nothing I did changed it's behavior.

What I have been focused on is that pam_ldap will return success if you provide an empty password. what I have learned is, under the hood ldap will do a null binding and succeed at that, but fail at authenticating.  pam_ldap sees the success in binding and calls it all a success.  This was why a blank password worked as well as a correct password.
I have since changed common-auth to this:

        auth       required     pam_env.so 
        auth       required     pam_group.so use_first_pass 
        auth       sufficient   pam_unix.so 
        auth       [auth_err=bad]   pam_ldap.so use_first_pass
        auth       required     pam_deny.so 

and as far as I can tell it behaves as I want it to on login.

EXCEPT ... 
gnome screensaver fails and claims I can't authenticate.
So I am now trying to work that one out...

---

