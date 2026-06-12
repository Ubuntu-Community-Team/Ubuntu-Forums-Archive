---
title: "AppArmor trouble"
date: 2013-05-18
forum: Security
---

### Post by ranger1021994 on 2013-05-18
When i run aa-status / apparmor_status , I get this :
> apparmor module is loaded.
You do not have enough privilege to read the profile set.

I have installed apparmor-profiles and apparmor-utils
I have pf kernel 3.9.2 installed.

Anyone has any workarounds ?
I tried downloading apparmor 2.8 source code but got strange errors while compiling it
I have attached the error file below :
[ATTACH]242745[/ATTACH]

---

### Post by cariboo on 2013-05-19
What are the the permissions on the apparmor profiles? on my systems the permissions are 644, which means I can read them as a normal user, but edit them. If you need to edit the profiles, press Alt-F2 and type:

```
gksu gedit <profile_name>
```

where profile_name = for example lightdm-guest-session

---

