---
title: "gnome3 login keyring failed"
date: 2012-01-01
forum: Ubuntu Studio
---

### Post by ron2794 on 2012-01-01
i never provided my gnome a login keyring password. but whenever i am logging in to  empathy it asks me login keyring and says that "login keyring no more matches your login password. provide a login keyring"
please help......
is there any way i can delete the login keyring file (wherever it exists), by sudo and then i will have to give a fresh login keyring thereafter

---

### Post by Paddy Landau on 2012-01-01
Try this:

Open Password and Encryption Keys.
Go to the Passwords tab.
Find the Empathy key that it is complaining about, right-click and select Delete.
Log out and in again.

If that doesn't work, I know that Gnome 2 stores its keyrings in ~/.gnome2/keyrings, so perhaps that will help you find the keyring in Gnome 3 and then delete that folder. Careful about what you delete!

---

