---
title: "setting up a domain?"
date: 2010-02-28
forum: Server Platforms
---

### Post by bone2006 on 2010-02-28
I have a multifunction printer that if I scan files I can save it to a shared directory.  It's asking for a domain though, which I believe it's referring to a domain controller?

I was wondering if I could just take ubuntu standard edition and install samba and if I could create a domain using Samba?  Or if that's not what I want?

Thanks in advance

---

### Post by Lucky. on 2010-03-01
I wish I knew man, sorry.  I've worked with a few multifunction printers asking for domains.  Sometimes they use it for DNS purposes, sometimes they use it to help authenticate on a domain, and sometimes all they do is add the domain name to the user name that has access to the share.  Sometimes you don't really need them at all.

It really depends on who and how they made it.  Sorry.

Out of my experience, I'd try to eliminate variables.  See if it will scan files to a simple everyone-read/write access Windows XP share on a domain.  If you don't have a domain, leave the domain field empty and see if it will dump it to the Windows XP share anyway.  Once you get that working, then try Ubuntu out with Samba.  It should be a piece of cake.  But trying it with Ubuntu first will leave you wondering "Hmm...do I really need a domain?  Did I configure Samba right? etc."

---

### Post by bone2006 on 2010-03-03
Thanks so much

I just put in the host name of the server and it worked as a shared folder.

---

