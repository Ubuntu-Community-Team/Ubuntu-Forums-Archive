---
title: "Force PAM to create user home folder if it already not exists"
date: 2011-11-10
forum: Security
---

### Post by Lorens on 2011-11-10
Hi all!

I've been trying to configure gdm to log by a RADIUS server.
I'm done with the auth. But the logging it's only working if the user has already a local home folder. So I'm trying to configure pam_mkhomedir.so in order to create the user home folder on the fly. The problem is that it's not working...

My /etc/pam.d/gdm file:

#%PAM-1.0
auth    sufficient    pam_radius_auth.so
auth    requisite       pam_nologin.so
#auth    sufficient        pam_env.so readenv=1
#auth    sufficient        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient    pam_succeed_if.so
#auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
account    sufficient    pam_radius_auth.so
@include common-account
#session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
#session required        pam_limits.so
session sufficient    pam_mkhomedir.so skel=/home/formacio umask=0
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password


Thanks

---

### Post by Lorens on 2011-11-18
I'm posting the configuration files:

############# /etc/pam.d/common-account ####################

account sufficient pam_radius_auth.so
session required pam_mkhomedir.so

account [success=1 new_authtok_reqd=done default=ignore] pam_unix.so
account requisite pam_deny.so
account required pam_permit.so


############# /etc/pam.d/common-auth #######################

auth [success=1 default=ignore] pam_unix.so nullok_secure
auth requisite pam_deny.so
auth required pam_permit.so


############# /etc/pam.d/common-session #######################

session [default=1] pam_permit.so
session requisite pam_deny.so
session required pam_permit.so
session required pam_mkhomedir.so
session required pam_unix.so
session optional pam_ck_connector.so nox11


############# /etc/pam.d/gdm #######################

auth sufficient pam_radius_auth.so debug
auth requisite pam_nologin.so
auth sufficient pam_env.so readenv=1
auth sufficient pam_env.so readenv=1 envfile=/etc/default/locale
auth sufficient pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth optional pam_gnome_keyring.so
account sufficient pam_radius_auth.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required pam_limits.so
session sufficient pam_mkhomedir.so skel=/home/formacio umask=0022
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional pam_gnome_keyring.so auto_start
@include common-password


############# /etc/pam.d/login #######################

auth required pam_securetty.so
auth requisite pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required pam_env.so readenv=1
session required pam_env.so readenv=1 envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

auth optional pam_group.so

session required pam_limits.so
session optional pam_lastlog.so
session optional pam_motd.so
session optional pam_mail.so standard

# Standard Un*x account and session
@include common-account
@include common-session
@include common-password

session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open

##################################################  ##########

I hope this will help.

---

### Post by Lorens on 2011-11-22
This way it's not working.

I already notice that the real problem is that accounting/session is  failing because the radius user has not an entry at `/etc/passwd`

I'm currently trying to do adduser by `libpam_script.so` plugin. Maybe it's the solution [IMG]http://static.linuxquestions.org/questions/images/smilies/wink.gif[/IMG]

---

### Post by Lorens on 2011-11-29
Finally I have solved the problem by using `pam_script` to execute `adduser` before entering the gdm session.

Thanks all.

---

