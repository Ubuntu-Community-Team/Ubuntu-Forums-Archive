---
title: "access shell via ssh using root"
date: 2012-02-01
forum: Server Platforms
---

### Post by Jefferythewind on 2012-02-01
Hi everyone,

  I just have a fresh 11.10 installation.  I cannot access the server remotely using the root account.  Is this supposed to be like this?  I have a super user account and can get to the root prompt by using the command: 
```
sudo bash
```
But NOT by trying to log in as "root" via ssh.

Thanks!

---

### Post by drmrgd on 2012-02-01
By default I believe the root account is disabled, and you'd have to activate it in order to use it.  I would imagine this is not possible remotely.  Why do you need root, though?  You should be able to do what you need with an admin account and sudo.

---

### Post by Jefferythewind on 2012-02-01
I agree with both of your comments, thanks @drmrgd.  I don't need root access.  But if I did, do you know how to activate it?

Edit:
  Sorry a quick search shows the official ubuntu docs have all the info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks

---

### Post by ruffEdgz on 2012-02-01
> **Jefferythewind said:**
> I agree with both of your comments, thanks @drmrgd.  I don't need root access.  But if I did, do you know how to activate it?

Edit:
  Sorry a quick search shows the official ubuntu docs have all the info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks

Just to add on to @drmrgd comments, you can always access the account 'root' but you just need to use 'sudo' to do so. I wouldn't recommend it unless you are stuck and you know what you are doing just because you can really break things as the 'root' user.

Best of luck with what you are doing.

---

