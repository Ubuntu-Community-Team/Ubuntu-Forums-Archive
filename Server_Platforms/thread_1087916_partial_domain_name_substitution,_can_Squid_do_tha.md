---
title: "partial domain name substitution, can Squid do that?"
date: 2009-03-05
forum: Server Platforms
---

### Post by PryGuy on 2009-03-05
Good day all of you!
I have a question, I have downloaded Ubuntu repository with apt-mirror and put it on server, the question is: is it possible to make Squid replace a part of the address? For instance Squid gets [http://archive.ubuntu.com/ubuntu/dists/intrepid/](http://archive.ubuntu.com/ubuntu/dists/intrepid/) it replaces it with [http://192.168.0.1/ubuntu/dists/intrepid/](http://192.168.0.1/ubuntu/dists/intrepid/). So it only changes 'archive.ubuntu.com' to '192.168.0.1' leaving all else unchanged. Or it is better to do the substitution somewhere else? Thank you in advance!

---

### Post by netztier on 2009-03-05
> **PryGuy said:**
>  Or it is better to do the substitution somewhere else? Thank you in advance!

If you are absolutely positive that you have mirrored *all* content (source archives and all architectures) included of archive.ubuntu.com, you can set up your local DNS server to be pseudo-authoritative for archive.ubuntu.com and add an A-Record to archive.ubuntu.com pointing to your IP address. However, for any client using that DNS to resolve names, *.archive.ubuntu.com will become unreachable.

I did such a "DNS hijacking job" once,  for *ch.archive.ubuntu.com *at an Ubuntu release party where we didn't have all too much bandwidth - it worked, sort of. It's an alternative, even if it's a crude one. Clever URL-Rewriting might be the better approach, as it wouldn't harm reachability of other hosts in *.archive.ubuntu.com.

regards

Marc

---

### Post by PryGuy on 2009-03-07
Thank you, will try it out!

---

