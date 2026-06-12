---
title: "libreadline.so.5 undefined symbol problem for apt-get"
date: 2006-10-01
forum: Repositories &amp; Backports
---

### Post by codemaster on 2006-10-01
I recently attempted to modify my repositories (shouldn't have changed anything, but knowing my luck). Anyway, I started to receive these very odd GPG errors durring an apt-get update:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: Unknown error executing gpgv

so, when running gpg at all, I receive this error:

gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: BC

I have attempted reinstalling libreadline, removing libreadline and overwriting the various hardlinks; all without any luck. I've also looked online quite a bit and also found no answers to this problem. ](*,) 

Any help is greatly appreciated.

---

### Post by codemaster on 2006-10-04
I solved the problem to this odd error:

I simply removed all of the libreadline files in /usr/local/lib/ and ran a sudo ldconfig.

Oddly enough, it fixed it and gpg and apt-get update now work properly!

---

### Post by dsipma on 2011-10-09
I just ran into this problem (except the error was libreadline.so.6 and the symbol was UP) and after searching and searching and breaking a few other things, I tried this and it worked like a charm.  Thanks.
Ubuntu 11.10

---

