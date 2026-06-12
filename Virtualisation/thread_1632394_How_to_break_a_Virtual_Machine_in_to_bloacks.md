---
title: "How to break a Virtual Machine in to bloacks"
date: 2010-11-27
forum: Virtualisation
---

### Post by Nirandi on 2010-11-27
II'm trying to break a VM to parts and bring map them together to boot. I want to break a Virtual Machine in to 16 pieces of 16KB. I'm very new to virtualization. I do not know if this is possible and if possible where I should start. Can some one help me with it.

---

### Post by dcstar on 2010-11-28
> **Nirandi said:**
> II'm trying to break a VM to parts and bring map them together to boot. I want to break a Virtual Machine in to 16 pieces of 16KB. I'm very new to virtualization. I do not know if this is possible and if possible where I should start. Can some one help me with it.

Virtual Machines are "booted" by their particular VM environments, your request does not make much sense.

Do some web searches and find out what VMs are.

---

### Post by HermanAB on 2010-11-28
Howdy,

Do you want to copy it in pieces using a memory stick or something?

If so, make a multi-part tar ball of the whole thing and tell tar to create the pieces no bigger than a certain size.  Copy the pieces and untar. Read the tar man page for details.

---

