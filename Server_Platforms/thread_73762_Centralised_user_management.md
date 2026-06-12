---
title: "Centralised user management"
date: 2005-10-10
forum: Server Platforms
---

### Post by nverhaar on 2005-10-10
Hey all, we have a vast mixture of different operating systems being run here at work, and would love to centralise our user management as best as possible. Currently we're creating all user accounts via Active Directory on Windows Server 2003, however all email is hosted on Linux, therefore all mail accounts need to be created on the linux servers as well.

I have been toying with Ubuntu and have now got it to authenticate user accounts via Active Directory, and it works GREAT!! I am able to login to the linux box with user accounts created within Active Directory and can use them via SSH, FTP, POP/IMAP, and even Samba File/Print sharing.

I am just wondering what would be the best option for configuring email aliases. Are we able to harvest the email addresses from Active Directory, or would we be better off to maintain a seperate alias database within Postfix.

Any suggestions would be greatly appreciated!!

---

### Post by Glut on 2005-10-10
We grab the information from windows using pam-ldap, on top of that we have a seperate database for 'other' email aliases. It may work for you.

---

### Post by nverhaar on 2005-10-10
I followed the Ubuntu guide on these forums to get the machine authenticating with the Windows domain and its working great.

When you say you have a seperate database for other email addresses, do you mean just the regular postfix aliases table, or do you mean something more along the lines of an SQL database or something?

Im trying to centralise user management as best as possible, and im trying to get a better understanding of how other people are achieving this.

---

### Post by Glut on 2005-10-10
The system uses the basic usernames as the base email address, then a 'standard' sendmail aliases database. In your scenario, that would most likely be an aliases table. It depends on how detailed it needs to be. In order to cut down the amount of maintanence that we need to do, we use a small amount of aliases.

---

### Post by nverhaar on 2005-10-11
Oh yeah, thats just how I imagined our system to be. Maintain all user accounts via Active Directory so all accounts need to only be created/modified in one instance, then any required mail aliases be managed on the relevent mail server (Ubuntu server running Postfix).

Previously we had to create user accounts in Active Directory, and then again for each different linux server for mail/web, proxy, file/print, etc, which can be a nightmare to maintain. This should simplify things immensely, and make my life MUCH easier.

I just have one question now. If I setup an Ubuntu server with an account name that already exists in the domain, which account will then take priority, the local account or the domain account? Would it be wise to remove the local account and have ONLY domain accounts available.

Also what happens if the Ubuntu server is unable to communicate with the domain? I guess if I remove all local accounts I could potentially lock myself out of the machine should it be unable to communicate with the domain, right?

---

### Post by Glut on 2005-10-11
[QUOTE=nverhaar]I just have one question now. If I setup an Ubuntu server with an account name that already exists in the domain, which account will then take priority, the local account or the domain account? Would it be wise to remove the local account and have ONLY domain accounts available.
[/QUOTE]
If you're using pam (as I assume that you are) then it's defined by pam. In your common-auth file (or service file if you have a completely different version for each service) you will have something like:
auth sufficient authtype1 (say pam_krb5)
auth required authtype2 (say pam_unix)

This will look for a password using krb5 first, then if that fails use normal unix authentication. If the authtypes were reversed, priority would reverse, with the unix authentication taking priority.
The same is true for account.
> 
Also what happens if the Ubuntu server is unable to communicate with the domain? I guess if I remove all local accounts I could potentially lock myself out of the machine should it be unable to communicate with the domain, right?
In the example above, if unable to contact the kerberos server, then the server will try to use its unix (passwd/shadow) login. If you have a passwd/shadow defined in here then the login will succeed. What I therefore recommend is that you create shadow/passwd entries for administrators and not for normal users.
Then, if the domain is not contactable you will still be able to log into those servers. The question remains, though, if your domain is not functioning, don't you have better things to do than check your email?

---

### Post by batou on 2006-06-27
Hi there,

i'm resuming this old post to ask help about pam configuration, i would like to authenticate users against a windows backup domain controller, and if a matching linux user doesn't exists, allow him anyway (do i have to create the user? mkhomedir does suffice?)

when i try to log in as a domain user i get unknown id.


krb5/kinit is working.

thank you in advance :-)


brutal grep of pam.d content:

common-account-# and should contain a list of the authorization modules that define
common-account-# the central access policy for use on the system.  The default is to
common-account-# only deny service to users whose accounts are expired in /etc/shadow.
common-account-#
common-account:account sufficient  pam_krb5.so ignore_root
common-account-account    required  pam_unix.so
--
common-auth-# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
common-auth-# traditional Unix authentication mechanisms.
common-auth-#
common-auth-auth    required        pam_env.so
common-auth:auth    sufficient      pam_krb5.so ignore_root try_first_pass
common-auth-auth    sufficient    pam_unix.so likeauth nullok_secure
common-auth-auth    required        pam_deny.so
--
common-krb5:#auth sufficient /lib/security/pam_krb5.so use_first_pass
common-krb5-
--
common-password-# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
common-password-# login.defs. Also the "min" and "max" options enforce the length of the
common-password-# new password.
common-password-
common-password:password  sufficient  pam_krb5.so ignore_root use_authok
common-password-password  sufficient  pam_unix.so nullok obscure min=4 max=8 md5 use_authok
common-password-password required pam_deny.so
common-password-
common-password-# Alternate strength checking for password. Note that this
--
common-session-#
common-session-#session    required    pam_unix.so
common-session-session    optional    pam_foreground.so
common-session-session  required  pam_limits.so
common-session:session  sufficient  pam_krb5.so ignore_root
common-session-session  required  pam_unix.so
common-session-session  optional pam_mkhomedir.so skel=/etc/skel/ umask=0022
common-session-
--
gdm-@include common-account
gdm-session    required    pam_limits.so
gdm-@include common-session
gdm-@include common-password
gdm:@include common-krb5
gdm-
--
login-# also removes the user's mail spool file.
login-# See comments in /etc/login.defs
login-session    optional   pam_mail.so standard
login-@include common-password
login:@include common-krb5
login-

