---
title: "Any ideas of how can I uninstall Mixxx - being compiled from source"
date: 2010-01-09
forum: Ubuntu Studio
---

### Post by jocampo on 2010-01-09
Hello folks,

Was dealing with mixxx on a virtual machine and I was able to install it from source following this instructions:

[http://mixxx.org/wiki/doku.php/compiling_on_linux]("http://mixxx.org/wiki/doku.php/compiling_on_linux")

But  removing it was a nightmare to me I was not able to. In fact, I used to use MAKE for install/uninstall from source, this time I used scons; so before doing the real stuff on my real machine, I would like to learn how to reverse the process. I am not a nobbie in Linux but not an expert either so this way to compile and install mixxx is kind of new.

Has anyone uninstall mixxx after being compiled from source?

Thanks,

ps: not sure if this will help, I have Ubuntu Studio Karmic and was dealing with mixxx 1.7

---

### Post by AutoStatic on 2010-01-09
**scons uninstall** from the directory from which you compiled it?

---

### Post by jocampo on 2010-01-09
> **AutoStatic said:**
> **scons uninstall** from the directory from which you compiled it?

Thank you sir! ;) 

I'll try that later, hopefully will work ...

---

