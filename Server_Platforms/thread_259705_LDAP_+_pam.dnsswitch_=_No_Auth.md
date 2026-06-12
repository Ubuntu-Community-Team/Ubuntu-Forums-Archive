---
title: "LDAP + pam.d/nsswitch = No Auth?"
date: 2006-09-17
forum: Server Platforms
---

### Post by backu on 2006-09-17
Hello All! 
I'm hoping someone can help me with this little problem I seem to have.

I am currently running Ubuntu Dapper on an x86/750MHz with several things installed. I have installed the OpenLDAP available in the repository, have it running, and am able to access it through phpLDAPadmin just fine.

I also have eGroupWare 1.2 installed with LDAP authentication mechanism, and through setup am able to access parts of the database just fine.

Following a walk-through I found through another post, I installed the libpam-ldap and libnss-ldap and configured them as per the HOWTO. Even after a reboot of the system, I cannot login using an LDAP user, my local account still works fine.

I also cannot get eGroupWare to authenticate either. 

Everything is configured (as far as I can tell) to use the MD5 encryption of the passwords. I am completely ](*,) at this point. Ask for anything, and I shall post it here.

Thank you all in advance.
Backu

---

### Post by bluefrog on 2006-09-18
need to tweak /etc/pam.d/common-*

sry away from my computer and I don't have the exact lines handy.
will try to follow up later on

James

---

### Post by backu on 2006-09-18
common-auth, common-account, common-session, and one other I can't remember. I added the lines into the files that the walk-through stated, but maybe I missed something. Maybe I need to do the stronger encryption steps since the LDAP is running using MD5 passwords... perhaps? The walk-through was [http://help.ubuntu.com/community/openldapserver](http://help.ubuntu.com/community/openldapserver)
and [http://help.ubuntu.com/community/ldapclientauthentication](http://help.ubuntu.com/community/ldapclientauthentication)

---

### Post by backu on 2006-09-18
I updated the LDAP to the latest Stable from OpenLDAP and eGroupWare authenticates just fine, but still no luck through pam.d

---

### Post by backu on 2006-09-20
Okay, I managed to get it to start working with the LDAP authentication, but now I have the problem that it says my account has been disabled by the admnistrator.. am I missing a key in the LDAP?

---

### Post by backu on 2006-09-20
Heh, self-answering, I just have to keep working. Forgot to change passwords in libpam-ldap to MD5 instead of exop. Now if I can just figure out eGroupWare 1.2's schema to get it to work with the naming contexts of the LDAP (ie: Gecos vs name, sn)

---

