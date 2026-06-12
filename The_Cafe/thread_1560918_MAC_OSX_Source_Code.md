---
title: "MAC OSX Source Code"
date: 2010-08-25
forum: The Cafe
---

### Post by Sporkman on 2010-08-25
...is here:

[http://www.opensource.apple.com/](http://www.opensource.apple.com/)

The kernel source is under the xnu folder.

I did not know they published all this.

Here is some more stuff:

[http://www.apple.com/opensource/](http://www.apple.com/opensource/)

---

### Post by dv3500ea on 2010-08-25
Yep, OSX is built on top of BSD [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)").

---

### Post by Sporkman on 2010-08-25
> **dv3500ea said:**
> Yep, OSX is built on top of BSD [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)").

Right, but they are not required to publish the source code under the BSD license. Yet there it is...

---

### Post by NMFTM on 2010-08-25
Questions:

1) Would it be legal to release the source code of an application you built but release it in such a way that would make it hard for someone to actually utilize it? Such as removing all of the comment sections from the source code version while they remain present (but, unreadable) in the binary version? Or does the source code have to be release exactly as it was before it was compiled to form the binary? Do compilers even keep the comments in the code after they've been compiled? Because, even if they did they'd probably be unreadable Or are they removed?

2) If it's possible to convert say C++ to the binary code that computers actually run. Why is it also not possible to do the reverse and translate binary code into C++? Or is it like the one way hashing that public key encryption uses in that it may be possible, but it's so hard that it's de-facto impossible?

3) Even though almost nobody actually programs in binary since even assembly language is sufficiently low enough on the abstraction level for even the most low level purposes, such as writing BIOS firmware. What if someone did program an application completely in binary. Technically the binary would be exactly the same a the source code version. But, licenses like the GPL state that you have to make available the source code to anyone you distribute the binary to. How would that work?

---

### Post by dv3500ea on 2010-08-25
1) This is not illegal, as far as I know, just unethical. Comments are ignored by the compiler..

2) You can decompile binary code to assembly but decompiling it to C would produce different code to the original because different higher level features can be compiled to low level assembly. eg. while and for loops compile to the same basic looping construct in assembly (usually some sort of GOTO).

3) This person would be insane.

---

### Post by whiskeylover on 2010-08-25
> **NMFTM said:**
> Questions:

1) Would it be legal to release the source code of an application you built but release it in such a way that would make it hard for someone to actually utilize it? Such as removing all of the comment sections from the source code version while they remain present (but, unreadable) in the binary version? Or does the source code have to be release exactly as it was before it was compiled to form the binary? Do compilers even keep the comments in the code after they've been compiled? Because, even if they did they'd probably be unreadable Or are they removed?

2) If it's possible to convert say C++ to the binary code that computers actually run. Why is it also not possible to do the reverse and translate binary code into C++? Or is it like the one way hashing that public key encryption uses in that it may be possible, but it's so hard that it's de-facto impossible?

3) Even though almost nobody actually programs in binary since even assembly language is sufficiently low enough on the abstraction level for even the most low level purposes, such as writing BIOS firmware. What if someone did program an application completely in binary. Technically the binary would be exactly the same a the source code version. But, licenses like the GPL state that you have to make available the source code to anyone you distribute the binary to. How would that work?

1) Code cannot be kept in the binary. If the binary is compiled in debug  mode, it has information that maps it to individual lines of code in  the source file. But no comments are kept in the binary. I suggest  reading a book on Computer Architecture.


2) C++ conversion to binary code is what the compilers do. The computers ONLY run binary code (unless you're talking about scripting languages, in which case the computers still run the interpreter in binary.) I suggest a book on Compiler Design.

3) Assembly to Binary is a 1:1 mapping. Instead of typing codes in hex (0x5f63 0x44ab ...) you write it in assembly which is easier to read (MOV a b, JMP c ...)

---

### Post by Bachstelze on 2010-08-25
1) Depends on the license.  Some licenses like the GPL forbid code obfuscation.  If someone complains, that will go to court, and they could very well win.

2) What dv3500ea said.

3) What dv3500ea, and also, even if writing such a program were possible, it would be silly to release it under the GPL (and even if you really want to release it under the GPL, as th copyright owner, you wouldn't be bound by its terms).

---

### Post by juancarlospaco on 2010-08-25
I think that copyright holder can change copyright, so GPL can become into other licenses.
*Im wrong?*

---

### Post by Bachstelze on 2010-08-25
> **juancarlospaco said:**
> I think that copyright holder can change copyright, so GPL can become into other licenses.
*Im wrong?*

Yes and no. The copyright owner of a piece of BSD software can say "well from now on, the code is GPL", but the versions already released under the BSD license will stay under the BSD license.

---

### Post by Bachstelze on 2010-08-25
Also

> **dv3500ea said:**
> Yep, OSX is built on top of BSD [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)").

Darwin is not BSD. It contains some BSD software, but also some GNU software. Its default shell is Bash, for example.

---

### Post by Sporkman on 2010-08-25
I was impressed with how Apple openly published all that code, and even describe how to compile the kernel, for example.

---

### Post by mcduck on 2010-08-25
> **Sporkman said:**
> Right, but they are not required to publish the source code under the BSD license. Yet there it is...

It's just the Darwin that open-source, so no OS X for free, not even by compiling from the sources. :D

Honestly, there's not much use for Darwin alone. You only get the basic CLI system, with far less software available than on any other BSD or Linux distribution, so there's hardly any reason to run it.

Apple does contribute to other open-source projects, though, for example they are the main developer of the CUPS printing server that is also used in Ubuntu (and pretty much every other Linux & BSD distribution as well).

---

