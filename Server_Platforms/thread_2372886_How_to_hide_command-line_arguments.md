---
title: "How to hide command-line arguments?"
date: 2017-09-29
forum: Server Platforms
---

### Post by LHammonds on 2017-09-29
Does anyone know a trick to hide command-line arguments to a program so it doesn't expose the options in the process list?

Example:

```
sendemail -login mysecretid -password mysecretpassword
```

Is there a way to prevent the ID/password from being exposed in the process list if the command does not support reading settings from a file?

Thanks,
LHammonds

---

### Post by TheFu on 2017-09-30
Many will get them from environment variables.

---

### Post by LHammonds on 2017-10-02
Finally found a good article on this subject.

[NetMeister.org - Passing Passwords](https://www.netmeister.org/blog/passing-passwords.html)

---

