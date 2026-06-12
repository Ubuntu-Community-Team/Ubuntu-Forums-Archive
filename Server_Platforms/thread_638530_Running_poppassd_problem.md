---
title: "Running poppassd problem"
date: 2007-12-12
forum: Server Platforms
---

### Post by satimis on 2007-12-12
Hi folks,


Ubuntu 7.04 server amd64
squirrelmail 1.4.11
poppassd 1.8.5


On running;
$ poppassd
200 poppassd v1.8.5 hello, who are you?
user satimis
200 Your password please.
pass satpass
200 Your new password please.
newpass satnewpass
500 Server error, password not changed


In another case;
$ poppassd
200 poppassd v1.8.5 hello, who are you?
user userA     
200 Your password please.
pass userApass
500 Old password is incorrect.


poppassd was installed on repo with;
$ sudo apt-get install poppassd


$ cat /etc/pam.d/poppassd 
@include common-auth
@include common-password


$ locate common-auth
/etc/pam.d/common-auth
/usr/share/pam/common-auth
/usr/share/pam/common-auth.md5sums


$ locate common-password
/etc/pam.d/common-password
/usr/share/pam/common-password
/usr/share/pam/common-password.md5sums


$ cat /etc/pam.d/common-auth 
auth    required        pam_unix.so nullok_secure


$ cat /usr/share/pam/common-auth
auth    required        pam_unix.so nullok_secure


$ cat /etc/pam.d/common-password 
password   required   pam_unix.so nullok obscure min=4 max=8 md5


$ cat /usr/share/pam/common-password
password   required   pam_unix.so nullok obscure min=4 max=8 md5


$ locate pam_unix.so
/lib/security/pam_unix.so
/usr/lib/vmware/lib/libpam.so.0/security/pam_unix.so
/usr/local/src/vmware-server-distrib-1.0.4-56528/lib/lib/libpam.so.0/security/pam_unix.so

pam_unix.so found


Please advise how to fix the problem.   TIA


B.R.
satimis

---

### Post by HermanAB on 2007-12-12
Hmm, poppassd has to run as root.  Are you?

Cheers,

H.

---

### Post by MJN on 2007-12-12
See if /var/log/auth.log gives any hints.

Mathew

P.S. When attempting to change the password for userA are you sure you got the old password correct?

---

### Post by satimis on 2007-12-12
> **HermanAB said:**
> Hmm, poppassd has to run as root.  Are you?

Thanks for your advice.


root can change users' password with poppassd but users' can't.


On SquirrelMail I can't give root password to all users to change their password.  Now I can't make users changing their password direct on SM.  They can change their password via Usermin.

$ ls -l /usr/sbin/poppassd ```

-rwxr-xr-x 1 root root 10968 2006-12-17 18:20 /usr/sbin/poppassd

```
changing the permission as 775 ?  Or any other solution?  TIA


Besides if I prefer only allowing some users changing password NOT ALL of them, what will be the solution?  Creating a new group for password change?


B.R.
satimis

---

### Post by satimis on 2007-12-12
> **MJN said:**
> See if /var/log/auth.log gives any hints.

$ tail /var/log/auth.log```

.......
Dec 13 10:06:05 mail poppassd[5409]: (pam_unix) authentication failure; logname=
satimis uid=1000 euid=1000 tty= ruser= rhost=  user=satimis

```


> 
P.S. When attempting to change the password for userA are you sure you got the old password correct?
Yes, absolutely.


B.R.
satimis

---

