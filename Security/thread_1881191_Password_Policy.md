---
title: "Password Policy"
date: 2011-11-15
forum: Security
---

### Post by temporizer on 2011-11-15
Hey everyone,
I'm playing around with ubuntu 11.04 server, and I want to know how to make it so i can use the same password (or a similar password) again when changing the password.

e.g.: if my password is 1234567 and i want to change it to 12345678 ubuntu says that the passwords are too similar and refuses to change it...

how do i change that?

---

### Post by tubbygweilo on 2011-11-15
It is often held to be bad practice to recycle passwords or parts of passwords and is discouraged by most users. If you are sure in your own mind as to why you think it safe to do such a thing then I expect someone may suggest a way for you to do it.

---

### Post by temporizer on 2011-11-15
I understand that, and thank you for pointing that out. However, I am not making this a public server, as there are only 2 users, me and my girlfriend. I am only looking to advance my knowledge in running/maintaining a server. If I know how to change little policies like the above mentioned, then I feel that I can manage a server with a little more confidence.

Perhaps, if one does not want to share this information to the world, maybe they can pm me. It would be much appreciated.

Thanks.

---

### Post by haqking on 2011-11-15
[s][https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

scroll to password policy section, it should all be valid still.

basically you will use

```
sudo chage username
```

to read more see

```
man chage
```[/s]

Edit.  sorry just reread your OP.  You will need to look at pam_cracklib, i cant remember off hand the config for this, not sure if tis same in ubuntu.

I will be back with more info when i get a second

---

### Post by sisco311 on 2011-11-15
Check out: [http://en.wikipedia.org/wiki/Linux_PAM](http://en.wikipedia.org/wiki/Linux_PAM)
and
```
man pam.d
man pam_unix
cat /etc/pam.d/common-password
```

The obscure option of the pam_unix module enables some extra checks on password strength.

---

### Post by haqking on 2011-11-15
> **sisco311 said:**
> Check out: [http://en.wikipedia.org/wiki/Linux_PAM](http://en.wikipedia.org/wiki/Linux_PAM)
and
```
man pam.d
man pam_unix
cat /etc/pam.d/common-password
```

The obscure option of the pam_unix module enables some extra checks on password strength.

ahh yeah thats the kiddy.

see here for changes you can make [http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html](http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html)

---

