---
title: "Add Apache to sudoers"
date: 2009-05-17
forum: Server Platforms
---

### Post by PeterW_R on 2009-05-17
Hi guys,

I've installed the latest distribution of ubuntu with open ssh, phpmyadmin and apache.
I've been able to remotelly execute scripts  but I need to do a script to remotelly halt the server and I need to run it as root or else it won't work.

My question is: How can I safelly add apache to the sudoers list?
Do I need to do something else? (chmod the script, etc)

Thank you!

---

### Post by kidders on 2009-05-18
Hi there,

> **PeterW_R said:**
> How can I safely add apache to the sudoers list?Technically, you can't. That said, assuming your machine isn't a commercial server, you should be *reasonably* safe. Some suggestions (which you may know already) ...[LIST]
[*]Always use visudo to edit /etc/sudoers.
[*]Be very careful with your syntax.
[*]Try to be as limiting as possible when specifying what apache is allowed to do as root.
[/LIST]

> **PeterW_R said:**
> Do I need to do something else?If I were you, I would make sure that apache can't alter/replace the shutdown script. That would make it at least slightly more difficult to exploit the script to acquire root privileges on your box.

I hope that helps.

---

### Post by sherl0k on 2009-05-18
Adding an account to visudo won't do much if the account doesn't have a shell in the system. In most cases apache's shell is set to /bin/false and has no password, so you can't log into the system with the username apache. It has an account, yes, but not one that an end user can succesfully log in with.

A better solution is to add apache to the user group which has the root privileges.

---

### Post by kidders on 2009-05-18
> **sherl0k said:**
> A better solution is to add apache to the user group which has the root privileges.Surely that would be *highly* inadvisable. :confused: There'd be no limit to the kind of damage a carelessly written script could do.

---

