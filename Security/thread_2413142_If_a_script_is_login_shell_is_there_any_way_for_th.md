---
title: "If a script is login shell is there any way for the user to get a real shell?"
date: 2019-02-21
forum: Security
---

### Post by wireandlace on 2019-02-21
I'd like to have a guest user account that is simply a basic program displaying some information or maybe something a bit more elaborate and fun, but hopefully simple enough that it can be pretty easy to make sure it doesn't have bugs itself. My plan is to do this by setting the user's shell as /bin/myprogram

Assuming it itself is not vulnerable (and it should not ever be accepting or doing anything with user input as I envision it) then is there any way for a user logging in with that account to get a real shell from their position?

---

