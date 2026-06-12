---
title: "pySonic"
date: 2005-10-08
forum: The Cafe
---

### Post by mikeisme77 on 2005-10-08
Does anybody know how to set up pySonic on Ubuntu (or Linux in general for that matter)? I've followed all the instructions (as limited as they are) but to no avail--it keeps saying I need a Makefile located in the config directory of Python2.4 (I've copied the Makefile from configuring Python source and got a different error where it's missing a completely non-existent pySonic.c file). I'd really like to be able to set this up with as easy instructions as possible as I'm trying to make an audio game for a local school for the blind (while most are Windows users--and it works fine under Windows--some are Linux users and I'd really like to meet their needs as well).

Thanks!

---

### Post by Quest-Master on 2005-10-08
I thought there was a package for it in the apt repositories :o?

---

### Post by mikeisme77 on 2005-10-10
[QUOTE=Quest-Master]I thought there was a package for it in the apt repositories :o?[/QUOTE]

I looked, but couldn't find one in the Hoary 64-bit repo. However, I know from past experience that some packages in the 32-bit repo aren't always in the 64-bit repo, so I may have to check that out. Or maybe it goes by another name? I didn't find anything when I searched for 'pysonic' or 'sonic' (nothing relevant for 'sonic' any way). I also manually scrolled through all of they 'python' entries and didn't find anything that appeared to be pySonic. Do you have additional repos added to your repo list that it could be in?

Thank you!

---

### Post by joebwan on 2005-10-11
I think if you execute a 

"sudo apt-get install python-dev"

you should be able to get this to work.  I had the same problem with another package complaining about Makefile not being in the config directory.

---

### Post by mikeisme77 on 2005-10-14
[QUOTE=joebwan]I think if you execute a 

"sudo apt-get install python-dev"

you should be able to get this to work.  I had the same problem with another package complaining about Makefile not being in the config directory.[/QUOTE]

That did the trick, thank you VERY much.

---

### Post by lostwong on 2005-10-31
I had a similar problem with Python while trying to install Trac... this thread solved my problem perfectly.  Thanks for the solution!

---

