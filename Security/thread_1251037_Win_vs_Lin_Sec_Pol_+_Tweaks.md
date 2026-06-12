---
title: "Win vs Lin Sec Pol + Tweaks"
date: 2009-08-27
forum: Security
---

### Post by azecraze on 2009-08-27
Could someone please explain to me: What are the options available in Ubuntu/Linux for tweaking or locking down parts of the gui or system.
In Windows, this can be done using either a Group Policy Object or a direct registry edit.

For instance, in Windows, I can put in a registry key called "NoControlPanel" under the "CurrentUser" to prevent that user from gaining access to the Control Panel..... or I can put in a "RestrictRun" complete with a list of allowed programs to run.

Q. Is such a thing available in Linux???

---

### Post by rookcifer on 2009-08-27
> **azecraze said:**
> Could someone please explain to me: What are the options available in Ubuntu/Linux for tweaking or locking down parts of the gui or system.
In Windows, this can be done using either a Group Policy Object or a direct registry edit.

For instance, in Windows, I can put in a registry key called "NoControlPanel" under the "CurrentUser" to prevent that user from gaining access to the Control Panel..... or I can put in a "RestrictRun" complete with a list of allowed programs to run.

Q. Is such a thing available in Linux???

What exactly do you want to restrict your users from doing?

---

### Post by HermanAB on 2009-08-27
The gnome policykit wizard is in the menu.

---

### Post by azecraze on 2009-08-31
to rookcifer: I am in a predominantly windows office environment that has been streamlined for productivity. This means no setting up junk and slowing everything down. I am hoping to transfer some windows users to ubuntu, but also maintain the same level of streamlining.

---

### Post by movieman on 2009-08-31
You can prevent users from doing most stupid things by simply not allowing them to use 'sudo'; hence they won't be installing programs using apt, or messing with system configuration. You can prevent them from downloading and running random programs by mounting /home, /tmp and /var/tmp with no execute permission.

---

### Post by bodhi.zazen on 2009-09-01
The first line of defense on Linux is Permissions. Permissions are sufficient for most users.

If you need more then permissions you next move ot things such as ACL (Access Control Lists) (there are gui tools for ACL) and beyond that you move to SELinux or Apparmor.

---

