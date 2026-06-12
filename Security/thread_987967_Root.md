---
title: "Root"
date: 2008-11-20
forum: Security
---

### Post by HenkR on 2008-11-20
Hi,

where is the root account in Ubuntu? I installed it, and in the installation I created a user but I didn't had to define a root password.

Now, when a password is asked, I have to enter the password of the user.

Is the user created during installation the root? Why can you choose a name then?

---

### Post by hyper_ch on 2008-11-20
have a read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Sarmacid on 2008-11-20
That account you created is not root, it's just an account with administrative privileges and access to the sudo command which let's you use commands as if you were root.```
whoami
sudo whoami
```
You'll see it there.

---

