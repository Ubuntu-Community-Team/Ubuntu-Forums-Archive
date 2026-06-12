---
title: "GDM auth via pam_ldap - Please Help!"
date: 2005-10-14
forum: Server Platforms
---

### Post by phill on 2005-10-14
I have a Breezy thin client server set up and I've installed libnss-ldap and libpam-ldap and configured them so I can log in locally, via ssh and run "getent passwd" and they all work for ldap user accounts.

I've tried as hard as I can to get GDM to work (locally and remotely) via pam_ldap.so but it just fails every time.  There must be someone out there who knows how it should look, please help!

```

/etc/pam.d/gdm:

auth     requisite      pam_nologin.so
auth     required       pam_env.so
auth    required       pam_unix.so nullok_secure
auth     sufficient     pam_ldap.so use_first_pass

account  sufficient     pam_ldap.so
account  required       pam_unix_acct.so

@include common-auth
@include common-account

session  sufficient      pam_ldap.so

```

The common-* files look like this:

```

# /etc/pam.d/common-account 
account sufficient      pam_ldap.so
account required        pam_unix.so


# /etc/pam.d/common-auth 
auth    required        pam_env.so
auth    sufficient      pam_unix.so likeauth nullok shadow
auth    sufficient      pam_ldap.so use_first_pass
auth    required        pam_deny.so


# /etc/pam.d/common-password 
password   sufficient   pam_ldap.so use_authtok
password   sufficient   pam_unix.so nullok obscure min=4 max=8 md5
password   required     pam_deny.so


# /etc/pam.d/common-session 
session         sufficient        pam_ldap.so
# session         required        pam_limits.so
session         required        pam_unix.so
# session         required        pam_mkhomedir.so skel=/etc/skel/ umask=0

```

---

### Post by tincanman on 2005-10-15
Hi Phill,

I got ldap authentication going with gdm by having this in my /etc/pam.d/gdm

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password


I have this in my /etc/pam.d/common-auth

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure

Have this in my /etc/pam.d/common-account

account sufficient      pam_ldap.so
account required        pam_unix.so

Have this in my /etc/pam.d/common-session

session         sufficient      pam_ldap.so
session         required        pam_unix.so

And finally this in my /etc/pam.d/common-password

password        sufficient      pam_ldap.so
password        required        pam_unix.so nullok obscure min=4 max=8 md5

---

### Post by claudiob on 2005-10-16
I had to fight with GDM and libpam-ldap and libnss-ldap a lot to make it work (GDM expects the connection with ldap to be on TLS/SSL that is a good thing).

These are the packages you need (you have to enable 'universe' repositories in /etc/apt/sources.list for download):
[LIST]
[*]nscd (this is not mandatory)
[*]libpam-ldap
[*]libnss-ldap
[/LIST]

These is my configuration for all the files necessary to have a working ubuntu desktop with ldap authentication:

**/etc/libnss-ldap.conf**
```
# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
ssl start_tls
ssl on
```
and since I had no server certificates it was necessary to add this line:
```
tls_checkpeer no
```

**/etc/pam.d/gdm**
```
#%PAM-1.0
auth requisite pam_nologin.so
auth required pam_env.so
@include common-auth
@include common-account
session required pam_limits.so
@include common-session
@include common-password
```

**/etc/pam.d/sudo**
```
@include common-auth
@include common-account
```

**/etc/pam.d/common-auth** - authentication settings common to all services
```
auth sufficient pam_ldap.so nullok_secure
auth required pam_unix.so use_first_pass
```
...this way you don't be asked two times for the password!

**/etc/pam.d/common-account** - authorization settings common to all services
```
account sufficient pam_ldap.so
account required pam_unix.so
```

**/etc/pam.d/common-password** - password-related modules common to all services
```
password sufficient pam_ldap.so
password required pam_unix.so nullok obscure min=4 max=8 md5
```

**/etc/pam.d/common-session** - session-related modules common to all services
```
session sufficient pam_ldap.so
session required pam_unix.so
```

**/etc/nsswitch.conf**
```
passwd: files ldap
group: files ldap
shadow: files ldap
```
...this way the system check for user/password match on local files first, if it fails will check on ldap (this is useful if you have for example a local user 'administrator' on the desktop client that do not have to be confused with the 'administrator' user on the ldap server). If you want to check ldap first just change the order of the words (ldap files).

