---
title: "Newb requests help building Qtractor 0.5.8"
date: 2013-05-29
forum: Ubuntu Studio
---

### Post by bachmaninoff on 2013-05-29
Apologize if this was covered elsewhere, I'm on some seriously sub-dialup speed now...  Being humbled by not being able to compile this source, qtractor-0.5.8.tar.gz.  Downloaded from Sourceforge.

I've downloaded and extracted the tarball:
tar xvzf qtractor-0.5.8

Changed directory:
cd qtractor-0.5.8/

Attempted configure:
./configure

Get an error:
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See 'config.log' for more details

The config.log seems kinda long to post here.  Is there a specific section that I should post?

Edit:
Typing 'ls -l /lib/cpp' produces:
lrwxrwxrwx 1 root root 21 Apr  5 10:22 /lib/cpp -> /etc/alternatives/cpp

---

### Post by jejeman on 2013-05-29
Why not use package from kxstudio ? It is the same version.

---

### Post by bachmaninoff on 2013-05-30
> **jejeman said:**
> Why not use package from kxstudio ? It is the same version.

No access to internet other than simple webbrowsing - unable to download anything.  Was hoping to use the tools I have, which apparently are not configured correctly or not adequate.  Thanks for the reply though!

---

### Post by jejeman on 2013-05-30
Well, if you can not download anything you can not compile eather. You need to satisfy build dependecies, install build tools and that means downloading...
Download qtractor package from kxstudio ppa on some other computer and pray that you have all dependecies. Use gdebi for install, it will tell you if you have all you need.

---

### Post by bachmaninoff on 2013-05-30
Well thanks for the response!  Bummer though...  EDIT:  Ah, I think I see where I went wrong.  I fired up Synaptic package manager and listed all compilers on my system...  I have GCC, GCC-4.7 and FPC.  I do not have G++, though I do have stdlibc++6.  I was also mistaken that the gcc on my system also compiles c++, apparently it does not, even though it has flags to allow c++ syntax.  Lesson learned!  Now if I could just compile G++ from GCC or FPC...  Silly as it may sound, it would be cool if there was a webpage that just listed the code without having to download.  It would take forever, but I have some extra time in the middle of nowhere...

---

