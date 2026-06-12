---
title: "Problem with modesecurity Ubuntu 20.04"
date: 2021-03-02
forum: Security
---

### Post by gevensen on 2021-03-02
There is a bug in modsecurity

[https://bugs.launchpad.net/ubuntu/+source/modsecurity-apache/+bug/1916108](https://bugs.launchpad.net/ubuntu/+source/modsecurity-apache/+bug/1916108)

No one is trying to fix

It is an old bug from 18.04

I need to recompile mod security

Where can I find the process needed to recompile

---

### Post by TheFu on 2021-03-02
Google found this project page:
[https://github.com/SpiderLabs/ModSecurity/wiki#wiki-Installation_for_Apache](https://github.com/SpiderLabs/ModSecurity/wiki#wiki-Installation_for_Apache)

The ubuntu instructions are from 2015, so they may be slightly off.  I did look at the dependencies which include the FLOSS versions of lex and yacc.  In theory, the makefile will handle building everything in the correct order.  No reason it shouldn't.

The other method is to pull the source package using apt. Insde it should be a debconf file with the options used by Canonical to build it.

I haven't used modsecurity in a few years and never built it myself. I have used flex ad bison to create language parsers, long ago. If  get stuck, post the steps and output. Hopefully, someone can help.

---

