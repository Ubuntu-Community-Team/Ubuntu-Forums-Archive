---
title: "REQ : screem 0.14.1 (everything you need is provided)"
date: 2005-07-13
forum: Ubuntu Backports
---

### Post by Remix_88 on 2005-07-13
Hi,

Screem is a HTML/XML editor, similar to BlueFish but much better integrated with Gnome and less of a resource hog. The 0.12.1 version in the Hoary repositories is over 2 years old, please see the URL below for current 0.14.1 Debian package which works fine under Hoary but due to some minor library version differences in the package has to be 'force' installed and constantly shows up as a broken package in Synaptic.

[http://packages.debian.org/unstable/gnome/screem](http://packages.debian.org/unstable/gnome/screem)

I am sure all the core libraries in Hoary will support Screem 0.14.1 :-)

---

### Post by Remix_88 on 2005-07-13
I have successfully made a package for screem 0.14.2 using 'checkinstall', whilst this works nicely on my system and I can now easily remove should a future upgrade be required I would really like to know how to make 'claen' back ports so that I could contribute to the back port effort.

Any primers available?

---

### Post by Remix_88 on 2005-07-13
OK, making a bit more progress in that I found the nifty, and also quite groovy, 'ubp-build.py' script :-) 

[http://ubuntuforums.org/showthread.php?t=37599](http://ubuntuforums.org/showthread.php?t=37599)

I have managed to make, what appears to be, a fairly clean package for 0.14.1. However, it did drop me to a shell complaining that build dependancies failed. I 'exit'd, as I was pretty sure I have all the required stuff and everything proceed and completed correctly?!

If build dependancies fail, how do I manually satisfy them? Just some tips to help me get started. Should I build packages on a seperate machine which is just running Hoary with the official repositories or is it OK to use dependancies from backports?

---

### Post by nkemer on 2005-10-29
Hi
where is the package 0.14.1, i couldn't find.
and 0.14.2.3 did not work on my breezy 5.10
thank you

---

