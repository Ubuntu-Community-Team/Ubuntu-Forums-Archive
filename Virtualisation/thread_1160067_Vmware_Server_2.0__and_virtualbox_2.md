---
title: "Vmware Server 2.0  and virtualbox 2"
date: 2009-05-15
forum: Virtualisation
---

### Post by fieldyweb on 2009-05-15
this isn't a question, its an observation, which may help others.

If you run Virtualbox 2.x and VMware Server 2.x on the same machine, depending on the machine type, you may find, that you can't run them at the same time.

I've found if there is a virtualbox session loaded, then the VMware server session fails at 95% with an error about not being able to start the monitor device.

If you start a VMware machine, then start a virtualbox machine, then the vmware machine shuts down.

I'm specifically using a Dell E3400

I think this is due to both packages wishing to use the Virtualization functionality on the motherboard, and Virtaulbox being a bigger bully.

---

### Post by maflynn on 2009-05-15
dumb question
why would you want to run both at the same time?

---

### Post by h1tchiker on 2009-05-28
Hi,

I would love to know the answer to this as I have a VMware server running and also wish to use VirtaulBox to connect to an XP environment for Webex sessions at work.  My VMware servers are not allowed on the same subnet as our desktop environment so transfering files is a nightmare, so if there is a resolve to this it would be greatly appreciated.

---

