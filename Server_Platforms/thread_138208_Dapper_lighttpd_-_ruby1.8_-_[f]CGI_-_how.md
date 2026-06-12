---
title: "Dapper: lighttpd - ruby1.8 - [f]CGI - how?"
date: 2006-03-01
forum: Server Platforms
---

### Post by colo on 2006-03-01
`lo there,

I just ironed Dapper Flight 4 on a spare box to test out some stuff before going "productive" in 2 months or so, and I'm currently trying to get lighttpd run ruby-scripts via its fcgi-interface. The php5-cgi package, for example, installs /usr/lib/cgi-bin/php{,5} and will supposedly work just fine. I've installed numerous Ruby-packages by now, for example "libcgikit-ruby1.8" (Ruby Web Application Framework) and "libfcgi-ruby1.8" (FastCGI library for Ruby) - however, still no /usr/lib/cgi-bin/*ruby*.

What do I need to install to "fix" this?

Tia,
- colo

---

### Post by colo on 2006-03-02
No ideas, anyone?

---

### Post by firecat53 on 2006-03-06
I may be answering the wrong question, and I don't want to insult you :)  Did you check /usr/local/lib?  It's not necessarily added to PATH by default, but a lot a stuff seems to get installed there.

Scott

---

### Post by colo on 2006-03-06
Nope, no luck there as well...

```
root@dapper-srv:/usr/local/lib# ls -lR site_ruby/
site_ruby/:
total 4
drwxrwsr-x 3 root staff 4096 2006-03-01 17:02 1.8

site_ruby/1.8:
total 4
drwxrwsr-x 2 root staff 4096 2006-03-01 17:02 i486-linux

site_ruby/1.8/i486-linux:
total 0
```

Btw, I don't see how you could have possibly insulted me with your question - I appreciate any form of constructive input :)

---

