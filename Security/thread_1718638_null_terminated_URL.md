---
title: "null terminated URL"
date: 2011-03-31
forum: Security
---

### Post by CptSnork on 2011-03-31
Hello, 

I'm still pretty new to everything related to IT but I really want to wrap my head around how to build Domains with Linux and mixing Windows and Linux. So I read a lot and try my luck with virtual machines. I keep coming across "null terminated URL" vulnerabilities...

As far as I understand it's a % sign (sorry for butchering the definition)  in this case.  And I'm trying to find an example of what such a URL would look like. Could somebody nudge me in the right direction or post an example?

Thank you.

---

### Post by kidders on 2011-04-02
Hi there,

Null terminators are pretty commonplace, but software implementing a protocol that doesn't use them could, in theory, mishandle them. HTTP, for example, uses CRLF terminators.

> **CptSnork said:**
> I'm trying to find an example of what such a URL would look like.

They're hard to represent, because a null character doesn't "look" like anything. In unicode, for instance, a null-terminated "http://www.google.ie/" would be ...

```
0x68 0x74 0x74 0x70 0x3a 0x2f 0x2f 0x77
0x77 0x77 0x2e 0x67 0x6f 0x6f 0x67 0x6c
0x65 0x2e 0x69 0x65 0x2f 0x00
```

I hope that helps.

---

