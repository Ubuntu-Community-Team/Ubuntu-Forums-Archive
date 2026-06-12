---
title: "Recommend encryption software with GUI?"
date: 2011-02-20
forum: Security
---

### Post by JayUK20 on 2011-02-20
I am looking for some software (not Tryecrypt) where I can just right click a file and it will encrypt it for me. It would be nice to unencrypt on Windows but not essential.

---

### Post by HermanAB on 2011-02-20
You can compress and encrypt a file and set a password using the Nautilus file browser: Right click, compress, Zip, Other options, Password.

---

### Post by Acheron3 on 2011-02-20
Have a look at this:
[http://www.randombugs.com/linux/encrypting-decrypting-files-ubuntu.html](http://www.randombugs.com/linux/encrypting-decrypting-files-ubuntu.html)
I've don't used it but I think it's worth giving it a try.

---

### Post by rookcifer on 2011-02-20
First of all there's two ways to do this: with public/private keys or with symmetric crypto (using a password).

The public/private method:

1) Create a key-pair:

```
gpg --gen-key
```

Use the default of 2048 bit RSA/RSA. 

2) Install seahorse-plugins.  

3) Kill nautilus (or just log-out and then back in).  

4) Once that's done, you will be able to right-click on any file and  encrypt it with any public key on your keyring.  If you want to encrypt to yourself, select your own key.  If you want someone else to have access, encrypt to their key as well.

The symmetric (password) way from the terminal:

```
gpg -c --cipher-algo AES filename
```

That will encrypt with a password using AES-128.  If you don't provide any --cipher-algo at all, it will default to CAST5 (unless you have set your gpg.conf file).  CAST5 is perfectly secure and fine for just about any purpose.

If you want to do it via a GUI (right-click) there are numerous nautilus front-ends for this operation on gnome-look.org.  Here's one example that will probably work:  [http://gnome-look.org/content/show.php/Encrypt%2BDecrypt+Files?content=74653](http://gnome-look.org/content/show.php/Encrypt%2BDecrypt+Files?content=74653)

---

