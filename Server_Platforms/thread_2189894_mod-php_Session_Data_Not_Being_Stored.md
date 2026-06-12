---
title: "mod-php Session Data Not Being Stored"
date: 2013-11-24
forum: Server Platforms
---

### Post by von Corax on 2013-11-24
I'm running stock apt installs of apache2 and mod-php5 on Precise, and my PHP sessions (using session handler "file") aren't working. I can see the PHP session cookie, and I see a PHP session data file whose name matches the SID in the cookie, but it appears that whatever I store in $_SESSION never makes it into the session file (filesize remains at 0 bytes), and when I try to read $_SESSION it's empty.

I would appreciate any suggestions as to where I should start looking for the cause, as any time I've installed this stack on another OS, PHP sessions have simply worked straight out of the box.

TIA,
von Corax

EDIT: Never mind, I figured it out. #-o

---

