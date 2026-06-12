---
title: "How does the GNOME Keyring (SeaHorse) work?"
date: 2011-06-27
forum: Security
---

### Post by amn108 on 2011-06-27
Hi all,

Recently I have started to use the GNOME keyring application to store information such as passwords (along with logins) so that I don't have to remember it. Mostly these are passwords to Internet services, such as websites. It all works well, but I am wondering what kind of protection does the keyring offer me?

As I understand it is a file that is part of my local storage. Interestingly enough, when I start up the keyring application, it doesn't ask me for a password. My worry is that the keyring file, if stolen, will grant the thief all my passwords stored in the keyring, on a silver platter. Is that so? I was thinking that the file was encrypted with the password I specified. My keyring password IS NOT the same as my login password, mind you.

Can it be that the keyring application does not ask me for my password because the daemon remember the password or keeps the decrypted file in memory?

---

### Post by ratcheer on 2011-06-27
[http://www.makeuseof.com/tag/do-encryption-decryption-signing-easily-with-seahorse-linux/](http://www.makeuseof.com/tag/do-encryption-decryption-signing-easily-with-seahorse-linux/)

Tim

---

### Post by amn108 on 2011-06-27
Unfortunately the article spends most of time explaining about public and private keys, while I am dealing simply with my passwords. It also doesn't exactly explain how it works.

I know how cryptography works. What I don't know is how SeaHorse works.

Thanks for trying though :)

---

### Post by haqking on 2011-06-27
> **amn108 said:**
> Hi all,

Recently I have started to use the GNOME keyring application to store information such as passwords (along with logins) so that I don't have to remember it. Mostly these are passwords to Internet services, such as websites. It all works well, but I am wondering what kind of protection does the keyring offer me?

As I understand it is a file that is part of my local storage. Interestingly enough, when I start up the keyring application, it doesn't ask me for a password. My worry is that the keyring file, if stolen, will grant the thief all my passwords stored in the keyring, on a silver platter. Is that so? I was thinking that the file was encrypted with the password I specified. My keyring password IS NOT the same as my login password, mind you.

Can it be that the keyring application does not ask me for my password because the daemon remember the password or keeps the decrypted file in memory?


Your keyring is automatically unlocked when you login to the machine unless you have it set differently which is why you can just open it without an additional password.

try here for a clear explanation of how the gnome keyring works [http://live.gnome.org/GnomeKeyring](http://live.gnome.org/GnomeKeyring)

and the keyring itself is secured under AES-128 and cannot be accessed without the password for the keyring.

[http://cegt201.bradley.edu/projects/proj2005/aes128/](http://cegt201.bradley.edu/projects/proj2005/aes128/)

---

### Post by ratcheer on 2011-06-29
I must admit I am having trouble seeing what Seahorse does, too. I find it much easier to use my keys through the gpg command interface. I can look at my keys with Seahorse, but that's about all.

Tim

---

