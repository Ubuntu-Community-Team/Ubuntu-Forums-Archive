---
title: "Permissions in running cgi script 'nph-proxy.cgi'"
date: 2009-11-01
forum: Server Platforms
---

### Post by anandamide on 2009-11-01
Hey guys
I've been trying to get this script working all day to no avail. I'm very new apache so this could be a real simple issue but I'm not getting anywhere.

Trying to access [http://myhost/cgi-bin/nph-proxy.cgi](http://myhost/cgi-bin/nph-proxy.cgi) gives me a blank screen. The Apache error log reads:

```
[error] (13)Permission denied: exec of '/usr/lib/cgi-bin/nph-proxy.cgi' failed

```


I have nph-proxy.cgi in /usr/lib/cgi-bin/nph-proxy.cgi. namei -m for this path gives:

```
 drwxr-xr-x /
 drwxr-xr-x usr
 drwxr-xr-x lib
 drwxr-xr-x cgi-bin
 -rwxr-xr-x nph-proxy.cgi

```

A simple perl script in the same location runs no problem. Changing the extension to .pl results in firefox asking me if I want to save or open (with gedit) nph-proxy.cgi.

Any ideas?

---

