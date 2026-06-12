---
title: "Virtualize encrypted Ubuntu Installation"
date: 2011-07-24
forum: Virtualisation
---

### Post by t.nitus on 2011-07-24
Hi everyone,

I´m having a tricky problem here:

I have to reinstall my laptop, and I would like to run my old ubuntu installation in VirtualBox in my new setup.

My first idea was to simply create a full disk image using a boot cd and then import that in VirtualBox.. The tricky part is that I have my whole hard disk encrypted using dm-crypt.  

Would the boot cd method work anyways, or is there a better possibility?

Thanks for your answers,  T.Nitus

---

### Post by HermanAB on 2011-07-26
Hmm, the main problem I see is that the encrypted system fills the whole disk and cannot be shrunken easily. 

However, Linux is very easy to install, so saving the whole kit and kaboodle is a waste of time - just save your data.

---

### Post by t.nitus on 2011-07-26
Thank you for your answer, Hermann!

The solution you posted is just what I did: I simply backed up my home directory and I´ll copy it in the virtual machine.

---

