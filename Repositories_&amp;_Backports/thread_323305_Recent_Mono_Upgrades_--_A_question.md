---
title: "Recent Mono Upgrades -- A question"
date: 2006-12-21
forum: Repositories &amp; Backports
---

### Post by droth6666 on 2006-12-21
Hi all,

Considering what I've been reading about the Novell/Microsoft deal recently, I noticed a bunch of Mono upgrades today [Dapper], and am a bit concerned.   I really don't want to use any Novell code from this point on if it turns out to be at all avoidable.

Is there any way to know who the contributor is for upgrades?  I really don't want to accept anything from Novell since this deal, and since the Mono project seems to be mainly their's, it seems like upgrades are probably from them as well.

Any ideas how I can tell?

Thanks

---

### Post by bapoumba on 2006-12-22
Hi,
I really do not wish to go to a mono discussion. Just look at the package informations, and you'll find the answer to your question ;)
```
:~ $ aptitude show mono
Package: mono
State: not installed
Version: 1.1.17.1-1ubuntu7.1
Priority: optional
Section: interpreters
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 24.6k
Depends: mono-common (= 1.1.17.1-1ubuntu7.1), mono-jit (= 1.1.17.1-1ubuntu7.1)
Recommends: libgdiplus, libmono-corlib1.0-cil
Description: Mono CLI (.NET) runtime
 Mono is a platform for running and developing applications based on the
 ECMA/ISO Standards. Mono is an open source effort led by Novell. Mono provides
 a complete CLR (Common Language Runtime) including compiler and runtime, which
 can produce and execute CIL (Common Intermediate Language) bytecode (aka
 assemblies), and a class library. 
 
 mono is a metapackage containing dependencies for the runtime of Mono. If you
 do not need all of them (or try to work around X11 dependencies), install the
 core packages manually: mono-jit, mono-mcs or mono-utils.

```

---

### Post by droth6666 on 2006-12-22
Thanks, that's what I needed to know!:)

---

