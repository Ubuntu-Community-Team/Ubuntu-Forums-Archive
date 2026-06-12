---
title: "Enabling a new profile in AppArmor"
date: 2011-06-18
forum: Security
---

### Post by desire.linux on 2011-06-18
When I enable a new AppArmor profile that is not in the kernel, I've used this command:

```
apparmor_parser -r /path/to/profile
```But when I recently read the manual for AppArmor, it says to use this command for new profiles:

```
apparmor_parser -a /path/to/profile
```Have I done something wrong by using -r instead of -a?

---

### Post by Dave_L on 2011-06-18
If there were no error messages, and the new profile shows up as enabled (sudo service apparmor status), then it should be ok.

It seems reasonable that -r (replace) would perform the -a (add) action if the profile is new, even though the man page doesn't explicitly state this.

>        -a, --add
           Insert the AppArmor definitions given into the kernel. This is the
           default action. This gives an error message if a AppArmor
           definition by the same name already exists in the kernel, or if the
           parser doesn't understand its input. It reports when an addition
           succeeded.

       -r, --replace
           This flag is required if an AppArmor definition by the same name
           already exists in the kernel; used to replace the definition
           already in the kernel with the definition given on standard input.

---

