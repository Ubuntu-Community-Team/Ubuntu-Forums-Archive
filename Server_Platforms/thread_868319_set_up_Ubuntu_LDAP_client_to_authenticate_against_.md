---
title: "set up Ubuntu LDAP client to authenticate against OS X ldap server"
date: 2008-07-23
forum: Server Platforms
---

### Post by bowmasters on 2008-07-23
I originally posted this here by mistake but moved it once I realized that this forum is for server releases (my installation is not one of the server releases)

However, after a week with no responses in the general and the networking forums, I've decided to repost it here with the hopes that you server gurus might know more about my problem or can direct me to a good place to get help. (the networking forum seems mostly involved in diagnosing simpler network config issues)

Here is the original message:

Hello all,

I am trying to configure the ldap client on one of my Ubuntu(8.04.1) Machines to authenticate against an LDAP database hosted on an OS X(10.4.11) server.

I installed the following packages per these instructions: libpam-ldap libnss-ldap nss-updatedb libnss-db

then I proceeded to manually edit parts of the config files where applicable (eg. 'host' in /etc/ldap.conf)

after I finished configuring things, I ran "getent passwd" to see if the configuration worked. The LDAP users failed to show up, so something is clearly amiss.

So, next I try to modify the configuration files per these instructions.

running "getent passwd" under this new configuration returns the users in the ldap database. "su" to one of those users also works. However, if I try to ssh into that machine using an ldap user, it does not work. Perhaps this is the "authenticating (partially) successfully" that the walkthrough was referring to?

In any case, I decided to try a third configuration using mostly the same parameters I had on a SUSE 11 box, (since I am able to ssh onto that one successfully using ldap users.) This config didn't fix the problem on ubuntu.

The last (and current standing) config I tried on this Ubuntu box was obtained using the command "auth-client-config" (which I just recently found out about). This command made it quicker and easier to configure, but it changed little and yielded the same result (no ssh login)

Just as a note, in between trying out these different configs, as a precautionary step, I uninstalled and reinstalled the ldap packages, being sure to purge the config files so that I started with a clean setup each time.

If anyone can help me figure out what is going wrong, I'd greatly appreciate it. If there is any additional specific information I can provide to help you help me, let me know and I will include it. 

P.S. I am fairly new to linux sys admin-ing, so please forgive my noobishness if it shows

---

### Post by pdwerryhouse on 2008-07-24
If you haven't already done it, there's a bunch of pam files you'll need to edit, including /etc/pam_ldap.conf and files under /etc/pam.d/  (eg, common-auth, common-account, etc).

This is the contents of my common-auth file:

```
auth [success=1 default=ignore] pam_unix.so
auth required pam_ldap.so use_first_pass
auth required pam_permit.so
```

---

### Post by bowmasters on 2008-07-24
thanks for the reply

I have modified the following files in /etc/pam.d:

common-account
common-auth
common-password
common-session

however, the auth-client-config automatically changed settings when I ran it. Here is what each file looks like:

common-account
```
account    sufficient   pam_ldap.so
account    required     pam_unix.so
```

common-auth
```
auth       sufficient   pam_ldap.so
auth       required     pam_unix.so nullok_secure use_first_pass
```

common-password
```
password   sufficient   pam_ldap.so md5
password   required     pam_unix.so nullok obscure min=4 max=8 md5
password optional pam_smbpass.so nullok use_authtok try_first_pass miss
```

common-session
```
session    required     pam_unix.so
session    required     pam_mkhomedir.so skel=/etc/skel/
session    optional     pam_ldap.so
session    optional     pam_foreground.so

```

I don't have the /etc/pam_ldap.conf
what should go into it?

---

### Post by pdwerryhouse on 2008-07-24
This is in mine:

```
host 127.0.0.1
base dc=mydc,dc=org
ldap_version 3
binddn cn=proxyuser,dc=mydc,dc=org
bindpw mypasswd
rootbinddn cn=admin,dc=mydc,dc=org
pam_password crypt
```

You should also have a file called libnss_ldap.conf, with similar contents. I'm surprised that the files aren't on your system, I'd have though they'd be configured when you installed other ldap packages (libnss-ldap and libpam-ldap).

Unless Ubuntu has switched to a file called "/etc/ldap.conf" like Redhat and Fedora use...

---

### Post by bowmasters on 2008-07-28
OK,  I  see  the  /etc/ldap.conf  file  and  it  has  most  of  the  things  you mentioned.

It also looks like it contains what would've gone into the libnss_ldap.conf and pam_ldap.conf files.

I believe that this was configured automatically when I ran auth-client-config

in any case, I still can't get SSH to work with the directory users and the files seem to be properly configured. What now?

---

### Post by pdwerryhouse on 2008-07-31
Not really sure what to say at this point; might be worth running tcpdump or wireshark on the network to see what sort of ldap traffic it is sending when you try to log in...

---

