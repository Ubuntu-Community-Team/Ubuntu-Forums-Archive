---
title: "Password &amp; Key Manager"
date: 2016-07-02
forum: Security
---

### Post by XBMC old School on 2016-07-02
How does it work? Does it manage passwords in a web brouser? I haven't been able to find a guide, tutorial, or video demo. Is there a Wiki for it? I just see the Arch Wiki.

---

### Post by DuckHook on 2016-07-03
> **XBMC old School said:**
> How does it work? Does it manage passwords in a web brouser? I haven't been able to find a guide, tutorial, or video demo. Is there a Wiki for it? I just see the Arch Wiki.We have no idea which "it" you are referring to:

[LIST=1]
[*]The password and key manager in the various 'buntu flavours is called *seahorse* and a general description of it follows: [http://www.jmcazes.com/sites/default/files/upload/viniv/viniv_us.pdf](http://www.jmcazes.com/sites/default/files/upload/viniv/viniv_us.pdf)
[*]The password manager in your browser that tracks your passwords for various websites is less secure and the details vary from browser to browser.
[/LIST]
There are further password managers that work as apps you must install, and other instances in computer usage that qualify as "Password & Key Manager". For example, rsync passwords, ssh keys, gpg keys, etc. While I doubt that you are referring to these, you must state more clearly which usages you are asking about before we can point you to the right learning resources.

---

### Post by XBMC old School on 2016-07-03
It would be the default password & key manager for UbuntuGnome, couldn't find url image. I did not know if it also managed web brouser passwords as well, that is why I'm asking.

Your weblink goes to a Wine Vineyard brochure.

---

### Post by DuckHook on 2016-07-03
> **XBMC old School said:**
> Your weblink goes to a Wine Vineyard brochure.:lolflag:

Now you and the world know about another one of my vices!

