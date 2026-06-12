---
title: "Rosegarden install requires removing Ardour"
date: 2011-02-19
forum: Ubuntu Studio
---

### Post by jmberrueta on 2011-02-19
Hi everyone. I currently have Ardour installed in my machine and I would like to additionaly install Rosegarden. However, when I try to do so it tells me that Ardour needs to be removed (together with a couple of other packages).

Could this have to do with some conflicting dependencies? I've been looking for a solution in the forums but haven't had any luck so far. What I did see is people actually use both programs so... does anyone know what's happening and how can I solve this issue?

Thanks in advance,
Juan

---

### Post by Pablo_F on 2011-02-19
Hi, 

Yes, this is a bit weird, it seems like a jackd1 / jackd2 dependency confusion. Are you running maverick?

Anyway, go ahead with installing rosegarden and then install ardour again. 

Cheers, Pablo

---

### Post by jmberrueta on 2011-02-20
Hey Pablo, that did it.
I appreciate your help, sir.

Juan

---

