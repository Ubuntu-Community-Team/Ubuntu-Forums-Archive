---
title: "Latest mono from code..."
date: 2009-06-12
forum: Ubuntu Dev Link Forum
---

### Post by kepeter on 2009-06-12
Hi,

Lately I checking the mono environment to extend my possible customer base (I have some .NET app developed on Windows).
After looking around choose Ubuntu as the OS to test on, but found out that the packaged mono is a bit old - i always like to experience the new stuff...
So I decided to install mono from source code...
I searched the web for solutions but didn't found something complete (and working).
It took me some time (I learned about UNIX some 25 years ago at school and since then my paths lead to Windows...) to build install scripts but today I have them and I want to post it here to help those interesting doing the same...

The install process made up by 3 scripts:
1. install-mono.sh - it installs the mono runtime environment with all dependencies.
2. install-monodevelop.sh - it installs the IDE with all dependencies.
3. install-mozilla.sh - it installs the mozilla-dev package.

The third script is somehow interesting, because I can not explain why I need it, and because I MUST be installed after the two others(?!).

I made and run these scripts on Ubuntu 9.04 using mono 2.4 and monodevelop 2.0, however it seems to me easy to convert them to other Ubuntu (or any Linux?) and other mono versions...

I hope this post will help someone... ever...

Peter

---

### Post by jimv on 2009-06-12
Launchpad PPA repository is your friend:

[https://launchpad.net/~mono-edge/+archive/ppa](https://launchpad.net/~mono-edge/+archive/ppa)

Add that to your sources list and install Mono.

---

### Post by SKLP on 2009-06-12
For mono 2.4: [https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

---

