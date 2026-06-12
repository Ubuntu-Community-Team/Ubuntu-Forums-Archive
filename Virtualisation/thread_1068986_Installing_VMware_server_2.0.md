---
title: "Installing VMware server 2.0"
date: 2009-02-13
forum: Virtualisation
---

### Post by djfick on 2009-02-13
I am trying to get VMware server 2.0 running on my box, which is running Hardy.  I've come to this spot and I'm worried about continuing as is.  Does anyone have advice?

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no]

What do I need to do to match the compilers?

---

### Post by NetworkGuy on 2009-02-13
Continue.  You should be OK.

---

### Post by djfick on 2009-02-13
So the mismatch isn't that big of a deal?

---

### Post by HermanAB on 2009-02-13
It won't work at all if it is a big deal.  So don't worry about it - just test it once done.

Cheers,

Herman

---

### Post by dcstar on 2009-02-15
> **djfick said:**
> So the mismatch isn't that big of a deal?

Trivial. I have not seen one issue posted that says it doesn't work, the only thing I have ever seen is from one nervous-nellie who was in a panic because his "production" machine was too important to risk by ignoring this message.

---

### Post by HermanAB on 2009-02-16
Hmm, well, maybe you should stop and rather install VMware server 1.x, since 2.x is a POS at best.  Some things should not have a built-in web server.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-02-16
> **dcstar said:**
> Trivial. I have not seen one issue posted that says it doesn't work, the only thing I have ever seen is from one nervous-nellie who was in a panic because his "production" machine was too important to risk by ignoring this message.
 
+1, lets not name call though ("nervous-nellie").

If you search the forums you will find the solution posted (I do not have the exact thread, use search terms such as gcc mismatch and vmware).

---

