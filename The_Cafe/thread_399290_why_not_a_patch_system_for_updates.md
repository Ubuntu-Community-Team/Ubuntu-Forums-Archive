---
title: "why not a patch system for updates?"
date: 2007-04-02
forum: The Cafe
---

### Post by handaxe on 2007-04-02
Towards furthering my Linux eduction, will someone please explain why Ubuntu (Linux?) does not employ a patch approach to updates?

In other words, why the download of the entire package, when undoubtedly just a part of it was changed  to provide the fix. Same could be asked about upgrades too.

Is it an ease of use issue, or rooted in fundamentals?

Searched the forums but did not spot an answer - link please if I missed it.

Thanks,

HA

---

### Post by 23meg on 2007-04-02
Patches are applied to source code. Since Ubuntu distributes packages in binary form, the whole compiled binaries have to be replaced. What you ask for can be accomplished in source based distributions where you download the source packages and compile locally.

---

### Post by use a name on 2007-04-02
Indeed, with open source, binary patches are undoable, as there will be a whole lot of different versions in use.

With the use of the repositories, new installs will be the latest version, and will allow people to 'patch'.

---

### Post by handaxe on 2007-04-02
Thanks.  I realise that Linux patches are applied to source but was wondering why not for binaries. So, it is a Linux policy not to patch binaries?

I suppose another way of examining this, is to contrast the Windoze and Linux approaches to updates. Do they do this differently?

HA

---

### Post by mac.ryan on 2007-04-02
If by "windows patching" you refer to the practice of replacing just some files of an entire package rather than all its installation, one of the reasons for which GNU/Linux is different is that the latter is much more modular.

Indeed packages in GNU/linux "recycle" bits of the system much more than under windows (this is also why - generally speaking - GNU/linux installations are more compact than windows ones).

For what concerns "patching" this means that many "packages" you upgrade/update are not fully functional programs but just "bits" of them. So, as a matter of facts, the underpinning concept is the same, but while under linux you "update libraryX" under windows you "patch the program X downloading a new file that replaces its library Y".

---

### Post by GeneralZod on 2007-04-02
I'm pretty sure that SUSE has used binary-diff style patching for some time, and I'm sure there's some kind of Ubuntu spec for it, too.

---

### Post by handaxe on 2007-04-02
Thanks all,

My interest in this was sparked by a Firefox update the other day.  I just checked the deb - 8.8 megs worth - a full Firefox install methinks (including icons!). At least 7 other debs came down with it (allied libs etc). That's a lot for a security fix.. or so it seemed.

"Binary-diff" style patching: is that in effect injecting code into a binary to replace a part?

If so, that is very much what I was alluding to. I seem to remember some Windoze proggies doing that from back when I used Redmond -stuff.

Tnx again,

HA

---

