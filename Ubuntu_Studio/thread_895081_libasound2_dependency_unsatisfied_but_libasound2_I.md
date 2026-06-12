---
title: "libasound2 dependency unsatisfied but libasound2 IS already installed"
date: 2008-08-19
forum: Ubuntu Studio
---

### Post by albesan on 2008-08-19
hello team,

I'm trying to install pure data extended on ubuntu feisty and I can't.
I get this dependency error with libasound2 but it is already installed.

I tried reinstalling without success.

Any body has any idea on how to go about solving this kind of issue?

Thanks

a.

---

### Post by Ubuntiac on 2008-08-20
Check the version of libasound2 installed versus the version required by pure data extended. Sometimes two different programs will depend on a package, but one will need an older version and one will need a newer version making for an impossible situation.

In Kubuntu you can open Adept Manager and click on "Details" to see both version number and dependencies of packages. I'm sure Synaptic would have the same kind of thing.

---

### Post by albesan on 2008-09-01
Thanks for the reply.
I gave up and installed ubuntu studio 8.04, then installed PD extended and I can use it but sound comes and goes as it wants, so not trusting it for live performance.
do you use PD at all?

thanks again.

a.

---

### Post by Stochastic on 2008-09-01
> **albesan said:**
> sound comes and goes as it wants, so not trusting it for live performance.

Are you running it with the sound pointed to ALSA or Jack?  Jack should be what you use in a production situation.

---

