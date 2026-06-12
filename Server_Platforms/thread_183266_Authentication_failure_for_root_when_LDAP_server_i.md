---
title: "Authentication failure for root when LDAP server is down."
date: 2006-05-27
forum: Server Platforms
---

### Post by acchopra on 2006-05-27
Hello, I'm having some problems configuring PAM in Ubuntu to look in local files for root authentication before attempting to contact ldap for authentication/authorization.

**Background:**
First I got authentication using LDAP working correctly for root and other users. Then, I stopped LDAP server to understand the ramifications. I found that when root attempts to login, the following occurs: 

```

username@machname:/etc$ su - 
Password:
su: Authentication failure
Sorry.

```

To eliminate the obvious, the entered password is correct.

The following can be found in the auth.log file upon performing the above test:
```

May 28 02:09:25 localhost su[22327]: pam_ldap: ldap_simple_bind Can't contact LDAP server
May 28 02:09:25 localhost su[22327]: (pam_unix) authentication failure; logname=username uid=1000 euid=0 tty=pts/5 ruser=username rhost=  user=root
May 28 02:09:27 localhost su[22327]: pam_authenticate: Authentication failure
May 28 02:09:27 localhost su[22327]: - pts/5 username:root

```


Following is the config:
**_/etc/nsswitch.conf:_**

```

passwd:     files ldap
group:      files ldap
shadow:     files ldap
.
.
.

```

**_/etc/pam.d/common-auth:_**
```

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so use_first_pass

```

**_/etc/pam.d/common-account:_**
```

account sufficent       pam_ldap.so
account required        pam_unix.so

```

**_/etc/pam.d/common-password:_**
```

password   sufficient pam_ldap.so
password   required   pam_unix.so try_first_pass nullok obscure min=4 max=8 md5

```

pam_ldap.conf and libnss-ldap.conf are configured properly because when the LDAP server is up, everything works fine. 

Has anyone had the same experience I'm having? If so, how were you able to fix the problem?

TIA!

Aakash

---

### Post by acchopra on 2006-05-30
um... bump 

](*,) 

Incidentally, there was a [bug]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=55193") filed against older releases of the authconfig tool included with redhat for not configuring the nsswitch and pam.d files correctly - resulting in the same problems I'm having with UBUNTU. I tried using some of the workarouds listed in the RH bug but some of the relevant PAM modules do not exist for Ubnutu (or at least I can not apt-get them). I have tried configuring authentication/authorization against LDAP in FC5 with the authconfig tool and it works like a charm - including the use case where communication with the LDAP server is down. 

Does any one have any suggestions to get things working properly in Ubuntu?

Thanks again for any help

---

### Post by Souseke on 2006-06-08
Does the root account exist locally and it is active. If i remember right, root is disable on default.

---

