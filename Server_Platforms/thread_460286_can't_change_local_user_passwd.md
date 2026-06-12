---
title: "can't change local user passwd"
date: 2007-05-31
forum: Server Platforms
---

### Post by mbradlcu on 2007-05-31
Hi all,
could someone please tell me were I've misconfigured my client ldap scripts (guessing that's the cause of the issue). I've set all the files I'll list back to the stock configuration verified by looking at another machine that 'passwd' works on.
I'm not able to change my local user account password, here's what happens:
> 
daturan@appserv2:~$ passwd 
Changing password for daturan
(current) UNIX password: 
Enter login(LDAP) password: 
Password change aborted
Changing password for daturan
(current) UNIX password: 
passwd: Authentication failure
passwd: password unchanged

Authentication works for both ldap and local users, note I don't need/want to be able to change ldap users passwords locally.

common-auth:
> 
auth required pam_nologin.so
auth sufficient pam_ldap.so
auth sufficient pam_unix.so shadow use_first_pass
auth required pam_deny.so

common-account
> 
account sufficient pam_unix.so
account sufficient pam_ldap.so
account required pam_deny.so

common-session
> 
session required        pam_unix.so
session optional        pam_foreground.so
session optional pam_ldap.so

common-passwd
> 
password   required   pam_unix.so nullok obscure min=4 max=8 md5
password required pam_cracklib.so
password sufficient pam_ldap.so
password sufficient pam_unix.so

nsswitch.conf
> 
passwd:         files ldap
group:          files ldap
shadow:         files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


thanks in advance!

---

### Post by mokomull on 2008-01-06
My /etc/pam.d/common-password looks like:
> password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5 


I have been having your issues until today; now I have passwd working to change local passwords when the user account isn't known to ldap.  _MY_ problem was that I had tossed use_first_pass around willy-nilly in my pam configs, so it's slightly different than yours.  Try this and see.

---

