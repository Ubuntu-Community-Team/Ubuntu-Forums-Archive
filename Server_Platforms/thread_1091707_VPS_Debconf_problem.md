---
title: "VPS Debconf problem"
date: 2009-03-09
forum: Server Platforms
---

### Post by masterpsk on 2009-03-09
Hi!

I have this VPS running Ubuntu 8.10 LAMP, and everytime i try to configure somethign with debconf it happens exactly the same as this post: [http://cmrg.fifthhorseman.net/ticket/70](http://cmrg.fifthhorseman.net/ticket/70)

> "dialog has terminal problems and has broken i/o in the terminal. the terminal colors go all funny, and it is not possible to navigate the dialog inputs, and therefore difficult to"

I tried the "fix" selecting: dpkg-reconfigure -f readline debconf and everytime i try to use "readline" option i got this message:

> Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <FIN> line 2.
Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <FIN> line 2.
Use of uninitialized value $val in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value $val in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value $val in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value $val in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.

Same with all packages.

Any idea? thank you.

---

