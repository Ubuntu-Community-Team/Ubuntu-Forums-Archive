---
title: "Redirecting all emails except password reset"
date: 2022-03-24
forum: Server Platforms
---

### Post by eitsop on 2022-03-24
I have a test server, that I want to be able to redirect all except password reset emails.

So I put in this in my /etc/postfix/main.cf
```
header_checks = regexp:/etc/postfix/header_checks
```

/etc/postfix/header_checks
```
!/Subject: \[TEST SYSTEM\] Please reset your password/m REDIRECT testing@mycompany.com
```

! at front is meant to be a not, and /m a multi line

I have tried multiple variations, but I can't get it to not redirect those emails with certain subject line

Any help please

---

### Post by slickymaster on 2022-03-25
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2022-03-27
I do not use Postfix and not familiar with it but could this be related to your issue?

[https://serverfault.com/questions/806535/postifx-header-checks-not-working](https://serverfault.com/questions/806535/postifx-header-checks-not-working)

LHammonds

---

