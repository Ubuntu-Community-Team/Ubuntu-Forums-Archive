---
title: "Messed up my privileges"
date: 2008-04-21
forum: Security Discussions
---

### Post by rocksocke on 2008-04-21
Hi!

i'm not sure if this is the right forum, but i hope so.

ok - this is a nono, but i unfortunately executed

```

sudo bash
cd /var/www
chown -R root:root .*

```

this leaded my system to be totally owned by root :( - my intent was to own all hidden files... (yes - i now know that this was wrong because of ..)
i'm frightened i messed up all my lamp-installation and my users (in fact only one)

is there a way to correct this, other than reinstall?

thanks.

---

### Post by HermanAB on 2008-04-21
Everybody sooner or later make this kind of recursive mistake, but you typically only make it once in a lifetime - welcome to the club...

Fixing it is not worth the effort.  It is far quicker to re-install.

Cheers,

Herman

---

### Post by rocksocke on 2008-04-21
:/ isnt there anything like 
```

fixpriviliges

```

:( definitifely s.t. which would be worth to be written.. same for

```

chkpriviliges

```

e.g. for intrusion detection.. :/


EDIT: tried to fix it instead of reinstalling. needed 40 mins for now - i manually compared it with my local installation and re-owned the files to the right users. i hope this works (it should)

---

