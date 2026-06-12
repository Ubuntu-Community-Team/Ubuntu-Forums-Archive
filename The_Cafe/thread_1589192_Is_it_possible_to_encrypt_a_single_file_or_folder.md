---
title: "Is it possible to encrypt a single file or folder?"
date: 2010-10-06
forum: The Cafe
---

### Post by user1397 on 2010-10-06
I know that when installing ubuntu you have the option of encrypting your home folder, but what if you just want a single folder or even a single file encrypted and nothing else?

Is there a way to do this easily?

---

### Post by Megaptera on 2010-10-06
There might be other ways, but TrueCrypt is simple & effective:

[http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/](http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/)

---

### Post by Paqman on 2010-10-06
> **ubuntuman001 said:**
> 
Is there a way to do this easily?

Yep, install seahorse-plugins, make yourself an encryption key in Passwords and Encryption Keys and then you'll be able to encrypt files from a right click.

---

### Post by surfer on 2010-10-06
a very simple way to encrypt a directory is [encfs]("http://www.arg0.net/encfs") (you can install it with synaptic).

---

### Post by mcduck on 2010-10-06
> **surfer said:**
> a very simple way to encrypt a directory is [encfs]("http://www.arg0.net/encfs") (you can install it with synaptic).

..and to make things even simpler, you can use Cryptkeeper, a nice & simple Gnome GUI for EncFS. :)

---

### Post by surfer on 2010-10-06
> **mcduck said:**
> ..and to make things even simpler, you can use Cryptkeeper, a nice & simple Gnome GUI for EncFS. :)

oh, didn't know about that one. i'll try it right away!

---

### Post by t0p on 2010-10-06
And yet another alternative (the method I use) is **cfs**.  It's available through Synaptic.

Isn't Linux wonderful.  So much choice.

---

### Post by HermanAB on 2010-10-06
Good grief...

$ gpg -c filename

---

### Post by pwnst*r on 2010-10-06
> **HermanAB said:**
> Good grief...

$ gpg -c filename

Are you Charlie Brown or something?

---

### Post by HermanAB on 2010-10-06
Lucie, is that you!?

---

### Post by pwnst*r on 2010-10-06
Nope, but you didn't have to be an *** to the OP for a simple question.

---

### Post by user1397 on 2010-11-02
i forgot to say thanks for all the replies guys, but i actually have one more question, if you chose not to encrypt your home folder when installing, but want to do it now, how would you go about doing that?

---

### Post by FuturePilot on 2010-11-02
> **ubuntuman001 said:**
> i forgot to say thanks for all the replies guys, but i actually have one more question, if you chose not to encrypt your home folder when installing, but want to do it now, how would you go about doing that?

```
ecryptfs-migrate-home
```

Preferably done from a console.

Or manually [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

---

### Post by undecim on 2010-11-02
> **FuturePilot said:**
> ```
ecryptfs-migrate-home
```

Preferably done from a console.

Or manually [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

That command needs to be run as root. I would recommend doing it from a recovery console. You need to install ecryptfs-utils first. It also needs the username with -u option, (i.e. run it as "ecryptfs-migrate-home -u username")

You should also make a backup of your home directory first (to an external hard drive, for example)

I think it will also tell you to log in before restarting to make sure you can access your files. You can do that from the recovery console with "sudo -iu nobody sudo -iu username" (so that you type in your password to unlock it)

After that, just exit the $ shell, and type "reboot"

---

### Post by sharkey77 on 2013-04-30
> **Paqman said:**
> Yep, install seahorse-plugins, make yourself an encryption key in Passwords and Encryption Keys and then you'll be able to encrypt files from a right click.

When you launch the encrypted file it creates a new unecrypted file.  This is not secure, the unecrypted file can be easily recovered even if deleted.

---

### Post by codemaniac on 2013-04-30
Old thread. Closed.

---

