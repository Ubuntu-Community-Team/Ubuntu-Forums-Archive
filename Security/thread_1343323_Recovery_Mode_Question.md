---
title: "Recovery Mode Question"
date: 2009-12-01
forum: Security
---

### Post by pEdRiDeR2008 on 2009-12-01
I'm kind of a newb when it comes to linux, but I try my best.  So here goes.  

About six months ago I switched my parents over to Ubuntu 9.04 on their computer from XP after a nasty bit of virus infestation and it was the simplest OS install I have ever done and they have had zero problems with it since then.  

Now because of that lack of problems, I forgot what I set the root password as and I needed to install a package for them in Synaptic but cannot remember the password.  I was reading that you can boot into recovery mode from GRUB and then drop into a root prompt right from there and change it in /etc/passwd.  I did that but couldn't figure out what to change so I left it and came here.  

Two Questions:

Can I actually change it from there and if so how?  It just seems a bit of a security hole to me for someone to be able to do that.  I mean, getting a root prompt with no password that easy seems absurd.  But I'm just a newb looking for answers.  Thanks.

---

### Post by pEdRiDeR2008 on 2009-12-01
So I was browsing a few threads here and answered the question about physical access.  But why is it that physical = root access?  That just seems kind of silly to me.  There has to be a good reason.

---

### Post by bodhi.zazen on 2009-12-01
> **pEdRiDeR2008 said:**
> So I was browsing a few threads here and answered the question about physical access.  But why is it that physical = root access?  That just seems kind of silly to me.  There has to be a good reason.

Physical access = root access because you can boot the machine with a live CD or remove the hard drive or boot to recovery mode or <insert a number of less savory techniques here>.

---

