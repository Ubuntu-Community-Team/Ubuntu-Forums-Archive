---
title: "[SOLVED] Skip Login Stage"
date: 2008-12-25
forum: Security
---

### Post by GreaterCore on 2008-12-25
Hi Guys,

How do I configure Ubuntu to login directly to an account without needing to key in anything? I am trying to turn an old box into a media station to connect to the TV, and trying to dumb it down as much as possible. As for the account I will be logging into, I will also need to disable "sudo" for it, but maintaining "su".

Can this be done?

Thanks in advance!

---

### Post by namdung on 2008-12-25
Go to *System-->Admin-->Login Window* from ur admin account as u will be required to enter admin password.

Select *Security* tab. Chk *Enable Automatic Login*, select the user and close. You're done.

The user u select should not be the admin user for him to use sudo. I hope u've activated the root user to use su.

Mark the thread as solved if ur satisfied with the answer.

---

### Post by bodhi.zazen on 2008-12-26
Although I agree you should auto log in to a restricted account, I see no reason to activate the root account.

If you need root access you can either switch users or su to an admin account then sudo.

---

### Post by LRTIMKEN on 2008-12-30
You wrote's nice and I support you![SKF](http://www.nskcn.com/product/ShowClass.asp?ClassID=27) [skf](http://www.nskcn.com/product/ShowClass.asp?ClassID=27) [SKF](http://www.9skf.cn/product/ShowClass.asp?ClassID=27) [skf](http://www.9skf.cn/product/ShowClass.asp?ClassID=27)

---

