---
title: "Log in to any account with live CD?"
date: 2008-12-08
forum: Security
---

### Post by QwUo173Hy on 2008-12-08
I found [a site]("http://www.psychocats.net/ubuntu/resetpassword") that explains how to reset a user password as well as get a list of all user names with only the live CD.

Is this not a serious security issue?

---

### Post by Kinstonian on 2008-12-08
With the physical access required to use a Live CD, you can do a lot more than get a list of users.  This is why physical security is one of the first steps to securing a computer.

---

### Post by jakupl on 2008-12-09
Well when people have physical access to your computer, there is nothing you can do. The only thing that will prevent people from getting to your stuff is if you encrypt your whole hard drive. the only safe computer is the one turned off, in a vault ... and that all people who knew about it are dead (and the computer too).

---

### Post by Sarmacid on 2008-12-09
He doesn't do that with the live CD, it's an option you can select in grub before ubuntu boots, and he even explains the security risk involved.

> Recovery mode makes me root user. Isn't that a security risk?
Well, if you have several people using your computer, you can put small obstacles in their way by setting a root password, setting a Grub password, or setting a BIOS password. Still, anyone who has physical access to your computer and a little know-how practically has root access anyway. She can boot a live CD and mount your partition or even just physically remove the hard drive from your computer and put it in another computer. There's a certain amount of trust you automatically give anyone by allowing her to sit at your computer. 

Also as jakupl said, encrypting is a good idea too.

---

