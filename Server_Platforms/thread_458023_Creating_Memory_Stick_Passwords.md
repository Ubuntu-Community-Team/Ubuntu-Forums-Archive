---
title: "Creating Memory Stick Passwords"
date: 2007-05-29
forum: Server Platforms
---

### Post by Drezard on 2007-05-29
So basically on my ubuntu linux box, i want to have to put in a special usb memory stick before logging into my computer. So, if i want to login to my ubuntu computer i have to first insert this usb memory stick, then i enter my password if I dont insert this special memory stick then type in my password, it wont login.

Would this be possible?

If so what programs/features do I use? (I don't need a long explaination I can google most of it, I just need
some to go on).

Regards, Daniel

---

### Post by ruy_lopez on 2007-05-29
As far as I know, to achieve what you want, you would need your /home on a separate, encrypted partition.

There's a howto for encrypting your home partition here:

[https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)

And there's information at the bottom of this page on how to add keys to an encrypted partition:

[http://luks.endorphin.org/dm-crypt](http://luks.endorphin.org/dm-crypt)

Basically you would set-up the partition using a password first, then later add a keyfile. If the key is going to be on a removable drive, you have to edit /etc/default/cryptdisks so that the boot process mounts the removable drive before the encrypted partition.

If your still interested, the links should get you started.

---

### Post by PetePete on 2007-05-29
would it also be possible to create a symlink from /etc/passwd to the memory stick?

i have a horriable feeling it would mess various service accounts up, but might work... if you do try it, make sure you back your data up first ;)

---

