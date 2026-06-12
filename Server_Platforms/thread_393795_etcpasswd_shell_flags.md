---
title: "/etc/passwd shell flags?"
date: 2007-03-26
forum: Server Platforms
---

### Post by Unknowndeepness on 2007-03-26
Hi there, fellas.

I'm one of those lazy people, not beeing able to write just a few more keystrokes to get where i want.
So, i figured i could add a new user, with a shell of "mysql", to get where i want directly.

Just putting "/usr/bin/mysql" as shell works just fine, but i need flags to it, as in "-u <username>" and "-p" to ask for password.
If i do put that into the passwd-file, auth.log will give me this:
```

User <username> not allowed because shell /usr/bin/mysql -u <mysqluser> does not exist

```

Is there some easy way to get past this?

[ Edit ]
I solved it by making a simple pythonscript, using os.system()
[ Edit ]

---

