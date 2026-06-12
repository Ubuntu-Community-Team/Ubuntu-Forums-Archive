---
title: "Hula: Logging In"
date: 2006-03-12
forum: Server Platforms
---

### Post by btdown on 2006-03-12
I was able to get Hula installed (In Dapper, no less). I can login to the web admin on port 89, and can get to login screen at 8080, but can't login. Should all existing users be able to login with their current pw from this screen, or do I need to enable them somehow in the admin section? 

Any help would be appreciated.
BT

---

### Post by harper on 2006-06-03
i could log in with the default admin account but not with any new users that i created.  the login screen would just refresh.

it turned out that when i created a new user it created the user but didn't save the user info including password properly.  I needed to reset the user password after creating the account.

then everything worked fine and i could log in with new users.

not sure if it is exactly the same problem if you already have existing users but it could be similar.  try reseting the password on a couple of them.

---

