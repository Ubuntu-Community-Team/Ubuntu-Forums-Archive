---
title: "Encrypted home on an already installed system"
date: 2009-12-02
forum: Security
---

### Post by mu22le on 2009-12-02
Hello,
I have ubuntu 9.04 installed on a lab workstation. For privacy reasons we need to add a user with an encrypted home directory. 

I know Ubuntu gives me a choice to encrypt my home folde at install time but the machine is in use and re-installing is not an option at the moment (yes, I know, poor foresight one year ago...). 

Also I'd rather leave the other users homes alone and not encrypt them (but if it is easier/necessary to setup home encryption for everybody then ok).

Is it possible to add home encryption to an already running ubuntu system? (btw do you have a link to a _recent_ documentation to encrypt /tmp and swap?)

Thanks in advance for the help,

Emme

---

### Post by mu22le on 2009-12-02
answer to the first question (create a new user with encrypted home) seems to be here:
[http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)

just do:
sudo adduser --encrypt-home <new_user>

As soon as I find a link on encrypting the swap I'll get back to you

---

### Post by bodhi.zazen on 2009-12-02
You can easily encrypt swap. You can use LUKS or Ecryptfs

Tons of stuff on LUKS, for example :

[http://blog.larsstrand.org//article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.larsstrand.org//article.php?story=EncryptedSwapAndHomeUbuntu)

Or search for Ecryptfs

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by paradigm2 on 2009-12-05
Well I've seen instructions on how to encrypt home after the fact and even tried it but I ended up getting a lot of errors during the sync and decided to reinstall instead.

Remember if you go to 9.10 you can use the normal installer to get an encrypted home as well as the ext4fs by default.  If you have a spare drive simply put it in (or use an external or large USB drive?) as a secondary and copy your existing home directories over to it.  Then after reinstall set up the accounts and copy the data back intelligently (you may not want to copy over certain config files, etc).

bodhi.zazen already provided the links I think for what you were asking if you don't reinstall...

---

### Post by Agent ME on 2009-12-06
He's making a new user account with an encrypted home, so he doesn't have to worry about possibly losing that user's files when making the account ;)

The "ecryptfs-setup-swap" command works well for making swap space encrypted (but seems to have nothing really to do with ecryptfs; not really sure why it's named that).

---

