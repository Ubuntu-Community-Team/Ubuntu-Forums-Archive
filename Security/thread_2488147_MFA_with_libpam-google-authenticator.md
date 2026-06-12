---
title: "MFA with libpam-google-authenticator"
date: 2023-06-24
forum: Security
---

### Post by ixeous on 2023-06-24
I'm trying to get MFA working for SSH logins to a new Ubuntu 22.04 server.  I've installed the module and it is "working", but not exactly as I would like.  I'm trying to match the functionality I have on a different distro and it's not quite there.  Specifically, on Ubuntu, if I attempt to login with an invalid username or invalid password, it simply prompts for the password again.  On the other distro, it will always prompt for the verification code even if the user is non-existent or the user is real but the password is wrong.  I prefer this because it does not tell someone (or bot) what they have wrong.  How can I have the Ubuntu system perform the same way?  This is only for SSH login.

I've tried comparing /etc/pam.d/sshd files, but they are very different.  I've tried to add additional auth required entries to match, as well as the forward_pass option but nothing seems to get what I want.  Does anyone know the magic formula to get this functionality?

The other system login appears as:

[FONT=monospace][COLOR=#000000]$ ssh not_a_real_user@my-server [/COLOR]
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]my-server[/COLOR][/FONT][FONT=monospace]) Password:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]my-server[/COLOR][/FONT][FONT=monospace]) Verification code:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]my-server[/COLOR][/FONT][FONT=monospace]) Password:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]my-server[/COLOR][/FONT][FONT=monospace]) Verification code:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]my-server[/COLOR][/FONT][FONT=monospace]) Password: 


