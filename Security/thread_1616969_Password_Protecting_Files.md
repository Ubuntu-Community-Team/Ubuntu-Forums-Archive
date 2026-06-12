---
title: "Password Protecting Files"
date: 2010-11-08
forum: Security
---

### Post by nightlock on 2010-11-08
I'm new to ubuntu, and I am very picky about security. Lately I have been trying to find a way to password protect folders that contain sensitive information for my work. I have not been able to do so as I know how, though I have found possibilities of doing it through terminal. I would greatly appreciate if those who reply write out the steps fully, as I have not quite yet wrapped my head around the many commands and uses of Terminal.

---

### Post by movieman on 2010-11-08
The simple solution is to encrypt your home directory so that it won't be accessible to anyone if you're not logged in (it's an option you can choose when adding a new user). If you need finer-tuned security than that, it will be more complex.

---

### Post by HermanAB on 2010-11-08
You can do individual files with zip or gpg.

---

### Post by nightlock on 2010-11-10
but it's not possible to protect created folders?

---

### Post by HermanAB on 2010-11-10
Howdy,

The only proper way to protect data is with encryption.

---

### Post by wojox on 2010-11-10
> **HermanAB said:**
>  gpg.

+1

```
gpg -c filename
```

---

### Post by nightlock on 2010-11-10
Then I suppose the next question is can I encrypt folders and if so how?

---

### Post by Megaptera on 2010-11-10
I suggest TrueCrypt:

[http://www.truecrypt.org/](http://www.truecrypt.org/)

simple to set up and use.

---

### Post by uRock on 2010-11-10
You can also create the private folder via this set of instructions. [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by cariboo on 2010-11-10
The other thing to keep in my is that Ubuntu automagically decrypts a decrypted home directory on login, so to be safe you should log out when not at the computer, and create a low privileged family/friend account for anyone else that uses the computer.

---

### Post by nightlock on 2010-11-18
For some reason, I cannot download truecrypt. I have tried 64 and 32 bit. A screenshot is posted.

---

### Post by cariboo on 2010-11-18
You are trying to open the installer with a text editor. Open a terminal and navigate to where the file is located. Next make it executable:

```
chmod +x truecrypt-7.0a-setup-x86
```

then run the file

```
sudo ./truecrypt-7.0a-setup-x86
```

---

### Post by bodhi.zazen on 2010-11-18
Cryptkeeper is a graphical interface for ecryptfs and is in the repositories

[http://tom.noflag.org.uk/cryptkeeper.html](http://tom.noflag.org.uk/cryptkeeper.html)

---

