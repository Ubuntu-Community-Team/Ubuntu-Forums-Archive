---
title: "Server refused our key - Keyfile authentification from anther user than root"
date: 2019-01-27
forum: Security
---

### Post by webprog24 on 2019-01-27
I tried to add another user with sudo right on server. Thats easy. The problem is that I only allow keyfile authentification on the server. I followed all the instruction on the internet to add another user using the keyfile authentification but somehow thats not possible. All the good advices did not help.

[LIST]
[*] .ssh 700 and authorized_key 600 permission
[*]added AuthorizedKeysFile	home/%u/.ssh/authorized_keys
[*]generated and placed the keyfile correct. For root it works sasme way
[*]restarted ssh with service ssh restart
[/LIST]
I tested now 2 days severa configurations and I still can only authentificate with root using keyfile authentification. If i try to ssh login with another user then it always fail with the message server refused our keys. I grated the new user all rights and file owner is the user. I tested all very carefully but it still does not work. Has anybody an idea?

---

### Post by joegry on 2019-04-20
Did you generate these keys as the root user or as the new user that you're trying to authenticate with?  Make sure you generate the keys using the new user and make sure to place the key file and authorized_keys under the new user's /home/newuser/.ssh/ folder

---

