---
title: "Pidgin 2.6.5?"
date: 2010-01-10
forum: The Cafe
---

### Post by Psumi on 2010-01-10
I just got another update to pidgin just now, version 2.6.5 apparently, but there's no changelog, so how do I know what's changed?

did they release it too early or something?

---

### Post by ar0n on 2010-01-10
I'm using gentoo ... And changelog states:

```

*pidgin-2.6.5 (10 Jan 2010)

  10 Jan 2010; Olivier Crête <*@gentoo.org> +pidgin-2.6.5.ebuild:
  Version bump for security bug #299751

```

---

### Post by FuturePilot on 2010-01-10
Assuming you're using the Pidgin PPA you can view the changelog here [https://launchpad.net/~pidgin-developers/+archive/ppa/+packages]("https://launchpad.net/~pidgin-developers/+archive/ppa/+packages")

---

### Post by Psumi on 2010-01-10
```
  * Build new upstream release for the Pidgin PPA
    - debian/control
      + Set Maintainer to Pidgin Developers < devel@pidgin.im>
      + Lower cdbs build-dep to 0.4.51 to allow building on Hardy
```

Not much of an update, but oh well.

---

### Post by ar0n on 2010-01-10
> **Psumi said:**
> Not much of an update, but oh well.

Actually this bug is really serious:
[http://xorl.wordpress.com/2010/01/01/pidgin-msn-slp-emoticon-directory-traversal/](http://xorl.wordpress.com/2010/01/01/pidgin-msn-slp-emoticon-directory-traversal/)

---

