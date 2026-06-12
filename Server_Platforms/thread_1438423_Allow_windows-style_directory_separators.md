---
title: "Allow windows-style directory separators?"
date: 2010-03-25
forum: Server Platforms
---

### Post by mike-buntu on 2010-03-25
I'm porting an application to a Ubuntu server which contains hard coded windows-style file separators (e.g. "\\examplefile.conf"). Of course, this doesn't work on Linux. Is there any way I can allow it? I'm trying to avoid rebuilding the source code.

Thank you.

---

### Post by diesch on 2010-03-25
No, there's no way to change the directory separators (at least not without patching the kernel).

---

### Post by pbpersson on 2010-03-25
What is the source code written in?  Is this a scripting language or is the code compiled?

Let's say that in your source code you are passing parameters to libraries such as FileOpen, FileRead, etc.......

You COULD create your own local versions of those libraries which change the parameters on the fly and then pass the new parameters to the real libraries.

I know that sounds like a crazy solution, but that is the first idea I had.

---

### Post by HermanAB on 2010-03-25
You have to parameterize all that hard coded cruft - sorry!

---