The link I was *actually* trying to copy was this: [https://www.linux.com/learn/manage-passwords-encryption-keys-and-more-seahorse](https://www.linux.com/learn/manage-passwords-encryption-keys-and-more-seahorse)

---

### Post by XBMC old School on 2016-07-03
So does it store brouser passwords?

---

### Post by DuckHook on 2016-07-03
> **XBMC old School said:**
> So does it store brouser passwords?

> **DuckHook said:**
> The password manager in your browser that tracks your passwords for various websites is less secure and the details vary from browser to browser.As mentioned in my first reply, browsers store their own passwords using their own methods and they are generally less secure.

---

### Post by XBMC old School on 2016-07-03
Okay, that is what I thought. That is what i am trying to remedy. So is Keepass the way to go? I generally want something local, encrypted, without a cloud sync option

---

### Post by DuckHook on 2016-07-03
[LIST=1]
[*]keepass is one option.
[*]Another is to encrypt your /home which is a lot easier if you set it up as a separate partition at install.
[*]A third way is to encrypt just a data partition/directory (for example *ecryptfs-setup-private*), move your browser's data into it, then symlink back to the the location that the browser is expecting to find its data on.
[/LIST]

---

### Post by XBMC old School on 2016-07-04
> **DuckHook said:**
> 
[LIST=1]
[*]keepass is one option. [COLOR=#ff0000]Is keepass or KeepassX generally what people use under ubuntu?[/COLOR] 
[*]Another is to encrypt your /home which is a lot easier if you set it up as a separate partition at install. [COLOR=#ff0000]Will this encrypt (protect), the Auto-complete information stored in a web brouser; ie., Chrome, Chromium, or firefox? [/COLOR] 
[*]A third way is to encrypt just a data partition/directory (for example *ecryptfs-setup-private*), move your browser's data into it, then symlink back to the the location that the browser is expecting to find its data on.[COLOR=#ff0000] Same as 2?[/COLOR] 
[/LIST]


If I want an encrypted volume (2nd HDD) to mount and would that be in the OS Password and Key manager?

My main goal is to reset all my online account passwords with really long, random/generic passwords, then consolidate them to one password manager on my home computer. I only access them from my home computer.
[SIZE=1]*These passwords would be written down in a note book.*[/SIZE]

---

### Post by DuckHook on 2016-07-04
The difficulty with answering security questions is the complexity of the topic. A simple-looking question gives rise to a complicated answer. Be that as it may, here's the best short answers I know:> **XBMC old School said:**
> Is keepass or KeepassX generally what people use under ubuntu?There is no "general" tool. Linux, and by extension, Ubuntu is so varied that people use whatever they are most comfortable with. I have never used keepass and know it only by reputation.> Will this encrypt (protect), the Auto-complete information stored in a web brouser; ie., Chrome, Chromium, or firefox?It will protect it in the following sense: your /home directory and all of the info in it will be encrypted. This means that a user who does not know your login password will have to decrypt your /home directory in order to get at any of your information. If both your login passphrase and your encryption passphrase are sufficiently robust, then this is not a trivial task. In fact, with the proper passphrase, your data is very secure. The big "however" is: if a scoundrel does know your login password, then they can login as you and have full access to your data. In that case, encryption is completely bypassed.> Same as 2?In essence, yes. But it requires more care. You will need to know where each of your browsers store their info and then move/symlink-back all relevant directories and files. The upside is that you can still log into a working account if your keyring gets corrupted, although your encrypted data will not be available. There are additional benefits like being able to ssh into your account easily.>  If I want an encrypted volume (2nd HDD) to mount and would that be in the OS Password and Key manager?Yes, provided you used your login password to allow decryption of the volume when you initially set up the encryption.> My main goal is to reset all my online account passwords with really long, random/generic passwords, then consolidate them to one password manager on my home computer. I only access them from my home computer.
These passwords would be written down in a note book.If this is your intent, then I would actually recommend as follows:

There is a downside to all of this encryption/security paranoia: although your data is secured, it comes at the expense of complexity and greater difficulty in recovery should something go wrong. Personally, I believe that the upside to encryption is more important than the downside, but it is important to note that there is indeed a downside. Since this downside increases as the complexity level increases, you must decide at which point the downside is greater than the upside. This is why my choice was option #3 for my own system. An encrypted "Private" directory gives me the fine grain control I need to determine what needs encrypting and what doesn't. For example, I can move my RSA private key into the encrypted directory but leave the rest of the directory unencrypted. In turn, this allows me to ssh into my various systems so that I can manage them remotely.

In short, based on your description, I believe that a similar approach using an encrypted "Private" directory is all you really need. However, each person must determine their own level of comfort with security. What I feel is enough may not feel enough to you. You may wish to encrypt your whole /home directory or even your whole disk and then still use keepass to have as many layers of security as possible. Only you can decide what is enough.

A further aspect of security is this: don't pay so much attention to passwords that you ignore larger threats. For example, it doesn't matter how complex and random your passwords are; if you negligently allow a keylogger to get installed, your passwords become completely transparent to the bad guys and may as well be blank.

---

### Post by DuckHook on 2016-07-04
*Thread moved to **Security** as the more appropriate forum.*

---

### Post by CantankRus on 2016-07-04
I find the default behaviour of chrome based browsers both convenient and secure for saving web passwords.

Passwords are saved to an encrypted file @ ~/.local/share/keyrings/login.keyring and can be viewed using seahorse.
Passwords are only available once logged into a gnome Xsession whereby the login.keyring is unlocked.
Even after a login  ~/.local/share/keyrings/login.keyring  is encrypted.

If you use seahorse to remove the login.keyring password you can view ~/.local/share/keyrings/login.keyring 
[INDENT]or[/INDENT]
use a script such as [**_[COLOR="#B22222"]gnome-keyring-dumper[/COLOR]_**]("https://github.com/mnagel/gnome-keyring-dumper") to show the contents of the login.keyring.

For banking though I prefer to use keepassx to generate and save more secure passwords and use with chrome's incognito mode.

---

