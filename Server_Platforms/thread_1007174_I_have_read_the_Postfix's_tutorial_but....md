---
title: "I have read the Postfix's tutorial but..."
date: 2008-12-10
forum: Server Platforms
---

### Post by lks45 on 2008-12-10
I receive an error connecting with pop3!

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

the system needs create the folder "Maildir" in user system folder, but not create... Trying to login with a pop3 client I see: "-ERR chdir Maildir failed"

Someone can be help me?

---

### Post by tshrinivasan on 2008-12-10
Is the error show in server or the client?
what clicne you use for pop?

---

### Post by lks45 on 2008-12-10
> **tshrinivasan said:**
> Is the error show in server or the client?
what clicne you use for pop?

client, any pop client... outlook, telnet...

---

### Post by tshrinivasan on 2008-12-10
Well.

see this link.
[http://ubuntuforums.org/archive/index.php/t-114549.html](http://ubuntuforums.org/archive/index.php/t-114549.html)

you have to create some directories in the home folder of the particular user, as

~/Maildir
~/Maildir/tmp
~/Maildir/cur
~/Maildir/new

---

### Post by hyper_ch on 2008-12-10
postfix is a MTA and no POP server. You'll have to install courier or dovecot.

---

### Post by lks45 on 2008-12-10
> **hyper_ch said:**
> postfix is a MTA and no POP server. You'll have to install courier or dovecot.

courier is installed too, see: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

