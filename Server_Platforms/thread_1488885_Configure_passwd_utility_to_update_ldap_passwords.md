---
title: "Configure passwd utility to update ldap passwords"
date: 2010-05-20
forum: Server Platforms
---

### Post by bjorgein on 2010-05-20
I recently set up a ldap server for user authentication and I want to be able to configure the passwd utlity to automatically update the password for the local account AND on the ldap server. How would I go about this? 

Thanks
Chris

---

### Post by cdenley on 2010-05-20
I don't think /usr/bin/passwd can be made to change passwords on LDAP.

---

### Post by bjorgein on 2010-05-20
Hi

Is there anyway to then disable it or some how redirect people to another utility when they use the passwd utility then? 

thanks
chris

---

### Post by cdenley on 2010-05-20
> **bjorgein said:**
> Is there anyway to then disable it or some how redirect people to another utility when they use the passwd utility then?

Create a new script at /usr/local/bin/passwd.

---

### Post by bjorgein on 2010-05-20
Hmmm.

Essentially I just want the client to be able to change their password without having to come to me or another sys admin to change their password for them on the server. How can I do that?

---

### Post by cdenley on 2010-05-20
Sorry, I'm not very familiar with LDAP.

---

### Post by bjorgein on 2010-05-20
Thanks anyways, LDAP + PAM is a very complicated process these days with so many different guides out there. Hopefully someone else will know.

---

### Post by Zeosa on 2010-05-20
I just removed /usr/bin/passwd (renamed actually) and linked /usr/bin/passwd to /usr/sbin/smbldap-passwd (from smbldap-tools) to update ldap.

just make sure your users have self-write privs to the attrs that need updated.

This doesn't give you a way to update the 'local' account ie /etc/passwd though, but it would be pretty trivial to create a shell script which calls smbldap-passwd then passwd afterward. (though the user would be going through both programs, typing their passwords a few times.

---