The Ubuntu system is:
[/FONT][FONT=monospace][COLOR=#000000]$ ssh -p 6200 not_a_real_user@ubuntu-server [/COLOR]
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]ubuntu-server[/COLOR][/FONT][FONT=monospace]) Password:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]ubuntu-server[/COLOR][/FONT][FONT=monospace]) Password:  
(not_a_real_user@[/FONT][FONT=monospace][COLOR=#000000]ubuntu-server[/COLOR][/FONT][FONT=monospace]) Password: 


/etc/pam.d/sshd

[/FONT][FONT=monospace][COLOR=#000000]# Standard Un*x authentication. [/COLOR]
@include common-auth 
auth    required        pam_google_authenticator.so nullok forward_pass secret=/home/${USER}/.ssh/.google_authenticator



/etc/ssh/sshd_config

[/FONT][FONT=monospace][COLOR=#000000]# Change to yes to enable challenge-response passwords (beware issues with [/COLOR]
# some PAM modules and threads) 
KbdInteractiveAuthentication yes
[/FONT][FONT=monospace][/FONT][FONT=monospace]
[/FONT]

---

### Post by CharlesA on 2023-06-24
It might help if you say what the other distro is.

My bet is that you need to authenticate with the correct password to trigger the 2FA code. I haven't tried setting it up like that on my boxes, so that's just a guess.

---

### Post by ixeous on 2023-06-24
The other distro is Rocky 8.  You are correct that if I use a correct user/password, then it will prompt.  The difference is on the other distro, it prompts when given an invalid user, a valid user with invalid password, and valid user with valid password.  Because there's no difference in how the service acts, there's no information given of "you got a valid username and password".  It also seemed to reduce the number of bot attempts in logs.

---

### Post by ixeous on 2023-06-24
It is definitely something in /etc/pam.d/sshd.  I copied the exact contents from the Rocky 8 version to Ubuntu and it behaved the same as I described.  I'm not sure exactly which part made it work that way though.  Guess I'll play around and figure it out.  I would prefer the file to be as default as possible on Ubuntu.

---

### Post by CharlesA on 2023-06-24
Could you post the two in code tags? I'm curious as to what the differences are.

---

### Post by ixeous on 2023-06-24
I think it has something to do with common-auth.  When I move the google-authenticator line in Ubuntu above the @include common-auth, I get a verify prompt for 2fa first in all situations.  That was completely missing from the Rocky verison.


Ubuntu:
```

[FONT=monospace][COLOR=#000000]# cat sshd [/COLOR]
# PAM configuration for the Secure Shell service 

# Standard Un*x authentication. 
@include common-auth 
auth    required        pam_google_authenticator.so nullok secret=/home/${USER}/.ssh/.google_authenticator 

# Disallow non-root logins when /etc/nologin exists. 
account    required     pam_nologin.so 

# Uncomment and edit /etc/security/access.conf if you need to set complex 
# access limits that are hard to express in sshd_config. 
# account  required     pam_access.so 

# Standard Un*x authorization. 
@include common-account 

# SELinux needs to be the first session rule.  This ensures that any 
# lingering context has been cleared.  Without this it is possible that a 
# module could execute code in the wrong domain. 
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so close 

# Set the loginuid process attribute. 
session    required     pam_loginuid.so 

# Create a new session keyring. 
session    optional     pam_keyinit.so force revoke 

# Standard Un*x session setup and teardown. 
@include common-session 

# Print the message of the day upon successful login. 
# This includes a dynamically generated part from /run/motd.dynamic 
# and a static (admin-editable) part from /etc/motd. 
session    optional     pam_motd.so  motd=/run/motd.dynamic 
session    optional     pam_motd.so noupdate 

# Print the status of the user's mailbox upon successful login. 
session    optional     pam_mail.so standard noenv # [1] 

# Set up user limits from /etc/security/limits.conf. 
session    required     pam_limits.so 

# Read environment variables from /etc/environment and 
# /etc/security/pam_env.conf. 
session    required     pam_env.so # [1] 
# In Debian 4.0 (etch), locale-related environment variables were moved to 
# /etc/default/locale, so read that as well. 
session    required     pam_env.so user_readenv=1 envfile=/etc/default/locale 

# SELinux needs to intervene at login time to ensure that the process starts 
# in the proper default security context.  Only sessions which are intended 
# to run in the user's context should be run after this. 
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so open 


# Standard Un*x password updating. 
@include common-password
[/FONT]
```
[FONT=monospace]
Rocky 8:
[/FONT]```

[FONT=monospace][COLOR=#000000]#%PAM-1.0 [/COLOR]
auth       substack     password-auth 
auth       include      postlogin 
account    required     pam_sepermit.so 
account    required     pam_nologin.so 
account    include      password-auth 
password   include      password-auth 
# pam_selinux.so close should be the first session rule 
session    required     pam_selinux.so close 
session    required     pam_loginuid.so 
# pam_selinux.so open should only be followed by sessions to be executed in the user context 
session    required     pam_selinux.so open env_params 
session    required     pam_namespace.so 
session    optional     pam_keyinit.so force revoke 
session    optional     pam_motd.so 
session    include      password-auth 
session    include      postlogin 
auth    required        pam_unix.so     no_warn try_first_pass 
auth    required        pam_google_authenticator.so nullok secret=/home/${USER}/.ssh/.google_authenticator 
[/FONT]
```

---

### Post by ixeous on 2023-06-25
I do have it working as I want.  In /etc/pam.d/sshd, I commented out @include common-auth and added 2 auth lines that matched the end of the file on Rocky.

[FONT=monospace]```

# Standard Un*x authentication. 
@include common-auth 

```

became

[/FONT]```
[FONT=monospace]
# Standard Un*x authentication.
#@include common-auth 
auth    required        pam_unix.so     try_first_pass 
auth    required        pam_google_authenticator.so nullok secret=/home/${USER}/.ssh/.google_authenticator
[/FONT]
```[FONT=monospace]


[/FONT]

---

### Post by CharlesA on 2023-06-25
Interesting. Thanks for letting us know how you got it working. :)

---

