---
title: "Waste Server Startup script"
date: 2005-12-20
forum: Server Platforms
---

### Post by livet0ski on 2005-12-20
Hey everyone,
I have a quick question. I have a server the I want to start at startup. I'm guessing that I would put a symlink in /etc/init.d/ and then have it run at startup, the only problem is that this server requires a password right after startup. There no options to put the password in at startup of the server, but about 2 seconds after startup, it asks for a password. I obviously know the password, but I'm trying to make it so i can just turn on my Ubuntu box and leave it. How would I do this, i'm no expert at scripts.
Thanks,
Pat

---

### Post by cactus on 2005-12-20
using 'expect' perhaps?
[http://expect.nist.gov/](http://expect.nist.gov/)
[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

---

### Post by livet0ski on 2005-12-24
hmm let me check this out... thanks

---

### Post by harisund on 2005-12-24
what kind of a server? Apache2 mysql etc that I know automatically startup. Could you please be a bit more specific here?

---

