---
title: "ecryptfs - when does encryption/decryption occur?"
date: 2010-10-26
forum: Security
---

### Post by Dave_L on 2010-10-26
On my netbook, I plan on setting up my /home/user ("user" denotes my actual username) directory as encrypted.

I've read several articles and topics here about ecryptfs, and understand the procedure. But I want to understand the limitations first, and have some questions.

1) Does the entire content of /home/user get decrypted on login, and encrypted on logout?

2) If I do a normal shutdown, without explicitly logging out, will all of /home/user be encrypted?

3) If an abnormal shutdown occurs, such as loss of power or crash, will /home/user be unencypted, meaning that booting into single user mode or booting from a Live USB would enable access to the unencrypted contents of /home/user?

Thanks :)

---

### Post by movieman on 2010-10-26
eCryptfs encrypts and decrypts on access: it uses a loopback mount to create a virtual file system which handles all that.

If you reboot the PC and look at the files without logging in, you'll just see garbage encrypted data.

---

### Post by Dave_L on 2010-10-27
Thanks.

---

