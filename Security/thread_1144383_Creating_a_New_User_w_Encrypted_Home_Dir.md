---
title: "Creating a New User w/ Encrypted Home Dir?"
date: 2009-04-30
forum: Security
---

### Post by CarlosinFL on 2009-04-30
When I installed Ubuntu & created my first user, it asked me if I wanted to encrypt their home directory. Can someone please tell me if I created a new user on my system using the 'useradd' command, how can I also 'encrypt' their home directory?

Thanks for any assistance!

---

### Post by bodhi.zazen on 2009-04-30
```
adduser --encrypt-home new_user_name
```

---

### Post by CarlosinFL on 2009-05-01
Well, normally I do the following so I was wondering if there is an option for useradd command -vs- adduser?

---

