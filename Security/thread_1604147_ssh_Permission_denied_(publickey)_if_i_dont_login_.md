---
title: "ssh: Permission denied (publickey) if i dont login to UI"
date: 2010-10-23
forum: Security
---

### Post by 133 on 2010-10-23
Hi guys,

I setup this ssh with PasswordAuthentication no on my ubuntu 10.04, I have this problem that ssh login from another machine only work after login to UI first.

Steps:
1. Login to UI and setup ssh with PasswordAuthentication no.
2. Test it from another machine - it works.
3. Reboot the machine (ssh server) without login to UI, try ssh login from another machine - it failed with Permission denied (publickey).
4. Login to UI and try ssh login from another machine - it works again.

So why is that I have to login to the machine first before I can ssh login from another machine? it doesnt make sense.

Can anyone help?

Cheers
133

---

### Post by FuturePilot on 2010-10-23
Did you select the encrypted home option when installing?

---

### Post by CharlesA on 2010-10-23
> **FuturePilot said:**
> Did you select the encrypted home option when installing?

That was my thought as well. If you have an encrypted home directory, it won't be able to access the keys, since the home directory won't be decrypted until you login.

---

### Post by 133 on 2010-10-24
Yes. That expplain why it is not working then.... :-(
Is there any solution/workaround to that?

Thanks

133

---

### Post by CharlesA on 2010-10-24
See here: [http://ubuntuforums.org/showthread.php?t=1602399](http://ubuntuforums.org/showthread.php?t=1602399)

---

### Post by 133 on 2010-10-24
It works now brilliant!!! thanks CharlesA!!!

---

