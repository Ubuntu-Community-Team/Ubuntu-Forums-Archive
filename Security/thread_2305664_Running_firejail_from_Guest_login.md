---
title: "Running firejail from Guest login"
date: 2015-12-08
forum: Security
---

### Post by adagio on 2015-12-08
I've had some success in maintaining a secure instance of firefox with [firejail]("https://l3net.wordpress.com/projects/firejail/").

The question then was can firejail be combined with a Guest login.

The result was the following error:

```
Error clone:main(1299): Operation not permitted
```

This is because the Guest user is [unable to run SUID programs]("https://l3net.wordpress.com/projects/firejail/comment-page-1/#comment-5492")? (firejail being a SUID executable.)

---

