---
title: "Kerberos &gt;&gt;&gt; kinit tool, where is it?"
date: 2006-04-05
forum: Server Platforms
---

### Post by kozmo on 2006-04-05
Using Breezy, I installed the krb5-user package.

I'm trying to join Ubuntu to our Active Directory domain and when I run the following command:

**kinit [email]domain_user_name@domain_name.com[/email]**

I get command not found.

What package do I need to install for the kinit tool?

---

### Post by Glut on 2006-04-07
[QUOTE=kozmo]Using Breezy, I installed the krb5-user package.

I'm trying to join Ubuntu to our Active Directory domain and when I run the following command:

**kinit [email]domain_user_name@domain_name.com[/email]**

I get command not found.

What package do I need to install for the kinit tool?[/QUOTE]
krb5-clients

---

### Post by kozmo on 2006-04-07
Thanks for the reply.

I believe krb5-client is part of the krb5-user package.

Once I re-install krb5-user it worked find.

---

