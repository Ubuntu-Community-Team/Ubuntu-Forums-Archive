---
title: "Using limits.conf"
date: 2009-10-05
forum: Server Platforms
---

### Post by mikko.ohtamaa on 2009-10-05
Hi,

I am trying to limit Apache not to bring down my server using ulimit. Apache has some buggy plug-ins which leak memory. When the server runs out of memory (all eaten by Apache) I cannot access it anymore using SSH.

I could prevent this possible problem using ulimit and forcing hard memory limit to Apache. If Apache goes haywire, only Apache dies, not the whole server.

Ubuntu has limits.conf:

[http://ss64.com/bash/limits.conf.html](http://ss64.com/bash/limits.conf.html)

Which is related to 

/etc/security/pam.d and various logins. limits.conf login gets loaded only when 

```

session     required      /lib/security/pam_limits.so

```

is in corresponding pam.d config?

Now my question is

1) What kind of login is /etc/init.d/apache2 session?

2) Can I enforce limits.conf for /etc/init.d/apache2?

3) Do you suggest alternative means to set ulimit for apache? I'd rather **not** poke the init.d script.

Cheers,
Mikko

---

