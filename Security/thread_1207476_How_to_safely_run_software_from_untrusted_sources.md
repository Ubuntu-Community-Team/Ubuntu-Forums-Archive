---
title: "How to safely run software from untrusted sources"
date: 2009-07-08
forum: Security
---

### Post by zoubidoo on 2009-07-08
What is the safest way to run closed-source software from an untrusted source?

I understand that installing a .deb is the same as giving root access, so that's not a good idea.

I have heard running software in a jail is one approach (BTW can anyone suggest a good tutorial).  Is running in a virtual machine better?  Are there other approaches?

Thanks for any suggestions.

Z.

---

### Post by cariboo on 2009-07-08
>  What is the safest way to run closed-source software from an untrusted source?


Don't run it.

> I understand that installing a .deb is the same as giving root access, so that's not a good idea.

You can't install software anywhere other than you home directory if you aren't installing it as root.

> I have heard running software in a jail is one approach (BTW can anyone suggest a good tutorial). Is running in a virtual machine better? Are there other approaches?

If you only install software from the repositoiries, then you won't have to worry about untrusted software.

If you are talking about running windows software using wine, all the applications are installed in you home directory, so the only part of the system that will be affected is your home directory, which of course you back up at least once a week, right. :)

---

### Post by zoubidoo on 2009-07-08
> **cariboo907 said:**
> Don't run it.
If you only install software from the repositoiries, then you won't have to worry about untrusted software.


Thanks for your reply.  There are many commercial linux applications that do not have open-source equivalents, so for some people it is inevitable to have to trust closed-source software.  (e.g labview, mainactor, skype, picasa,...).

What I'm asking is, is it possible to use these apps as safely as possible, that is, not grant them full privileges, restrict access to filestore, and monitor/restrict network access.

I've just come across Apparmor which seems to be relevant.

---

### Post by natravis on 2009-07-08
> **zoubidoo said:**
> I've just come across Apparmor which seems to be relevant.

Apparmor is the right path AFAIK.

---

### Post by HermanAB on 2009-07-09
The usual way is to install the untrusted software in a virtual machine.  Then if it screws up, the damage is limited to that VM.  So, look into Virtualbox and VMware.

---

### Post by juancarlospaco on 2009-07-09
LiveCD, Lethe, something similar.

Enable and configure SELinux.

You can unpack the .deb and see whats inside without installing, 
but this doesn't help when binary-only data is inside.

---

