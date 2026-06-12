---
title: "why is default home directory permissions 755?"
date: 2011-02-08
forum: Security
---

### Post by sigflup on 2011-02-08
On most unixes I find the default home directory permissions are 755. Can someone explain to me why this is? I usually get on just fine with 750. Why 755?

edit:

I understand 755 is the default directory umask but why doesn't adduser change this before making new home directories? Is there a good reason for home directories to be globally readable?

---

### Post by cariboo on 2011-02-08
The reason for permissions to be set to 755, is to make it easier for new users to share files. Personally I set permissions to 700 for my home directory.

---

