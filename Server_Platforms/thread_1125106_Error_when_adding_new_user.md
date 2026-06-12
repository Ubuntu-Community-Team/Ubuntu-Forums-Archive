---
title: "Error when adding new user"
date: 2009-04-14
forum: Server Platforms
---

### Post by botfish on 2009-04-14
Why did I receive the following warning when adding a new user?

Also, when adding the new user is did not ask me for a default shell. How do I ensure that the default shell is bash?

#sudo adduser USER
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_NZ.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

... proceded to add user ok

---

### Post by JochenJung on 2009-04-16
> **botfish said:**
> How do I ensure that the default shell is bash?

useradd -s bash

This could also solve the other issues, for "locale" does not work in all shells the same way

---

### Post by botfish on 2009-04-17
Thanks!

---

