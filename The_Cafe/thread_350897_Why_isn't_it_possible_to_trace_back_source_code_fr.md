---
title: "Why isn't it possible to trace back source code from a binary?"
date: 2007-02-01
forum: The Cafe
---

### Post by miceagol on 2007-02-01
Just read [this article]("http://news.bbc.co.uk/2/hi/technology/5271386.stm"), and started wondering why one cannot get back to the source code from a binary (compiled) file? What does it then mean to do "back engineering", like e.g. the alsa developers has to do to make drivers for a sound card with unreleased specs? Am I talking about two different things here? Just curious. :KS

---

### Post by GeneralZod on 2007-02-01
You can get some kind of source code back from a compiled binary, but it will be stripped of function, method, class, variable etc names and comments, and so largely worthless.  I'm not sure to what degree obfuscation techniques inhibit obtaining even this poor level of source, but I'm betting they don't help :)

---

### Post by mips on 2007-02-01
It's possible but frigging hard to read because of things mentioned above.

---

### Post by prizrak on 2007-02-01
What the other two said. There is also usually certain protection measures undertaken to inhibit the ability to decompile a binary.

---

### Post by G Morgan on 2007-02-01
You can disassemble code quite easily but you will get totally undocumented code in ASM.

Note that a compilation does not go source code -> machine code but takes many steps along the way.

With GCC you go source to generic, generic to ASM, then assemble the ASM to machine code.

Each of these steps break down into further steps. Source to generic would require lexical analysis, syntax analysis and semantic analysis.

In the end >10 steps are involved and we can reverse only the last step.

---

