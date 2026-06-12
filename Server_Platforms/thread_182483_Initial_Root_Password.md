---
title: "Initial Root Password?????"
date: 2006-05-26
forum: Server Platforms
---

### Post by henkdeswardt on 2006-05-26
Please help.

I did my first SERVER installation of Ubuntu 5.04 now.
WHAT is the password for the root account?
During the installation I was only asked to give the username and password for a non-administrator account.

I try and log in as root, but is asks for a password.
The password is not [blank] and not "root"

HHHEEELLLLPPPPP


Henk de swardt

---

### Post by Porrly on 2006-05-26
As your 'normal' user (the FIRST user you created) you have to execute the command:

sudo passwd root

from a terminal, insert your 'normal' user password and then you will be prompted to set the root password.

---

### Post by henkdeswardt on 2006-05-26
Thank you, but is did not work.

I typed:
sudo passwd root
And received the reply:
henkds is not in the sudoers file. This incident will be reported.

(henkds is the first user's login)

So I tired:
passwd root
And received the reply:
You may not view or modify password information for root.


HHEEEEEEELLLLLLLLPPPPPPPPPP

---

### Post by Gustav on 2006-05-26
Although it's not recommenden to use a root account. 

Ubuntu relies on sudo instead, for a explanation look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by henkdeswardt on 2006-05-26
Thank you!!!

Henk

---

### Post by Porrly on 2006-05-26
Gustav, can you tell me why sudo passwd root didn't work?

I was under the impression that the first user on Ubuntu was in the sudoers file by default.

---

