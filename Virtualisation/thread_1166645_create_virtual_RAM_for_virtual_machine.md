---
title: "create virtual RAM for virtual machine"
date: 2009-05-21
forum: Virtualisation
---

### Post by v1nsai on 2009-05-21
Is it possible to use only a page file as ram in a virtual machine?  Meaning, the virtual machine sees the file as system RAM and uses it as such, while still keeping it's own virtual paging file like it expects to.  Wouldn't this be essentially the same thing in a virtual environment?

---

### Post by kidders on 2009-05-23
Hi there,

Your question is a strange one ... Normally, people go out of their way to *prevent* virtual machines paging, rather than forcing them to do so. In any case, I'm not sure what you're trying to achieve makes sense ...

Let's assume you did manage to get your virtual machine to use nothing but virtual memory. The real hardware underlying it can't access data directly from a pagefile anyway, so there would be no net effect on the amount of RAM the VM was actually using ... it would just be a hell of a lot slower, because of all the intermediate copying the host would have to perform. Disk seek times are typically something of the order of 100s of millions of times higher than RAM, so even if using no RAM at all *were* possible, it would take all week for the VM to boot!

---

