---
title: "Cups not in smb.conf, but cups connect errors?"
date: 2008-07-11
forum: Server Platforms
---

### Post by whit on 2008-07-11
I've got a simple Samba setup with a few shares - nothing but file directories. Yet I'm getting errors in the individual users' log files on the server like so:
> [2008/07/11 21:21:30, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refusedWell, that's nice. I'm not running Cups on this server. And with an identical smb.conf on its Gentoo ancestor in the same role, there were none of these errors. There is *no* printer share in smb.conf whatsoever. So where do I turn this off - what's causing Ubuntu's Samba to even attempt to connect to a service it's not configured - at least not in the standard smb.conf way - to share?

---

