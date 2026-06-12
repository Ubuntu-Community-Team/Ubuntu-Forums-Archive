---
title: "pam_krb5, Preauthentication failed"
date: 2005-09-02
forum: The Cafe
---

### Post by JJdaKing on 2005-09-02
Hello,
i don`t know if i`m in the right section but i`m really desperate :(

Its about Kerberos :)
I have the user in "klist", and "kinit" works, but when i try to log him in 
i get this error :
pam_krb5: pam_sm_authenticate(ssh cen30148): krb5_get_init_creds_password(): Preauthentication failed

Please help !

---

### Post by zielgruppe on 2005-09-15
capitalize the domain name

kinit [email]user@SOME.DOMAIN.COM[/email]

worked for me ;)

---

### Post by nocturn on 2005-09-16
Just guessing, but did you create a Kerberos account for your machine?  Did you add it to your local keytab?

I'm using pam_krb5 from universe against an MIT server (also on Ubuntu)

---

