---
title: "64 bit?"
date: 2006-06-26
forum: Sun Sparc Users
---

### Post by phignuton on 2006-06-26
<de-lurk>

Can anyone shed some light on the progress getting pure 64 bit libs for the niagara platform? I've been trying to get a sizeable list of open source apps to compile in a 64 bit kind of way, but they continue to fail linking as the libs are 32 bit. Am I perhaps missing a repository of straight 64 bit sources or something?

Sorry if this is just static... I'm overjoyed by the support of the platform in general, I would just like to take full advantage of it...

</de-lurk>

---

### Post by hw-tph on 2006-06-26
As far as I know, Debian (and hence Ubuntu) have traditionally shipped all 64bit SPARC software as 32bit, but with a 64bit kernel. Translation between 32bit software and the 64bit hardware is handled in the kernel, and using 64bit software (libraries, executables) is supposed to often be *slower* than using 32bit apps with the 64bit kernel. Search the [mailing list archives](http://marc.theaimsgroup.com) for more detailed explanations.

OpenBSD on the other hand (I suppose the other BSD's as well) provide a full 64bit environment, for good or for worse. Both Debian and OpenBSD run very well on my aging Ultra10.


Håkan

---

### Post by joga on 2006-06-27
Try to install the packages libc6-sparc64 and libc6-dev-sparc64.

This at least allows you to build simple applications as 64bit binaries (using the -m64 compiler switch).

Unfortunately, 64bit versions of other libraries, e.g. libpthread, seem to be missing.

---

