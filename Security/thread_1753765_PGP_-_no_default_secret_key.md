---
title: "PGP - no default secret key"
date: 2011-05-09
forum: Security
---

### Post by Lars Noodén on 2011-05-09
How do I go about specifying which secret key to use to sign a document?  I am trying to eliminate the error below:

```

gpg --clearsign foobar
gpg: no default secret key: unusable secret key
gpg: foobar: clearsign failed: unusable secret key

```

---

### Post by Paddy Landau on 2011-05-09
gpg uses the first key in your keyring as the key, unless you specify otherwise.

It looks as though you have not set up a key.

Open Passwords and Encryption Keys. File > New > PGP Key. Create your key, and it should work after that.

---

### Post by Lars Noodén on 2011-05-10
> **Paddy Landau said:**
> gpg uses the first key in your keyring as the key, unless you specify otherwise.

How do I specify otherwise?   There are multiple keys in this keyring.

---

### Post by Paddy Landau on 2011-05-10
> **Lars Noodén said:**
> How do I specify otherwise?   There are multiple keys in this keyring.
Read the manual for all the options.
```
man gpg
```The option you are looking for is either --default-key or --local-user.
```
gpg --default-key 70A6B53F --clearsign foobar
```

---

### Post by Lars Noodén on 2011-05-10
> **Paddy Landau said:**
> The option you are looking for is either --default-key or --local-user.

Thanks. That was it.

I needed to read the part about --clearsign, where it mentions --default-key

---

### Post by Paddy Landau on 2011-05-10
Personally, I would have preferred a GUI method to sign and encrypt files. That would make it easy.

However, I don't know of any GUI utility that does this.

---

### Post by Lars Noodén on 2011-05-10
> **Paddy Landau said:**
> Personally, I would have preferred a GUI method to sign and encrypt files. 

For e-mail on Thunderbird, there is the plug-in [engimail](http://enigmail.mozdev.org/home/index.php.html). But for general files, I only know of the text-based option.

---

### Post by Paddy Landau on 2011-05-10
> **Lars Noodén said:**
> there is the plug-in [engimail]("http://enigmail.mozdev.org/home/index.php.html").
I don't think this works on files; only on emails.

---

### Post by Irihapeti on 2011-05-10
If you install seahorse-plugins, you have "sign" and "encrypt" (or "decrypt") as options when you right-click on a file.

---

### Post by spynappels on 2011-05-10
Not much use here, but KDE has Kleopatra which iirc has the option to encrypt or decrypt using a GUI.

Might be wrong though, I use Kleopatra on my Windows partition.

---

