---
title: "Picasa, WINE and unlinking folders..."
date: 2011-01-27
forum: Security
---

### Post by dpatel on 2011-01-27
OK, I've seen Bodhi's sticky suggesting to remove any links between wine and my $HOME and / folders. I want to do this (just to be safe).

However, I have a couple of questions about this:

1. I use Google Picasa - if I remove links between WINE and my folders, will that mean Picasa will no longer be able to see/find my photos?

2. Does Picasa use its own WINE (bottle??)?

3. While I'm asking, how do I disasscoiated .exe and WINE?

---

### Post by handy on 2011-01-27
> **dpatel said:**
> OK, I've seen Bodhi's sticky suggesting to remove any links between wine and my $HOME and / folders. I want to do this (just to be safe).

However, I have a couple of questions about this:

1. I use Google Picasa - if I remove links between WINE and my folders, will that mean Picasa will no longer be able to see/find my photos?

2. Does Picasa use its own WINE (bottle??)?

3. While I'm asking, how do I disasscoiated .exe and WINE?

I recently installed Picassa "on Arch" to have a look at it. I found that Picassa installs its own version of Wine in */opt/google/picassa/3.0/wine* .

So have a look on your Ubuntu install to see if that is the case, which I'm pretty sure it will be. I also have my original installation of Wine ( ~/.wine ), which I use for a few other things. They don't interfere with each other at all. 

Google did a good job as I see it. If you remove links from your "original" *~/.wine* to folders, it shouldn't have any effect on the Wine that is installed with Picassa in /opt... 

Beyond that I can't offer you anymore for your above questions.

You may find this page & their forum of use if you are worried about giving it a go:

[http://picasa.google.com/support/bin/topic.py?topic=14609&hl=en](http://picasa.google.com/support/bin/topic.py?topic=14609&hl=en)

---

