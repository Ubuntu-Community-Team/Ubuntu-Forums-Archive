---
title: "Apache suEXEC with user directives?"
date: 2013-10-21
forum: Server Platforms
---

### Post by wAAbJMT on 2013-10-21
Hi!

Iam looking for a way to run a script with different users.
I dont want to hardcode the users in the config... and I found some information that it should be possible that the user goes to... lets say: 

```
http://localhist/~user1/mxscript.cgi
```

and the script gets executes as user 'user1'.

Does anybody know if that is possible and how?

Thanks a lot!
Greets,
Kodak

---

### Post by SeijiSensei on 2013-10-22
I would think you need to enable Basic Authentication and require the user to login with the same username and password as they have on the operating system itself.  That's just a guess, though. 

If you have not read [http://httpd.apache.org/docs/2.2/suexec.html](http://httpd.apache.org/docs/2.2/suexec.html) I would start there.

---

