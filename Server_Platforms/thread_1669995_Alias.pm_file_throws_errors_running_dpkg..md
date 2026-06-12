---
title: "Alias.pm file throws errors running dpkg."
date: 2011-01-18
forum: Server Platforms
---

### Post by plr4ever on 2011-01-18
I've been trying to get an SQL database up and running, but before I could even get started, I encountered an error when running dpkg:

```

Variable "$Alias" is not imported at /usr/lib/perl/5.10/Encode/Alias.pm line 26.
Bareword found where operator expected at /usr/lib/perl/5.10/Encode/Alias.pm line 26, near "$Alias find"
        (Missing operator before find?)

```

This error prints twice when I run dpkg-reconfigure. I don't anything about perl, and seeing as this error "appeared" sometime around christmas, I'm doubtful that I screwed something up this time. However, anything is possible.

Any ideas?

Also, is there anyway I can get a more comprehensive record of who logged in to the server? I've run "last" but it won't give me any login info before January 4th.

Thanks!

---