---

### Post by Glut on 2006-06-27
[QUOTE=batou]Hi there,

i'm resuming this old post to ask help about pam configuration, i would like to authenticate users against a windows backup domain controller, and if a matching linux user doesn't exists, allow him anyway (do i have to create the user? mkhomedir does suffice?)
[/quote]
Sounds like a whole other topic, but anywho

> 
when i try to log in as a domain user i get unknown id.

This is generally a fault in your common-account setup...

> 
krb5/kinit is working.

common-account-# and should contain a list of the authorization modules that define
common-account-# the central access policy for use on the system.  The default is to
common-account-# only deny service to users whose accounts are expired in /etc/shadow.
common-account-#
common-account:account sufficient  pam_krb5.so ignore_root
common-account-account    required  pam_unix.so

Kerberos is not used for account lookup, which is for discovering UID, etc. linking into AD you will need to use pam_ldap. So your common account should be:
```
[COLOR="Green"]
account sufficient pam_ldap.so
account required pam_unix.so
[/color]
```

> 
common-auth-# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
common-auth-# traditional Unix authentication mechanisms.
common-auth-#
common-auth-auth    required        pam_env.so
common-auth:auth    sufficient      pam_krb5.so ignore_root try_first_pass
common-auth-auth    sufficient    pam_unix.so likeauth nullok_secure
common-auth-auth    required        pam_deny.so

Errgh! Environment should not be handled in auth. Kerberos has no first_pass to try (it's the first authentication mechanism)  
Let's simplify:
```
[COLOR="Green"]
# I like debug because login issues can be a pain to debug...
auth sufficient pam_krb5.so ignore_root debug 
auth required pam_unix.so try_first_pass
# I don't like nullok, as pam_unix is required, deny becomes unnecessary, also my manual indicates likeauth is an invalid argument to this module
[/color]
```

> 
common-krb5:#auth sufficient /lib/security/pam_krb5.so use_first_pass
common-krb5-

Common-krb5 is unnecessary, delete.

> 
common-password:password  sufficient  pam_krb5.so ignore_root use_authok
common-password-password  sufficient  pam_unix.so nullok obscure min=4 max=8 md5 use_authok
common-password-password required pam_deny.so
common-password-
common-password-# Alternate strength checking for password. Note that this

looks ok, I've not had much success with getting pam to change windows passwords...

> 
common-session-session    optional    pam_foreground.so
common-session-session  required  pam_limits.so
common-session:session  sufficient  pam_krb5.so ignore_root
common-session-session  required  pam_unix.so
common-session-session  optional pam_mkhomedir.so skel=/etc/skel/ umask=0022

You wont get anywhere including krb5 here:
```
[COLOR="Green"]
session optional pam_foreground.so
session required pam_limits.so
session optional pam_mkhomedir.so skel=/etc/skel
session required pam_unix.so
[/color]
```

> 
gdm-@include common-account
gdm-session    required    pam_limits.so
gdm-@include common-session
gdm-@include common-password
gdm:@include common-krb5

you don't need pam_limits or common-krb5 here. 
> 
login-# also removes the user's mail spool file.
login-# See comments in /etc/login.defs
login-session    optional   pam_mail.so standard
login-@include common-password
login:@include common-krb5

ditto here

There is a big gottcha in using windows. If the user doesn't have a local account then windows must be able to supply the information with the AD LDAP. Microsoft distributes Services For Unix which adds the required information into AD. Once this is done and you've updated the user data you must make sure that there are no conflicts of uid. That is bad. Finally, install libnss ldap and change the switch.conf file to use ldap so that linux can use windows information about uids.
Finally mkhomedir is not the be all and end all. If the process doing login doesn't use pam then the directory wont be created. If the process is not run as root then the directory will not be created. If the user has never authenticated on the linux box then the directory wont exist. Autodir is an option.

---

### Post by batou on 2006-06-28
[quote=Glut]There is a big gottcha in using windows.[/quote]

thanks a lot for the very detailed reply, for three reasons: it is a true reply for the question (very informative), it is a reply for the questions i should have asked before ;-), and makes me understand that both i have to study harder and that what i was trying to accomplish is not really suited for what i really wanted to do (especially given that it requires me interaction with the local sysadmin which is a very nice and collaborative person but it's kept in an "chadmin jail" ;-) by the extremely strict corporate rules.

thanks again

---

