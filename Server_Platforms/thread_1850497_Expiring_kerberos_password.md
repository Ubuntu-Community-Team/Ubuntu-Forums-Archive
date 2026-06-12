---
title: "Expiring kerberos password"
date: 2011-09-26
forum: Server Platforms
---

### Post by supremedalek on 2011-09-26
Let's say I have a kerberos password policy saying passwords need to be changed every, say, 90 days. If users log in either through the graphics console or through ssh, is there a way to reminding them of impending doom, i.e. of password expiration date steadily approaching? From what I understand, the KDC sends that information to the client, which has the option of displaying it.

---

### Post by Space_Balls on 2011-10-14
Oneiric warns the user about password expirations. I'm actually trying to get rid of this warning, since we don't use password expiration.

---

### Post by supremedalek on 2011-10-14
That is good to know; I will test that today.

For your own question, you can define the password policy in kerberos. First check the user principal and see if there is a policy associate with it. 

In kadmin, you can also do listpols to see which policies are defined. And then check each of the policies, as in

```
kadmin:  getpol default
Policy: default
Maximum password life: 0
Minimum password life: 0
Minimum password length: 7
Minimum number of password character classes: 2
Number of old keys kept: 5
Reference count: 0
Maximum password failures before lockout: 0
Password failure count reset interval: 0
Password lockout duration: 0
kadmin:
```

Then you can change the policies as needed. I hope this helps you get moving.

---

