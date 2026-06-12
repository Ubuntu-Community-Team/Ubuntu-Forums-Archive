---
title: "32bit guest running 32bit specific code on 64bit host"
date: 2012-01-20
forum: Virtualisation
---

### Post by chuuk on 2012-01-20
Hey guys,

I don't know very much about virtualization and need some help with a question that I haven't been able to find a satisfactory answer on Google for (possibly because it's so trivial). 

I have a cryptographic application that needs to be run on 32bit code.

I was stuck for a bit, then I decided to try virtualisation, as I can't find a 32bit computer within miles of where I am. My question, finally, is: if I install a 32bit Ubuntu guest on my 64bit Ubuntu installation (using VMWare) will this run as a pure 32bit install or will there be some background conversions go on that negate my efforts?

Thanks for the help.

---

### Post by wojox on 2012-01-20
You need the 32 bit libs. In Ubuntu the package is called ia32-libs. To install it, just open a terminal window and type:
```
sudo apt-get update; sudo apt-get install ia32-libs
```
Should run after that.

---

