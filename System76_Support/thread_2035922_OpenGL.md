---
title: "OpenGL"
date: 2012-07-31
forum: System76 Support
---

### Post by cigtoxdoc on 2012-07-31
RE: Edubook running Edubuntu 12.04

Sketchup 8 free verdion loads and runs with noncritical OpenGL error on my user account (admin) with wine program loader.

However, it will not run from my Son's account (non admin).

How does one make OpenGL work?

Thank you,

John

---

### Post by Ubun2to on 2012-08-01
This is a problem with the Edubuntu distro-not a System76 hardware problem. Just keep that in mind before you post here.
Anyway, here's a quick test to see if you can even access the program from a non admin account first.
1. Right click on the icon (you may have to drag it to the desktop first).
2. Go to the Permissions tab.
3. Make sure it looks similar to this:
Owner: insert-name here
Access: Read and write
Group: group_name_here
Access: Read-only OR Read and write
Others
Access: Read-only OR Read and write
Execute [check mark here] Allow executing file as program
4. The most important thing is to make sure you can read and write the file on a non admin account, and to make sure the file can be executed as a program.

---

### Post by cigtoxdoc on 2012-08-01
Thank you for your reply.  The Edubutu was the doing of upgrade manager.  It was Ubuntu before upgrading to 12.04.
 
So, if I need to get this back to Ubuntu 12.04, please post instructions.

Thank you very much.

John

---

### Post by cigtoxdoc on 2012-08-01
File permissions were already set as you specified. Failed to initialize OpenGL error only occurs on non-admin side.  What graphics device does Edubook use and what are correct drivers for OpenGL?

Thank you,

John

---

### Post by Ubun2to on 2012-08-02
> **cigtoxdoc said:**
> File permissions were already set as you specified. Failed to initialize OpenGL error only occurs on non-admin side.  What graphics device does Edubook use and what are correct drivers for OpenGL?

Thank you,

John

It might be that Open GL requires you to be in a certain usergroup. Post the output of this command in terminal:
```
groups
```
For good measure, also post the output of this command:
```
groups root
```

---

