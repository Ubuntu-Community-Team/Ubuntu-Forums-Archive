---
title: "Problem with: no valid OpenPGP data found."
date: 2011-10-04
forum: Security
---

### Post by WDYSUN on 2011-10-04
Dear Memebers

I am trying to update my Karmic box and I have serious problems. It seems that the issue is caused by gpg.

If I try to get a new key I get this:

```

gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg: requesting key E084DAB9 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

but I can ping keyserver.ubuntu.com  with no problems. 

Any ideas?

Best 
Pietro

---

### Post by WDYSUN on 2011-10-05
Dear Forumers,


sorry for the previous message... I solved the issue. The problem was caused by the proxy server.

Best
Pietro

---

### Post by gmridul on 2013-01-20
Can you please tell me how did you solved the problem? I am also behind a proxy and have tried various things but I am unable to solve the problem.

---

