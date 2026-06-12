---
title: "Locked Out Of Server"
date: 2012-01-15
forum: Server Platforms
---

### Post by marcusww on 2012-01-15
I have locked my self out of my server, for no apparent reason..am now getting

[COLOR=Blue]Permission denied (publickey).[/COLOR]

I was messing around with a few permissions on files, but I can't logically understand why this would affect my server access with public/private key pair.

---

### Post by Habitual on 2012-01-15
oops.

---

### Post by Habitual on 2012-01-15
> **marcusww said:**
> I have locked my self out of my server...
[COLOR=Blue]Permission denied (publickey).[/COLOR]

> **marcusww said:**
> I was messing around with a few permissions on files, ...

Oh "grasshopper" :)

messing around with files WHERE?
Local or Remote?

---

### Post by marcusww on 2012-01-15
remote...

I was changing permissions and owners, that's all....

---

### Post by CharlesA on 2012-01-15
> **marcusww said:**
> remote...

I was changing permissions and owners, that's all....
If authorized_keys has the wrong owner or permissions, you are pretty much out of luck. There is no way to fix that without getting access to the machine either locally or through another account that has ssh access.

---

### Post by SeijiSensei on 2012-01-16
Is this a physical server or a virtual one?  Virtual hosting providers like Linode offer alternatives to SSH for connecting with your VM in the server's control panel.  

If it's a physical server, then you'll need physical access like Charles suggests.  Logging in with a second account will only work if either (a) that account has sudo privileges, or (b) the root account has a password so you can use su.

---

