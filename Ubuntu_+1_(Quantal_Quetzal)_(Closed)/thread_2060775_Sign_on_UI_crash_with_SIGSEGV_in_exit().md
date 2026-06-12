---
title: "Sign on UI crash with SIGSEGV in exit()"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by nikhilbhalwankar on 2012-09-21
Whenever I start the laptop running Ubuntu 12.10, I get the below error.

 Sign-on UI crash with SIGSEGV in exit()


Can anybody please help me on this?


Many Thanks,
Nikhil Bhalwankar

---

### Post by effenberg0x0 on 2012-09-21
> **nikhilbhalwankar said:**
> Whenever I start the laptop running Ubuntu 12.10, I get the below error.

 Sign-on UI crash with SIGSEGV in exit()


Can anybody please help me on this?


Many Thanks,
Nikhil Bhalwankar

I think it relates to "Online Accounts" in System Settings. Do you have any account configured there? 

Do you still get this bug after performing a successful sudo apt-get update && sudo apt-get upgrade and rebooting?

If so, does it also happens when you login as guest or creates another user?

I believe you should report it here:
[https://launchpad.net/online-accounts-signon-ui](https://launchpad.net/online-accounts-signon-ui)

Regards,
Effenberg

---

### Post by nikhilbhalwankar on 2012-09-23
> **effenberg0x0 said:**
> I think it relates to "Online Accounts" in System Settings. Do you have any account configured there? 

Do you still get this bug after performing a successful sudo apt-get update && sudo apt-get upgrade and rebooting?

If so, does it also happens when you login as guest or creates another user?

I believe you should report it here:
[https://launchpad.net/online-accounts-signon-ui](https://launchpad.net/online-accounts-signon-ui)

Regards,
Effenberg
Hello,

sudo apt-get update && sudo apt-get upgrade and rebooting resolved the issue.

Thanks a lot !!

---

