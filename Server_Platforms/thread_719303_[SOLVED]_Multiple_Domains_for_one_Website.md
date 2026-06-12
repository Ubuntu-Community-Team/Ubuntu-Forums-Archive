---
title: "[SOLVED] Multiple Domains for one Website"
date: 2008-03-09
forum: Server Platforms
---

### Post by freelinuxhelp on 2008-03-09
If I have domain.com, domain.net and domain.org, is it possible to have them all point to the same web site?

---

### Post by Mr. C. on 2008-03-09
> **freelinuxhelp said:**
> If I have domain.com, domain.net and domain.org, is it possible to have them all point to the same web site?

Yup.

How are they hosted now ?

---

### Post by freelinuxhelp on 2008-03-09
Well, honestly, I haven't registered them yet. Im just wondering if I need to do some apache virtual host trickery or something else.

---

### Post by Mr. C. on 2008-03-09
There's no trickery.

You can use IP-based hosts, virtual hosts, aliases, or a number of mechanisms.  This is all normal operations.

---

### Post by freelinuxhelp on 2008-03-09
But it's all done on the apache side right?
That's really what I needed to know, I guess. I can figure out how to do it, just didn't know if apache was the only place to do it or if i needed to tweak dns somehow(i hate tweaking dns).
Thanks for your help!

---

### Post by Mr. C. on 2008-03-09
DNS gets your visitors to your site (via name -> IP translation).  Apache takes care of serving the files from the site, based upon any properties of the URI (IP, hostname, etc.).  You can have, for example, just a single site, that is served regardless of how user's arrived.

---

### Post by freelinuxhelp on 2008-03-09
perfect. that's exactly what i needed. thanks :-)

---

