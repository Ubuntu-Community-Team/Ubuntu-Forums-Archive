---
title: "Corporate File Server on Active Directory Domain"
date: 2007-04-23
forum: Server Platforms
---

### Post by OneSeventeen on 2007-04-23
I would like to create a file server that is easy to manage that authenticates against an Active Directory Domain.

We currently have a shared folder on an Ubuntu machine that anyone on Windows can map to and throw stuff on, which is great, but now I'd like to start applying user/group policies on folders based on the users and groups on our AD domain controller.

Is there a GUI for managing these permissions?

And is there a GUI yet for attaching to an AD domain for authentication?

---

### Post by gfowler on 2007-04-23
I realize this is an Ubuntu forum, and having said that!
If you are looking to do this on a box by itself and has the GUI, CIFS, i.e. the full meal deal take a look at FreeNAS at [http://www.freenas.org/](http://www.freenas.org/)

I've not put it in a production environment but looks ok in testing

Jerry

---

