---
title: "[SOLVED] Enigmail / GCR caches passphrase for ever"
date: 2014-06-01
forum: Security
---

### Post by afxmac on 2014-06-01
Ever since my Xubuntu 14.04 upgrade, I only get asked the PGP passphrase once after reboot.
Having my gpg passphrase cached indefinitely is something I consider a  major security hole.

gpg-agent is not running, it does not matter whether I've enabled gpg-agent in enigmail or not and the cache setting is ignored in enigmail, so something else but enigmail handles the gpg pw.

When Enigmail asks for the passphrase, I see /usr/lib/gcr/gcr-prompter running.

So why the &%$&§! hell does that silliness take over the gpg prompting? I never asked it to.
And where is it configured? 
And why does it not even have a man page?

cheers
afx

---

### Post by afxmac on 2014-06-03
I still do not know why Enigmail uses GCR for GPG password management without asking (appropriate bug report has been opened).

But thanks to some googling I finally found out how to make GCR cache the passphrase for a reasonable time instead of the default which is the whole session.
Using dconf-editor one can set up the following variables:
org.gnome.crypto.cache gpg-cache-method 'idle'  
   (this defaults to session, so the cache-ttl is not used. Only 'idle' and 'timeout' use the configured ttl)
org.gnome.crypto.cache gpg-cache-ttl 1200

They will be active after the next login.

cheers
afx

---

### Post by sudodus on 2014-06-03
I'm still running 12.04 LTS as my production platform, where I have Enigmail.

- Is it the same problem also when you run gpg as a separate program from a terminal window? Or is it only Enigmail?

- What happens if you close Thunderbird and re-open it?

- Can you check if you get the same problem in a system that is 'a fresh install'?

---

### Post by afxmac on 2014-06-03
> **sudodus said:**
> - Is it the same problem also when you run gpg as a separate program from a terminal window? Or is it only Enigmail?
It is only Enigmail. GPG on the commandline works as it should.

> - What happens if you close Thunderbird and re-open it?
Completely irrelevant. Log out / log in does not change it either. 

> - Can you check if you get the same problem in a system that is 'a fresh install'?
No time for a complete install...

cheers
afx

---

### Post by sudodus on 2014-06-03
My last question was to find out if the problem depends on upgrading (instead of making a fresh install).

I'd agree that it is a bug. I hope you can supply the bug report with enough data to keep the debugging guy(s) happy :-)

 Anyway I will subscribe to this thread. If you tell me the bug number, I can also subscribe to the bug report.

---

### Post by afxmac on 2014-06-03
Bug numbers are #1325832 (Enigmail) and  #1325833 (GCR).
But I had marked them as Security bugs so I am not sure whether they are publicly visible.

I do have a fresh install machine at home where I have not been using enigmail so far, but I do not have much time for experiments unfortunately....

cheers
afx

---

### Post by sudodus on 2014-06-03
I checked if the bug reports are available for me, and they are not, but we can communicate via this thread.

---

### Post by afxmac on 2014-06-03
Ok, tried it on the box that was installed from scratch. Exactly the same symptoms.
GCR is used without my consent and the defaults are just incredibly stupid.

cheers
afx

---

### Post by sudodus on 2014-06-04
Thanks for sharing that result. It is probably also valuable for the Launchpad bug reports.

---

### Post by afxmac on 2014-06-04
I've added it it there.
The bug reports have been set to public now by the admins.

cheers
afx

---

