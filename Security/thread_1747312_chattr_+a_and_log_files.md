---
title: "chattr +a and log files"
date: 2011-05-02
forum: Security
---

### Post by CandidMan on 2011-05-02
This is just of curiosity, no real urgency but I was wondering about the chattr +a attricbute and the similar chflg (??) attribute on OpenBSD. Specifically making the attribute of a file appendable only.

I was wondering if it was possible for someone to do an 'Indiana Jones' ? If they had access to say a logfile with this attribute, and like Indie(at the stone plinth) swap a portion of the file with their own data. This would technically append to the file whilst deleting what they wanted

This might be relevant to anyone who has or wants a server reachable outside their home network

This is assuming of course the cracker doesn't have root access and doesn't consider file attributes

---

### Post by bodhi.zazen on 2011-05-02
See [http://manpages.ubuntu.com/manpages/natty/en/man1/chattr.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/chattr.1.html)

It might help, depending on the skill of the intruder. If they have root access it would be trivial to reset.

---

### Post by CandidMan on 2011-05-02
Thanks for the link. But I think I'll have to do some of my own quick tests to be sure. 
My thinking was that if you can get around  the attribute simply by ensuring a file becomes larger than the original, then it would invalidate the 'appendable'.

Of course I mean if this were applied to a non-root file/directory and a non-root process was editing said file.

---

### Post by bodhi.zazen on 2011-05-02
I would not rely on setting the attribute as a method of increasing security in general.

---

### Post by CandidMan on 2011-05-02
Okay, thanks, will bear that in mind. 
Done some quick tests opening a text file in vi and I couldn't edit it. Appending output from stdin with ">>" did work. So I guess chattr isn't foolproof, but neither is it trivial to edit a file with the +a attribute.

---

