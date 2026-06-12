---
title: "mod_dir is missing in package apache2-common"
date: 2007-04-10
forum: Server Platforms
---

### Post by Azaron on 2007-04-10
Hi,

I'm having trouble configuring an Apache http server. The *DirectoryIndex* directive isn't working.
After some investigation I found out that the mod_dir module isn't provided by the apache2-common package.

The package I'm talking about is:
Package: apache2-common
Architecture: amd64
Source: apache2
Version: 2.0.55-4ubuntu2
Ubuntu Version: Dapper

The mod_dir module is one of the standard modules for the apache server, and is also provided in the source package.

Does anybody know why the module is missing, or am I getting something totally wrong...

Cheers,

Azaron

---

### Post by Towelie on 2007-05-03
I wondered about this as well.  Apparently, it was compiled into Apache.

```
apache2ctl -l
```

---

### Post by MJN on 2007-05-04
Indeed. Apache 2.0 onwards has mod_dir as a 'base' (pre-compiled) module.
 
What are the symptoms of your problem? Post these with your config and we should have you up-and-running on no time.
 
(The default server-wide DirectoryIndex directive can be found in /etc/apache2/apache2.conf - is this what you've been modifying?)
 
Mathew

---

