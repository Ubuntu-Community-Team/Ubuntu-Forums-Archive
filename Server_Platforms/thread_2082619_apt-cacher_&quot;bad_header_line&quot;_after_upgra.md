---
title: "apt-cacher &quot;bad header line&quot; after upgrade to 12.04"
date: 2012-11-10
forum: Server Platforms
---

### Post by davidmcq on 2012-11-10
I have four servers, one runs apt-cacher and I just upgraded this one to 12.04. I can update/upgrade it through it's own apt-cacher without error.

After the upgrade, I'm getting errors when doing apt-get update on the other machines. 

One is running 10.04 and has these errors:

[INDENT]Err http://<serverIPaddress> lucid-updates Release.gpg
 BAD HEADER FILE
Err http://<serverIPaddress> lucid/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
[/INDENT]
Another is also running 10.04 and has this error: 

[INDENT]W: A error occurred during the signature verification. ... etc[/INDENT]

The third is running 8.04 and has NO errors.

Can anyone suggest how to resolve these? They both happened since the upgrade of the apt-caching machine. Are they local errors or caused by the cache?

---

