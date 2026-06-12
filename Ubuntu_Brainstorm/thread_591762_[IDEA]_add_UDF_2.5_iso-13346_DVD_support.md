---
title: "[IDEA] add UDF 2.5 iso-13346 DVD support"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by SonicSteve on 2007-10-25
I suggested this idea for Gutsy 7.10 and I don't believe it was added. So here goes again.

We need tp add support for UDF volume DVD's. I fear to mention that this is a format that Vista is using but... it is. People are burning DVD's on Vista and having problems reading them on Ubuntu. 
Here is proof
[http://ubuntuforums.org/showthread.php?p=3632852#post3632852](http://ubuntuforums.org/showthread.php?p=3632852#post3632852)

This is sourceforge link.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295)

More and more people will be coming with DVD's burned from Vista, and expecting them to work. It's already happening, just search our own forum. Then search google, the problem is growing. This needs to be compiled into the standard Ubuntu kernel especially since this next Ubuntu will be LTS.

---

### Post by Kow on 2007-10-25
[http://sourceforge.net/tracker/index.php?func=detail&aid=1795804&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1795804&group_id=295&atid=300295)
for reference, probably want to verify the code as it was submitted by "anonymous". Comments to the patch are positive (all 2 comments).

---

### Post by SonicSteve on 2007-10-25
> **Kow said:**
> [http://sourceforge.net/tracker/index.php?func=detail&aid=1795804&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1795804&group_id=295&atid=300295)
for reference, probably want to verify the code as it was submitted by "anonymous". Comments to the patch are positive (all 2 comments).

Exactly how do you verify code? I'm not very good at compiling myself yet so that's not much of an option. I do have one sure fire method of testing though. I have a Vista DVD that gives me the UDF volume message. I just need someone to help me compile. I have a system to do this on but I need help.

---

### Post by SonicSteve on 2007-10-26
Here is a better source for the patch, depending on which kernel Hardy will use and you are currently using. IE. the patch needs to match the kernel.
[http://sourceforge.net/tracker/?group_id=295&atid=300295](http://sourceforge.net/tracker/?group_id=295&atid=300295)

---

### Post by SonicSteve on 2008-02-27
This keeps happening, more than once I've been given a DVD burned with Vista. We need to get this added to our Kernel. Search our forums, this problem isn't going away. It would be great if someone involved with development would take this on. I would love to but I'm not a programmer.

---

### Post by dalonso on 2008-03-08
Please, look this thread in order to avoid building your own kernel:

[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)

It's a temporary hack until all necessary udf 2.5 patches get into the hardy kernel.

Best regards.

---

### Post by SonicSteve on 2008-03-09
I'll give this a try later in the week.

---

