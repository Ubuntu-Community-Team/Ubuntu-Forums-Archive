---
title: "Deny and Allow on new ssh does not work why ??"
date: 2009-09-18
forum: Server Platforms
---

### Post by pi4r0n on 2009-09-18
Hello Guys

I have installed ssh server. ALL is nicely configured but i wanted to limit access to only one user. For some reason it does not work ??

AllowUser Jow
DenyUser John

ALL howtos i have seen says to do this and restart ssh but it does now work I still can login as John. Can someone tell my why?? What I am doing wrong

Also do you have any good advance ssh howtos ?? Saying advance I mean advance.

Cheers

pi4r0n

---

### Post by Bachstelze on 2009-09-18
```
AllowUser Jow
DenyUser John
```

is redundant. Try with just

```
AllowUser Jow
```

---

