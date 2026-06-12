---
title: "swacl HP-UX PA-RISC compatible command to UBUNTU"
date: 2008-12-27
forum: Security
---

### Post by a.mant on 2008-12-27
How Srs.,

I have to execute the following command on UBUNTU, but I don't know the related command for it. The original command is for HP-UX PA-RISC.

I will appreciate all help, because if I could make it, I will solve a problem with my database.

The original command is:

swacl -l root -M any_other:rt

This gives permissions to acces swlist for any user.


** I need to transform this command to UBUNTU reality.

Thanks a lot,

Alexandre.

---

### Post by brian_p on 2008-12-28
> **a.mant said:**
> 

I will appreciate all help, because if I could make it, I will solve a problem with my database.

The database is on a Ubuntu machine? The chmod and/or chown commands could be what you are looking for.

---

### Post by a.mant on 2008-12-28
Hi Brian. How're you? 

Yes, the database server (Oracle Database 10g Enterprise Edition) is on the Ubuntu desktop machine.

I need to make this command for Ubuntu, because Oracle needs to access the SWList (I think it's the Software list). This is a solution from Oracle for HP-UX, but I don't know how to make it on ubuntu.

Could you please help me giving permission to access swlist for any user?

Thanks a lot.

a.mant

---

### Post by scorp123 on 2008-12-29
> **a.mant said:**
> I need to make this command for Ubuntu, because Oracle needs to access the SWList (I think it's the Software list). Ubuntu's software is organised in a different way than on HP-UX. So the HP-UX commands "swlist" and so on don't work on Ubuntu.

Given that I don't think you need to translate that HP-UX command at all. Even if I told you to install the "acl" package on Ubuntu and use the "setfacl" command ... you'd only hit one more road block right after this one.

You'd be better off to closely analyse that script and understand what it tries to do, then rewrite it so you get a valid Ubuntu script.

---

