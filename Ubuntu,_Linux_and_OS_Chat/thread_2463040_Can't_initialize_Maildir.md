---
title: "Can't initialize Maildir"
date: 2021-06-02
forum: Ubuntu, Linux and OS Chat
---

### Post by daniilolegovich1995 on 2021-06-02
Good day! I did everything according to the instructions from this link [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-18-04-ru](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-18-04-ru). I'll clarify, installed the postfix, then created two new users and added them to the mail group as root (the root was also added to the mail group). Next, I did everything according to the instructions (I tried it twice from scratch, once I followed the instruction on behalf of the root, the other from just the main account), when I start to do the Maildir initialization item, if I send a letter from the root or the main account to myself , then the cur, new and tmp folders are created, and if I do initialization from the created users, then these folders are not created, even Maildir is not created and letters do not come anywhere.
I also tried to issue full rights to the folders of created users and added them to the list of admins (sudoers), nothing changes. If I write ls -R ~ / Maildir (when I am in the account of the created user), I get a message: "ls: cannot access 'home / mailNDO / Maildir': No such file or directory". Help, please, I've already tried a bunch of different instructions and the same thing every time. Even in the main.cf file, My destinations left only localhost, local.domain and the same thing.

---

### Post by QIII on 2021-06-02
Support request, not a chat subject.

Duplicate exists in General Help.

Closed.

---