**! UPDATED** on Oct 20 2005

---

### Post by phill on 2005-10-17
Thanks for your help, you've got me almost there!

I've set my files to be exactly as yoursare above Claudiob (except I've dropped the nullok and secure from the ldap entry in common-auth because gdm complains that they are illegal options in the syslog).

I can still log in via ssh or to a tty and I can also get a rejection (incorrect username or password) from gdm when logging in with a valid LDAP username but the wrong password.  When I enter the correct password through gdm I get "Cannot set your group" displayed (in white text under the login box) with an ugly grey popup box saying "Authentication failed".  The syslog the entry is:
```
gdm[19196]: Cannot set user group for andyr
```

Andyr is a valid user on the ldap server with GID 107 (lpadmin).  I tried giving him a group 255 which only exists on the ldap server but I get the same message.  Getent passwd and group both work fine and retrieve all the info from the LDAP server.

Can anyone get me passed this final hurdle please...?

---

### Post by claudiob on 2005-10-17
Phill try to put the user in a group GID > 1000. I think that is the only difference between my setup and yours.

Regarding the 'nullok secure' I also have complains in syslog:
Oct 17 15:52:19 localhost gdm[7450]: illegal option nullok
Oct 17 15:52:19 localhost gdm[7450]: illegal option secure

Before my setting was: nullok_secure and syslog was complaining the same.

My actual /etc/pam.d/common-auth:
```
auth sufficient pam_ldap.so nullok secure
auth required pam_unix.so use_first_pass
```

Does anybody know the correct parameter for common-auth?

---

### Post by phill on 2005-10-17
Thanks for the suggestion about the gid, I tried it 
```

uid=1301(andyregent) gid=1301(andyregent) groups=1301(andyregent)

```
 but didn't get anywhere :-(

Then, at great trouble, I reboot the server and it lets me in!!!  I get some errors about the .dmrc file and my xsession lasted only a few seconds but at least I'm in!

It's a bit annoying that you have to reboot, I've tried restarting GDM and several other services but nothing extra happened until the machine went through a full restart.  Thanks!!

---

### Post by sund on 2005-10-19
I tried the configurations above and cannot login!
Some questions:
-Why use "nullok secure"? the original file uses "nullok_secure"
-Why edit the sudo file? It includes de auth file, "@include common-auth". The password is being asked twice when uses the sudo command.

---

### Post by sund on 2005-10-19
I tried to configure with the Phill's configuration:

You should not edit the /etc/libnss-ldap.conf file if your server does not use tls.
It depends of your server, not the client.
I tried to put it in my network and doesn't work.

I dont need to edit /etc/pam.d/sudo file.

I cant put "nullock secure" in common-auth. I have to put "nullock_secure"

And you should think about the server's crypt! My server uses md5, so my password should have "(...) pam_ldap.so md5"

---

### Post by claudiob on 2005-10-20
The configuration I posted is working for me but Sund is right and I corrected the above with 'nullok_secure'  in common-auth (and updated also the post above).
Also found this reagrding this feature:
[http://archives.neohapsis.com/archives/pam-list/2005-08/0014.html](http://archives.neohapsis.com/archives/pam-list/2005-08/0014.html)

I also removed the first two lines in /etc/pam.d/sudo because we include them. The corrected configuration still works for me.

> You should not edit the /etc/libnss-ldap.conf file if your server does not use tls.
It depends of your server, not the client.
I tried to put it in my network and doesn't work.

I think that is where the problem originated for me... is it possible to have GDM authenticate on ldap without tls on ldap server? I think not.

---

### Post by sund on 2005-10-20
Hello claudio!
This problem I have with tls is interesting... I dont put it on the client, when I put my client cant login!
My server configuration looks like [ServidorLdap](http://colab.interlegis.gov.br/wiki/ConfigurandoUmServidorLdap)
Its portuguese... but look the slapd.conf
Can you show your server configuration?

---

### Post by zeg on 2005-10-22
just to confuse everybody...

if you use kdm instead of gdm the user can login in X and but the error codes are still available in the logs.

---

