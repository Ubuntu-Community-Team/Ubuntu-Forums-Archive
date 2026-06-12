---
title: "RCS fails in fwbuilder"
date: 2007-09-18
forum: Server Platforms
---

### Post by Pollywoggy on 2007-09-18
I installed fwbuilder in Kubuntu Feisty and when I open a new project and then try to add it to RCS, I get this error:

Error adding file to RCS
Fatal error during initial RCS checkin of file.
Exit Status 0


I have used fwbuilder in FreeBSD recently and I did not get this type of problem.
Is it a bug?

---

### Post by HermanAB on 2007-09-19
Hmm, RCS is so simple, I have never heard of it not working!

Usually, all you need to do is create a subdirectory called RCS, then check something in with 'ci -u filename'.

My guess is that the RCS subdirectory doesn't exist.

Here is some help: [http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html)

Cheers,

H.

---

### Post by Pollywoggy on 2007-09-19
> **HermanAB said:**
> Hmm, RCS is so simple, I have never heard of it not working!

Usually, all you need to do is create a subdirectory called RCS, then check something in with 'ci -u filename'.

My guess is that the RCS subdirectory doesn't exist.

Here is some help: [http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html)

Cheers,

H.

I did not have the rcs package installed.

thanks, you helped a great deal and it works now.

---

