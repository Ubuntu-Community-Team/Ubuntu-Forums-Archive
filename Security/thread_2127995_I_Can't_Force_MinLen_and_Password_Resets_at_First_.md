---
title: "I Can't Force MinLen and Password Resets at First Login"
date: 2013-03-21
forum: Security
---

### Post by charliemp3 on 2013-03-21
I need to be able to force users to choose a password that is at least 14 characters long. They also need to reset their temp passwords at first login. 

This is what my /etc/pam.d/common-auth looks like right now:

[I]auth    required    pam_env.so
auth    required    pam_tally.so per_user    deny=3    unlock_time=30
auth     sufficient    pam_unix.so    nullok    try_first_pass
auth    requisite    pam_succeed_if.so uid >= 500 quiet
auth    required    pam_deny.so

account    required    pam_unix.so
account    sufficient    pam_succeed_if.so uid < 500 quiet
account    required    pam_permit.so

password    required    pam_craklib.so    try_first_pass    retry=3
password    sufficient    pam_unix.so    md5    shadow    nullok    try_first_pass     use_authtok
password    required    pam_permit.so

session    optional    pam_keyinit.so    revoke
session    required    pam_limits.so
session    [success=1 default=ignore]    pam_succeed_if.so    service in crond quiet use_uid
session    required    pam_unix.so
[/I]

And this is what the /etc/pam.d/common-password looks like:

[I]password    requisite    pam_cracklib.so retry=3 difok=3 dcredit=1 ucredit=1 lcredit=0 ocredit=1
password    [success=1 default=ignore]    pam_unix.so obscure use_authtok try_first_pass sha512 minlen=14 remember=24
password    requisite    pam_deny.so
password    required    pam_permit.so
password    optional    pam_gnome_keyring.s[/I]o 

I have not yet started to configure anything for the forced reset at first login, I have however put in here what I think should force the user to reset using 14 characters and 1 upper case, 1 number and 1 special character. 

When I reset a user account I can enter any length including an 8 digit password and it will take it.

How do I fix that?  :confused:

---

