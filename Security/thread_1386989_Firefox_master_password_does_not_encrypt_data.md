---
title: "Firefox master password does not encrypt data"
date: 2010-01-21
forum: Security
---

### Post by pveurshout on 2010-01-21
I just tried out setting a master password for Firefox saved passwords and compared the old and new (before and after setting the master password) signons.sqlite files. Although passwords were not stored in plain text in either of the files, I did notice that the files were *exactly* the same. Am I wrong in assuming that setting the master password did not encrypt anything at all, or am I simply looking at the wrong file??

---

### Post by lovinglinux on 2010-01-21
If you have opened the file signons.sqlite with a sqlite manager, then you have noticed that both the username and password are encrypted. You can't view them without the master password and encryption key stored inside key3.db.

The database file itself, where the passwords are stored, is not encrypted, but the contents are. I presume you haven't notice any file size change because the passwords and usernames are probably encrypted all the time. What changes when you select the option to use a master password is the master password itself inside key3.db. When you don't have a master password, it still exists inside that file but it is probably blank, so anyone can use it to decrypt the contents of signons.sqlite. This possible scenario is similar to a[ gnome keyring with a blank password](http://www.google.com/search?hl=en&safe=off&num=20&ei=BIlYS_OiG4aXtgfMntS-BA&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAUQBSgA&q=keyring+network+blank+password+site%3Aubuntuforums.org&spell=1).

> From: [http://kb.mozillazine.org/Password_Manager](http://kb.mozillazine.org/Password_Manager)

Firefox stores your password data in two files: key3.db (Master Password / Encryption key) and a "signons" file (encrypted names and passwords). You can back up your passwords by making a copy of both "Key3.db" and the "signons" file for your Firefox version. Firefox 2 uses signons2.txt, Firefox 3.0.x uses signons3.txt, and Firefox 3.5 and 3.6, including current Beta and nightly builds, use signons.sqlite. [4] See Profile folder - Firefox and Profile backup for additional information. 

If you are worried about the Firefox Password Manager security, you could use the [Gnome-keyring password integration](https://addons.mozilla.org/en-US/firefox/addon/8737) add-on for Firefox or the [KDE Wallet password integration](https://addons.mozilla.org/en-US/firefox/addon/49357). I use the KDE integration and it works like a charm. Passwords ans usernames are stored in the Kwallet instead of signons.sqlite.

---

### Post by pveurshout on 2010-01-21
Thanks for your quick and detailed reply! Just to be sure, though: so if I set a master password, is it _not_ true that the key3.db file alone (so without knowing the password) is useless to decrypt the info in signons.sqlite? (like my private PGP-key cannot be used to decrypt anything without knowing the passphrase) I'm somewhat new to encryption and am still learning about that stuff :)

---

### Post by lovinglinux on 2010-01-21
> **pveurshout said:**
> Thanks for your quick and detailed reply! 

You are welcome.

> **pveurshout said:**
> if I set a master password, is it _not_ true that the key3.db file alone (so without knowing the password) is useless to decrypt the info in signons.sqlite? 

No, you still need the key3.db file, otherwise the data stored in the signons.sqlite becomes unavailable.

I just did a test with a clean profile, saved a password, then deleted key3.db, then saved a new one and opened the signons.sqlite with SQLite Manager. Take a look at the stored passwords screenshot:

[[IMG]http://img403.imageshack.us/img403/4416/signons.th.png[/IMG]](http://img403.imageshack.us/img403/4416/signons.png)

Once I saved the first login data without using a master password, the signons.sqlite was immediately updated with encrypted login info (url, username and password). When I delete the key3.db, the encrypted login data remained there on signons.sqlite, but it doesn't show up when I click to see the saved passwords on Firefox. Then I restarted Firefox (new key3.db created) and saved another login and this one shows up on Firefox, but the first one is still hidden, although it never leaves the signons.sqlite. Please note that the fields "username" and "passwd" are replaced with "data[Login][email]" and "data[Login][password]". Even if I replace those with the previous values, this login information doesn't show up on Firefox's password manager interface. So its pretty much lost forever. This happens because the encryption key inside key3.db does not match the one used to store the first login data, even without a master password.

So don't delete key3.db, otherwise your passwords will be unavailable forever, even if you don't use a master password (passphrase).

---

### Post by pveurshout on 2010-01-21
Allright, that sounds safe enough! I suppose the level of security provided by key3.db still depends on the strength of the passphrase, right? So a weak passphrase would make it relatively easy (using brute force or just guessing) to use key3.db without knowing the passphrase on beforehand. As it's a password that has to be typed quite often (each session) I'd like it to be as short as possible, though still providing some level of security. Do you know what length would be appropriate for such, let's call it mid-level, security? Would something like 8 characters be sufficient to keep anyone trying to break in busy for at least a couple of months?

---

### Post by lovinglinux on 2010-01-21
> **pveurshout said:**
> Allright, that sounds safe enough! I suppose the level of security provided by key3.db still depends on the strength of the passphrase, right? So a weak passphrase would make it relatively easy (using brute force or just guessing) to use key3.db without knowing the passphrase on beforehand. As it's a password that has to be typed quite often (each session) I'd like it to be as short as possible, though still providing some level of security. Do you know what length would be appropriate for such, let's call it mid-level, security? Would something like 8 characters be sufficient to keep anyone trying to break in busy for at least a couple of months?

Yep, it's not uncommon to see people bashing Firefox's password manager, but it seems pretty secure for me. 

I use 15 characters :)

---

### Post by pveurshout on 2010-01-22
> **lovinglinux said:**
> Yep, it's not uncommon to see people bashing Firefox's password manager, but it seems pretty secure for me. 

I use 15 characters :)

Yeah, I agree. Can't really see why it would not be secure. Thanks so much for your help; thread marked as solved!

One quick last question, if you don't mind: would there be any security threat if I use the same password for both Ubuntu logon/keyring and the Firefox password manager?

---

### Post by lovinglinux on 2010-01-22
> **pveurshout said:**
> Yeah, I agree. Can't really see why it would not be secure. Thanks so much for your help; thread marked as solved!

One quick last question, if you don't mind: would there be any security threat if I use the same password for both Ubuntu logon/keyring and the Firefox password manager?

As a general rule, you shouldn't use a single password for everything.

I prefer to use one password for Ubuntu login and another for password storage and encryption (Kwallet/Keyring/Gpg). The only security risk is that if someone cracks your login password, would have total access to your protected documents if tries to use the same password.

Most important, don't use the same password related to system access, document encryption or password management on web sites.

---

### Post by pveurshout on 2010-01-22
I'm currently using one and the same password for login and unlocking the keyring, but I use different (and longer) passwords for PGP and TrueCrypt encryption. I completely agree that using different passwords is important (I use different passwords for pretty much everything and keep track of them using a TrueCrypt container with a long passphrase), but I'm willing to take the risk that if someone somehow manages to crack my login password they can access a couple of websites in Firefox using my account details. (Unless, of course, if cracking the logon password is too easy, for instance because it is stored in plain-text somewhere....is it? :o)

---

### Post by lovinglinux on 2010-01-22
> **pveurshout said:**
>  for instance because it is stored in plain-text somewhere....is it? :o)

No, is not.

---

### Post by pveurshout on 2010-01-22
Good :) Well then, thanks so much for all your help. I really appreciate it!

---

### Post by lovinglinux on 2010-01-22
> **pveurshout said:**
> Good :) Well then, thanks so much for all your help. I really appreciate it!

You are welcome.

---

