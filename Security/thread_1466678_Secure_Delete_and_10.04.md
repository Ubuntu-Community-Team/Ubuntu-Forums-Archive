---
title: "Secure Delete and 10.04"
date: 2010-04-30
forum: Security
---

### Post by Greymatter on 2010-04-30
Thank you for any help you can offer. I'm not a veteran of Ubuntu.

I installed Secure Delete on 10.04 using sudo. It installed and I ran smem at the command line and it said smem hasn't been installed. In 9.10 smem was part of secure delete. Is it now something different? I don't want to install smem is it means something different in 10.04.

On the other hand if they have to be installed separate is that ok?

---

### Post by Greymatter on 2010-04-30
I installed smem and it is not part of secure delete. It shows the following:

PID User     Command                         Swap      USS      PSS      RSS

Under each is information. smem -v is not accepted as running smem to overwrite memory and adding the verbose tag, -v, was said not to be a legitimate command.

FYI.

---

### Post by bodhi.zazen on 2010-04-30
Did you try the man page ?

[http://manpages.ubuntu.com/manpages/lucid/en/man8/smem.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/smem.8.html)

What is it you are wanting to know or do exactly ?

---

### Post by Greymatter on 2010-04-30
Thank you for the response. I admire the time you put in to help those with security issues. Your guide has been an excellent learning tool.

In 9.10 I used smem -v to erase traces of memory. It comes with the secure delete package.

In 10.04 smem does something different, at least than what it did with 9.10.   [http://manpages.ubuntu.com/manpages/karmic/en/man1/smem.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/smem.1.html)

I've installed secure delete and in the command line I put: smem -v (V because I like the verbose)

It would delete traces of memory (I'm not sure if that is the correct nomenclature) in 9.10.
 Now it no longer does it.

In 10.04 what has replaced smem for secure delete?

---

### Post by bodhi.zazen on 2010-04-30
To me it appears the same basic functionality is there, it is just that you are missing the verbose output.

Honestly I would run it with the -l option and IMO the Gutmann theory has been debunked, at least on hard drives.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

With RAM they would need almost instant access and, although I do not know, I doubt this command is any more secure then simply turning your computer off.

If somebody has physical access you really need to use encryption.

---

### Post by Greymatter on 2010-04-30
> **bodhi.zazen said:**
> To me it appears the same basic functionality is there, it is just that you are missing the verbose output.

Honestly I would run it with the -l option and IMO the Gutmann theory has been debunked, at least on hard drives.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

With RAM they would need almost instant access and, although I do not know, I doubt this command is any more secure then simply turning your computer off.

If somebody has physical access you really need to use encryption.

Understood.

For those who, like me, used the command smem in 9.10 and watched from the command line as the memory was wiped (little ***would pop up until it was completed), it is a change in 10.04. The differences are in the manual should anyone else have a question. I'm sure they will because I got the information from others who also used it.

Thank you for your help.

**UPDATE:** If you use SRM and wish to delete the memory traces the command is now "sdmem" instead of "smem"

---

### Post by cosimo on 2010-08-01
Hey guys,
  yes in the new secure-delete  the command is now  sudo sdmem -ll -v
I was confused about this myself :)

coz

---

