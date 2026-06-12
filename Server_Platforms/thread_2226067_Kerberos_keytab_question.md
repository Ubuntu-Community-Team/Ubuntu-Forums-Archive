---
title: "Kerberos keytab question"
date: 2014-05-25
forum: Server Platforms
---

### Post by richard51 on 2014-05-25
I have setup up my Ubuntu 14.04 LTS server for **S**ingle**S**ign**O**n using Kerberos, LDAP and GSSAPI. I now wish to implement NFS, but I am not sure what keytab file I am supposed to add the NFS principal to.

Kerberos, LDAP and NFS are all on the same server, but OpenLDAP references the **/etc/ldap/ldap.keytab** file and not the system **/etc/krb5.keytab** file.

My question is this: Do I add the NFS principal to the **ldap.keytab**, the **krb5.keytab**,or **both**?

---

### Post by richard51 on 2014-05-25
After looking through the system logs, I found these entries:
[B]
unable to obtain root (machine) credentials
do you have a keytab entry for nfs/<your.host>@<YOUR.REALM> in /etc/krb5.keytab?[/B]

So, I added the NFS principal to the **krb5.keytab **file, and the warnings have now gone. I am still not sure if I need to add the NFS principal to the **ldap.keytab** file aswell?

---

