---
title: "Alternate installer - Encrypted private directory"
date: 2009-02-06
forum: Security
---

### Post by keithvella on 2009-02-06
I am trying to install ubuntu 8.10 using the alternate cd. During the installation process I choose to create the encrypted private directory but for some odd reason this does not get created.

When I do the same installation on a guest machine in VirtualBox on a Windows host I get a folder on the desktop representing the private directory.

Can anyone offer a possible reason for this different behaviour or a solution?

---

### Post by hyper_ch on 2009-02-06
I haven't played with the encrypted private directory. I just think it's much easier to encrypt everything. Is there a reason you only want to have certain parts encrypted?

Anyway, just make also backups of your encrypted data ;)

---

### Post by keithvella on 2009-02-06
I used to make use of the full-disk encrypted LVM option but thought I'd try this instead to reduce the performance penalty when the whole thing is encrypted.

---

### Post by hyper_ch on 2009-02-06
good luck then :)

---

### Post by Tubes6al4v on 2009-02-06
Did you want to have that directory on the main partition or would you be satisfied just creating another partition and encrypting it? The directory wouldn't adjust to the volume needed, which is kind of a bummer, but it gives the functionality.

Alternatively, you could use truecrypt to encrypt a directory (come to think of it, dm-crypt should be able to encrypt a directory as well) after install. I have not done this, I always just have encrypted partitions/drives, but it is a suggestion.

---

