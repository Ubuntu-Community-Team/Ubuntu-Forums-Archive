---
title: "reset encryption key expire date"
date: 2022-01-08
forum: Security
---

### Post by pete0512 on 2022-01-08
I find that when I try gpg --list-keys the encryption sub key is not listed
gpg --edit-key <key> does list it with index (1) but when I select that key and input expire it will only allow me to modify the secret key, it then warns me that the encryption has expired but when I try to modify that date it simply returns to editing the secret key

---

### Post by TheFu on 2022-01-08
Dates for keys cannot be changed.
Create a new key with the date you'd like.
Keep the older key around for use to read old stuff.

---

